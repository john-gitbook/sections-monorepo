---
icon: code
---

# Reference

References for the command line utility `gitbook`. The CLI can be used to create, test and publish integrations for the GitBook Integrations platform.

Install the CLI using `npm install @gitbook/cli -g`.

### `gitbook auth`

Authenticate the CLI with a GitBook Developer API token. You can generate a personal developer token in your [GitBook Developer settings](https://app.gitbook.com/account/developer).

The token can also be provided using the command line argument `--token=<token>`; if none is provider, it'll be prompted.

### `gitbook new <dir>`

Create and initialize a new integration locally. The program will prompt for information about the integration.

### `gitbook dev <spaceId>`

Create a live connection with a space within your GitBook organization. Updates made locally while the connection is running will automatically be received in the chosen space.&#x20;

See the [development section](../getting-started/development.md) to learn more.

### `gitbook publish`

Publish the integration defined in the `gitbook-manifest.yaml` file. See the [GitBook Manifest reference](../integrations/configurations.md) documentation to learn more.

See the [publishing section](../getting-started/publishing.md) to learn more about publishing your integration to GitBook.

### `gitbook unpublish <integration-name>`

Unpublish your integration from the GitBook integration platform. Pass the name of the integration as an argument to the command.

### `gitbook whoami`

Print information about the currently authenticated user.

### `gitbook help`

View the GitBook CLI commands and information on using them.
