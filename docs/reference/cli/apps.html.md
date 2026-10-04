<!-- GENERATED FILE — do not edit. Rebuilt by scripts/docs_site/generate_reference.py from apps/cli/python/openprogram_cli/_impl/parser.py. -->


# apps

Install and invoke applications shown on the new tab page

```text
usage: openprogram apps [-h] {list,install,uninstall,run,status,cancel} ...
```

## `apps list`

List installed applications

## `apps install`

Install an application from a local directory

| Option | Description |
|---|---|
| `directory` |  |
| `--replace` |  |
| `--trust` | Authorize execution of the reviewed Python backend |

## `apps uninstall`

Unregister an application, retaining its data

| Option | Description |
|---|---|
| `id` |  |

## `apps run`

Start an Agent-visible application operation

| Option | Description |
|---|---|
| `id` |  |
| `operation` |  |
| `--input` `INPUT` | Operation input as JSON |
| `--project` `PROJECT` | Project ID for a project-scoped application |
| `--request-key` `REQUEST_KEY` | Stable key for safe submission retries |

## `apps status`

Status an application run

| Option | Description |
|---|---|
| `run_id` |  |

## `apps cancel`

Cancel an application run

| Option | Description |
|---|---|
| `run_id` |  |
