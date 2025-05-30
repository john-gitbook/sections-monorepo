---
icon: circle-question
---

# Support

.. \_enterprise-overview:

## FiftyOne Enterprise Overview

.. default-role:: code

FiftyOne Enterprise is purpose-built to integrate into your existing ML workflows,\
including annotation, evaluation, model training, and deployment.

{% hint style="info" %}
[Learn more](https://voxel51.com/enterprise) about FiftyOne Enterprise and [contact us](https://voxel51.com/talk-to-sales) to try it! .. \_fiftyone-vs-fiftyone-enterprise: ### Open Source vs Enterprise
{% endhint %}

Here's a high-level overview of the capabilities that FiftyOne Enterprise brings:

```
</td>
<td style="text-align: center"><p>Apache 2.0</p></td>
</tr>
</tbody>
```

|                      | FiftyOne Enterprise                                                                                        | FiftyOne Open Source                                                                                       |
| -------------------- | ---------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------- |
| Curate Datasets      | [![check](https://voxel51.com/images/icons/checkmark.svg)](https://voxel51.com/images/icons/checkmark.svg) | [![check](https://voxel51.com/images/icons/checkmark.svg)](https://voxel51.com/images/icons/checkmark.svg) |
| Evaluate Models      | [![check](https://voxel51.com/images/icons/checkmark.svg)](https://voxel51.com/images/icons/checkmark.svg) | [![check](https://voxel51.com/images/icons/checkmark.svg)](https://voxel51.com/images/icons/checkmark.svg) |
| Find Mistakes        | [![check](https://voxel51.com/images/icons/checkmark.svg)](https://voxel51.com/images/icons/checkmark.svg) | [![check](https://voxel51.com/images/icons/checkmark.svg)](https://voxel51.com/images/icons/checkmark.svg) |
| Visualize Embeddings | [![check](https://voxel51.com/images/icons/checkmark.svg)](https://voxel51.com/images/icons/checkmark.svg) | [![check](https://voxel51.com/images/icons/checkmark.svg)](https://voxel51.com/images/icons/checkmark.svg) |
| Deployment           | <p>Multi-user, on-premise,<br>private/public cloud</p>                                                     | Local, Single user                                                                                         |
| Dataset Management   | [![check](https://voxel51.com/images/icons/checkmark.svg)](https://voxel51.com/images/icons/checkmark.svg) |                                                                                                            |
| User Permissions     | [![check](https://voxel51.com/images/icons/checkmark.svg)](https://voxel51.com/images/icons/checkmark.svg) |                                                                                                            |
| Dataset Permissions  | [![check](https://voxel51.com/images/icons/checkmark.svg)](https://voxel51.com/images/icons/checkmark.svg) |                                                                                                            |
| Dataset Versioning   | [![check](https://voxel51.com/images/icons/checkmark.svg)](https://voxel51.com/images/icons/checkmark.svg) |                                                                                                            |
| SSO                  | [![check](https://voxel51.com/images/icons/checkmark.svg)](https://voxel51.com/images/icons/checkmark.svg) |                                                                                                            |
| Enterprise Support   | [![check](https://voxel51.com/images/icons/checkmark.svg)](https://voxel51.com/images/icons/checkmark.svg) | Discord Community                                                                                          |
| Licensing            | <p>Unlimited data, flexible<br>user-based licensing</p>                                                    |                                                                                                            |

.. \_enterprise-backwards-compatibility:

#### Backwards compatibility

FiftyOne Enterprise is fully backwards compatible with FiftyOne Open Source. This\
means that all of your pre-existing FiftyOne Open Source workflows should be\
usable without modification.

For example, you can continue running all of the workflows listed below as you\
would with FiftyOne Open Source:

.. list-table::\
:widths: 25 75\
:header-rows: 1\
:stub-columns: 1

*
  * Application
  * Workflows
*
  * Data ingestion
  * [Loading data into FiftyOne](loading-datasets/)
*
  * Data curation
  * \| [Using the FiftyOne App](fiftyone-app/)\
    \| [Creating views into datasets](using-views/)\
    \| [Embedding-based dataset analysis](https://voxel51.com/docs/fiftyone/tutorials/image_embeddings.html)\
    \| [Visual similarity](brain-similarity/) and [dataset uniqueness](brain-image-uniqueness/)
*
  * Annotation
  * [Using the annotation API](fiftyone-annotation/)
*
  * Model training and evaluation
  * \| [Exporting data for model training](exporting-datasets/)\
    \| [Adding model predictions to FiftyOne](https://voxel51.com/docs/fiftyone/tutorials/evaluate_detections.html#Add-predictions-to-dataset)\
    \| [Evaluating models in FiftyOne](evaluating-models/)\
    \| [Using interactive plots to explore results](interactive-plots/)

.. \_enterprise-system-architecture:

#### System architecture

FiftyOne Enterprise is implemented as a set of interoperable services, as described\
in the figure below.

<figure><img src="../../images/enterprise/enterprise_architecture.png" alt="enterprise-architecture"><figcaption></figcaption></figure>

FiftyOne Enterprise is strictly a software offering. All relevant hardware is owned\
and managed by your organization, whether on-premises or in your virtual\
private cloud.

**Enterprise database services**

The primary storage location for all of the FiftyOne Enterprise datasets and related\
metadata (excluding media files) for your organization.

**Enterprise web service**

An always-on front-end from which you can visually access the datasets in your\
FiftyOne Enterprise deployment. Web-based access is the standard entrypoint for\
non-technical users who need point-and-click access to dataset curation and\
related features, as well as basic workflows for technical users. Most dataset\
curation and model analysis work by engineers happens via client installations.

**Enterprise API authentication**

Technical users connecting to FiftyOne Enterprise via Python or Jupyter notebooks\
use token-based authentication to make authorized connections to the\
centralized database storing your Team’s dataset metadata.

**Python/notebook users (your organization)**

Similar to FiftyOne Open Source, technical users can install the FiftyOne\
Enterprise client in their working environment(s). These clients are configured\
to use the centralized database service and will additionally serve their own\
App instances (like FiftyOne Open Source) so that engineers can work locally,\
remotely, and in Jupyter notebooks.

**Web users (your organization)**

FiftyOne Enterprise provides an always-on login portal at`https://<your-org>.fiftyone.ai` that users can login to from any browser for\
web-only workflows.

**Data lake (your organization)**

FiftyOne Enterprise does not require duplication or control over how your source\
media files are stored. Instead, FiftyOne Enterprise stores references (e.g., cloud\
object URLs or network storage paths) to the media in your datasets, thereby\
minimizing storage costs and providing you the flexibility to provision your\
object storage as you see fit. FiftyOne Enterprise has full support for cloud,\
network, and local media storage.

**User authentication (your organization)**

FiftyOne Enterprise can be configured to work with your organization’s\
authentication and authorization systems, enabling you to manage access to\
FiftyOne Enterprise using your existing OAuth stack. FiftyOne Enterprise supports SAML\
2.0 and OAuth 2.0.

.. \_security-considerations:

#### Security considerations

FiftyOne Enterprise relies on your organization's existing security infrastructure.\
No user accounts are created specifically for FiftyOne Enterprise; we integrate\
directly with your OAuth system.

Usage of the FiftyOne Enterprise client by technical users of your organization is\
also secure. All database access is managed by the central authentication\
service, and self-hosted App instances can be configured to only accept\
connections from known servers (e.g., only localhost connections). In remote\
client workflows, users are instructed how to configure ssh tunneling to\
securely access self-hosted App instances.

No outside network access is required to operate FiftyOne Enterprise. Voxel51 only\
requests the ability to (a) access the system logs for usage tracking and\
auditing purposes, and (b) access the system at the customer’s request to\
provide technical support. We are flexible in the mechanisms used to accomplish\
these goals.
