<!-- GENERATED FILE — do not edit. Rebuilt by scripts/docs_site/generate_reference.py from apps/cli/python/openprogram_cli/_impl/parser.py. -->


# 工作流

检查并列出 Workflow 包

```text
usage: openprogram workflows [-h] verb ...
```

## `workflows check`

校验 Workflow、运行其测试并提交，使其可以调用

| 参数 | 说明 |
|---|---|
| `directory` | Workflow 包目录（包含 __init__.py） |
| `-m`, `--message` `MESSAGE` | 提交信息 |
| `--json` | 输出 JSON 报告 |

## `workflows list`

列出用户 Workflow 及其加载状态

| 参数 | 说明 |
|---|---|
| `--json` | 输出 JSON |
