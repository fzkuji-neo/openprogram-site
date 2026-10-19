<!-- GENERATED FILE — do not edit. Rebuilt by scripts/docs_site/generate_reference.py from apps/cli/python/openprogram_cli/_impl/parser.py. -->


# workflows

Check and list workflow packages

```text
usage: openprogram workflows [-h] verb ...
```

## `workflows check`

Validate a workflow, run its tests and commit it so it can be called

| Option | Description |
|---|---|
| `directory` | Workflow package directory (contains __init__.py) |
| `-m`, `--message` `MESSAGE` | Commit message |
| `--json` | Emit a JSON report |

## `workflows list`

List user workflows and their load state

| Option | Description |
|---|---|
| `--json` | Emit JSON |
