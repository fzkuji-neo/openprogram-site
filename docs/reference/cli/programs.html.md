<!-- GENERATED FILE — do not edit. Rebuilt by scripts/docs_site/generate_reference.py from apps/cli/python/openprogram_cli/_impl/parser.py. -->


# programs

Manage agentic programs (run, list)

```text
usage: openprogram programs [-h] verb ...
```

## `programs run`

Run a program

| Option | Description |
|---|---|
| `name` | Program name to run |
| `--arg`, `-a` `ARG` | Program arg as key=value (repeatable) |
| `--provider`, `-p` `PROVIDER` | LLM provider: claude-code, openai-codex, gemini-cli, anthropic, openai, gemini. Auto-detected if not specified. |
| `--model`, `-m` `MODEL` | Model name override (e.g. sonnet, gpt-4o, claude-sonnet-4-6). |

## `programs list`

List all saved programs

## `programs available`

List installable programs + installed third-party harnesses

## `programs install`

Install a program (gui/research/wiki/all) or any third-party harness by git URL / owner/repo

| Option | Description |
|---|---|
| `name` | gui \| research \| wiki \| all — or a git URL / owner/repo for a third-party harness |
| `--upgrade`, `-U` | Reinstall/upgrade even if already present |

## `programs uninstall`

Uninstall a program (gui/research/wiki/all) or a third-party harness by its clone-dir name

| Option | Description |
|---|---|
| `name` | Program or harness dir name to uninstall |

## `programs apps`

Install and invoke applications shown on the new tab page

### `programs apps list`

List installed applications

### `programs apps install`

Install an application from a local directory

| Option | Description |
|---|---|
| `directory` |  |
| `--replace` |  |
| `--trust` | Authorize execution of the reviewed Python backend |

### `programs apps uninstall`

Unregister an application, retaining its data

| Option | Description |
|---|---|
| `id` |  |

### `programs apps run`

Start an Agent-visible application operation

| Option | Description |
|---|---|
| `id` |  |
| `operation` |  |
| `--input` `INPUT` | Operation input as JSON |
| `--project` `PROJECT` | Project ID for a project-scoped application |
| `--request-key` `REQUEST_KEY` | Stable key for safe submission retries |

### `programs apps status`

Status an application run

| Option | Description |
|---|---|
| `run_id` |  |

### `programs apps cancel`

Cancel an application run

| Option | Description |
|---|---|
| `run_id` |  |
