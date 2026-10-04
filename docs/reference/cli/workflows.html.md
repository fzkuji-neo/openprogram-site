<!-- GENERATED FILE — do not edit. Rebuilt by scripts/docs_site/generate_reference.py from apps/cli/python/openprogram_cli/_impl/parser.py. -->


# workflows

Author and validate reusable Workflow packages

```text
usage: openprogram workflows [-h] verb ...
```

## `workflows validate`

Statically validate a Workflow package without executing it

| Option | Description |
|---|---|
| `directory` | Workflow project directory containing pyproject.toml |
| `--json` | Emit a stable JSON report |

## `workflows test`

Run Workflow behavior tests in a required OS sandbox

| Option | Description |
|---|---|
| `directory` | Workflow package directory containing pyproject.toml |
| `--json` | Emit a JSON result |

## `workflows publish`

Test and publish an immutable Workflow package revision

| Option | Description |
|---|---|
| `directory` | Workflow package directory containing pyproject.toml |
| `--json` | Emit a JSON result |
| `--replace` | Replace an existing clean Workflow package after tests pass |
