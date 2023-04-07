# setup-state-tool

An action to install the ActiveState [State Tool](https://docs.activestate.com/platform/state/) CLI and add it to the `$GITHUB_PATH`.

This makes it easy to install projects from the ActiveState platform during a GitHub actions workflow.

## Inputs

| name  | type  | default  | description  | required  |
|---|---|---|---|---|
| version  | string  | latest  | Version of the State Tool CLI to install  | false  |
| channel  | string  | release  | Channel to download the State Tool CLI from  | false  |
| activestate-api-key  | string  |   | API key used to authenticate to the ActiveState platform  | false |
| opt-in  | string  | false | Opt-in to unstable state tool commands  | false  |

## Examples

Example using the default configuration to install state tool for use with public projects:

```yaml
name: "my workflow"
on:
  workflow_dispatch:

jobs:
  install-state-tool-cli:
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@v3
    - uses: gscho/setup-state-tool@v1
    - name: run help command
      run: state --help
```

Example using the latest beta state tool and an api-key:

```yaml
name: "my workflow"
on:
  workflow_dispatch:

jobs:
  install-state-tool-cli:
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@v3
    - uses: gscho/setup-state-tool@v1
      with:
        activestate-api-key: foobar
        channel: beta
    - name: run help command
      run: state --help
```
