<!-- GENERATED FILE — do not edit. Rebuilt by scripts/docs_site/generate_reference.py from apps/cli/python/openprogram_cli/_impl/parser.py. -->


# 工作流

编写和验证可复用的 Workflow 包

```text
usage: openprogram workflows [-h] verb ...
```

## `workflows validate`

静态验证 Workflow 包，不执行代码

| 参数 | 说明 |
|---|---|
| `directory` | 包含 pyproject.toml 的 Workflow 项目目录 |
| `--json` | 输出稳定格式的 JSON 报告 |

## `workflows test`

在强制启用的操作系统沙箱内运行 Workflow 行为测试

| 参数 | 说明 |
|---|---|
| `directory` | 包含 pyproject.toml 的 Workflow 包目录 |
| `--json` | 输出 JSON 结果 |

## `workflows publish`

测试并发布不可变的 Workflow 包修订版本

| 参数 | 说明 |
|---|---|
| `directory` | 包含 pyproject.toml 的 Workflow 包目录 |
| `--json` | 输出 JSON 结果 |
| `--replace` | 测试通过后替换已有且无未提交改动的 Workflow 包 |
