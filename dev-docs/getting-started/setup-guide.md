
# Out-of-band Interoperation

The preferred way of making changes in the network is to perform all changes through NSO  <br/> which keeps the NSO copy of device configurations up-to-date (in sync) at all times. This approach has many benefits, as it allows NSO to:

- Avoid making provisioning decisions based on stale data
-  
- Provide a single pane of glass to network configuration  
- Act as a network source of truth  
- Better aid in troubleshooting scenarios  
- Provide improved performance  
- Expose advanced compliance and reporting capabilities  

However, in some situations, such a setup is undesirable or not possible due to historic, organizational, or other reasons. While an organization may decide to forgo most of these benefits by managing the network through multiple systems, it is essential for NSO provisioning code to work with current data.

![Out-of-band changes](../../images/oob-change.png)

To better allow coexistence with other systems and processes that manage the same devices, NSO 6.5 introduces an innovative, patent-pending approach to so-called "out-of-band" changes. Out-of-band changes are changes to NSO-managed devices not done through NSO. From a high-level perspective, this approach consists of:

- "Ships passing in the night" handling of configuration not relevant to NSO-managed parts  
- Verification of data used in provisioning decisions prior to being pushed out to the network  
- Policy-based retention of changes by other systems and agents on NSO-managed configuration  

It now becomes possible to manage a network device by never doing a `sync-from`/`sync-to` operation (though the first `sync-from` may still be desirable). Special-purpose pre-provisioning checks also become unnecessary in most cases, as NSO verifies the correctness of data used in the transaction.

![Handling out-of-band changes](../../images/oob-handling.png)

Such an approach allows NSO to use targeted correctness checks, especially useful for devices with large configurations. If only small parts are relevant to NSO, the checks can be optimized, enabling the system to scale with the extent of the change rather than the entire configuration size.

## Introducing `confirm-network-state`

Handling out-of-band changes requires NSO to make additional checks during provisioning, so this is opt-in functionality. The first option is to use the `commit confirm-network-state` variant, which applies only to the current commit.

This is useful for testing and experimenting. You can also use `confirm-network-state` with `sync-from` and service `re-deploy`.

### Enabling by Default

For normal use, enable `confirm-network-state` through device settings:

```bash
admin@ncs(config)# devices device c1 confirm-network-state enabled-by-default true
```

```bash
admin@ncs(config)# devices profiles profile prod confirm-network-state enabled-by-default true
```

```bash
admin@ncs(config)# devices global-settings confirm-network-state enabled-by-default true
```

Once enabled, you don’t need to explicitly use the option in each commit.

When NSO uses `confirm-network-state`, it doesn’t check device sync status. Instead, it verifies that all data read during the transaction still matches the device state. This uses the same transaction read-set used for [concurrency checks](../../development/core-concepts/nso-concurrency-model.md).

### Python Script Example

```python
import ncs
with ncs.maapi.single_write_trans('admin', 'python') as t:
    root = ncs.maagic.get_root(t)
    intf = root.devices.device['c1'].config.interface.GigabitEthernet['0/1']
    if intf.mtu is None or intf.mtu < 1520:
        intf.mtu = 1520
    params = t.get_params()
    params.confirm_network_state()
    t.apply_params(True, params)
```

**Output example:**

```bash
$ python3 update-mtu.py || echo 'inconsistency detected!'
...
inconsistency detected!
$ ncs_cli -Cu admin
admin@ncs# devices device c1 compare-config
diff
 devices {
     device c1 {
         config {
             interface {
                 GigabitEthernet 0/1 {
+                    mtu 9000;
                 }
             }
         }
     }
 }
```

This failure is expected — the script should retry after inspecting out-of-band changes, using `sync-from` to accept or `sync-to` to reject them.

If the commit succeeds, NSO includes the out-of-band changes in the transaction. This ensures CDB consistency and allows you to preview them in a `commit dry-run`.

**Dry-run Example:**

```bash
admin@ncs(config)# no devices device c1 config interface GigabitEthernet 0/1 ip dhcp snooping trust
admin@ncs(config)# commit dry-run outformat cli-c
...
        confirm-network-state {
            device {
                name c1
                out-of-band devices device c1
                             config
                              interface GigabitEthernet0/1
                               mtu 9000
                              exit
                             !
                            !
                data devices device c1
                      config
                       interface GigabitEthernet0/1
                        no ip dhcp snooping trust
                       exit
                      !
                     !
            }
        }
```

## Service Out-of-band Policies

`confirm-network-state` is especially powerful when used with services. NSO tracks which service created which configuration using [backpointer references](../../development/advanced-development/developing-services/services-deep-dive#ch_svcref.refcount).

When NSO detects an out-of-band change to service-managed config, it uses a service policy to decide how to respond.

### Policy Example

```
services out-of-band policy iface-servicepoint
 rule allow-mtu
  path         ios:interface/GigabitEthernet/mtu
  at-create    sync-from-device
  at-delete    sync-from-device
  at-value-set sync-from-device
 !
 rule reject-ip-address
  path         ios:interface/GigabitEthernet/ip/address
  at-create    sync-to-device
  at-delete    sync-to-device
  at-value-set sync-to-device
 !
!
```

**Explanation:**

- **`allow-mtu` rule**  
  Allows MTU to be changed out-of-band. NSO syncs the value from the device into CDB. Good for values unrelated to service logic.

- **`reject-ip-address` rule**  
  Rejects IP changes. NSO syncs the CDB value back to the device. Useful for service-critical data.

The `at-create`, `at-delete`, and `at-value-set` operations allow fine-grained control over when to apply the rules. For example, a service might tolerate IP address changes as long as one exists, even if the exact value is different.
