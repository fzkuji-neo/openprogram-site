<!-- GENERATED FILE — do not edit. Rebuilt by scripts/docs_site/generate_reference.py from apps/cli/python/openprogram_cli/_impl/parser.py. -->


# 程序

管理 Agent 程序（运行、列表）

```text
usage: openprogram programs [-h] verb ...
```

## `programs run`

运行程序

| 参数 | 说明 |
|---|---|
| `name` | 要运行的程序名 |
| `--arg`, `-a` `ARG` | 程序参数，格式 key=value，可重复指定 |
| `--provider`, `-p` `PROVIDER` | 模型服务：claude-code、openai-codex、gemini-cli、anthropic、openai、gemini。未指定时自动检测。 |
| `--model`, `-m` `MODEL` | 覆盖模型名称（如 sonnet、gpt-4o、claude-sonnet-4-6）。 |

## `programs list`

列出全部已保存程序

## `programs available`

列出可安装程序及已安装的第三方框架

## `programs install`

安装内置程序（gui/research/wiki/all），或通过 Git URL / owner/repo 安装第三方框架

| 参数 | 说明 |
|---|---|
| `name` | gui \| research \| wiki \| all，或第三方框架的 Git URL / owner/repo |
| `--upgrade`, `-U` | 即使已安装也重新安装或升级 |

## `programs uninstall`

按克隆目录名卸载程序（gui/research/wiki/all）或第三方框架

| 参数 | 说明 |
|---|---|
| `name` | 要卸载的程序或框架目录名 |

## `programs apps`

安装和调用新标签页中的应用

### `programs apps list`

列出已安装应用

### `programs apps install`

从本地目录安装应用

| 参数 | 说明 |
|---|---|
| `directory` |  |
| `--replace` |  |
| `--trust` | 授权执行已审查的 Python 后端 |

### `programs apps uninstall`

注销应用并保留数据

| 参数 | 说明 |
|---|---|
| `id` |  |

### `programs apps run`

启动 Agent 可见的应用操作

| 参数 | 说明 |
|---|---|
| `id` |  |
| `operation` |  |
| `--input` `INPUT` | JSON 格式的操作输入 |
| `--project` `PROJECT` | 项目范围应用所属的项目 ID |
| `--request-key` `REQUEST_KEY` | 用于安全重试提交的稳定键 |

### `programs apps status`

查看应用运行状态

| 参数 | 说明 |
|---|---|
| `run_id` |  |

### `programs apps cancel`

取消应用运行

| 参数 | 说明 |
|---|---|
| `run_id` |  |
