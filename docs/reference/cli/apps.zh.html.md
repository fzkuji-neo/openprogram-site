<!-- GENERATED FILE — do not edit. Rebuilt by scripts/docs_site/generate_reference.py from apps/cli/python/openprogram_cli/_impl/parser.py. -->


# 应用

安装和调用新标签页中的应用

```text
usage: openprogram apps [-h] {list,install,uninstall,run,status,cancel} ...
```

## `apps list`

列出已安装应用

## `apps install`

从本地目录安装应用

| 参数 | 说明 |
|---|---|
| `directory` |  |
| `--replace` |  |
| `--trust` | 授权执行已审查的 Python 后端 |

## `apps uninstall`

注销应用并保留数据

| 参数 | 说明 |
|---|---|
| `id` |  |

## `apps run`

启动 Agent 可见的应用操作

| 参数 | 说明 |
|---|---|
| `id` |  |
| `operation` |  |
| `--input` `INPUT` | JSON 格式的操作输入 |
| `--project` `PROJECT` | 项目范围应用所属的项目 ID |
| `--request-key` `REQUEST_KEY` | 用于安全重试提交的稳定键 |

## `apps status`

查看应用运行状态

| 参数 | 说明 |
|---|---|
| `run_id` |  |

## `apps cancel`

取消应用运行

| 参数 | 说明 |
|---|---|
| `run_id` |  |
