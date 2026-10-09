<!-- GENERATED FILE — do not edit. Rebuilt by scripts/docs_site/generate_reference.py from openprogram/config_schema.py. -->


# 配置键

全部用户可编辑设置来自同一份 schema，供 `setup`、`openprogram config`、终端和网页设置界面使用。`apply` 表示生效时机：`live` 为立即生效，`next_start` 为下次 worker 或网页服务启动时生效。

## 执行

| 配置键 | 默认值 | 生效方式 | 说明 |
|---|---|---|---|
| `execution.prevent_idle_sleep` | `False` | `live` | 在 macOS 上于 Agent 执行期间阻止空闲系统休眠。默认关闭；下一次执行时读取设置，显示器休眠与主动休眠仍然可用。 |
| `execution.instant_steer` | `True` | `live` | 默认开启。Agent 回复过程中发送的补充指令会立即结束正在生成的回复（文本、思考，或仍在写参数的工具调用），并按你的指令继续。已开始运行的工具仍会先执行完。关闭后，指令会等当前回复结束再生效。 |
| `execution.code_change_policy` | `keep_original` | `live` | 持久化函数默认保留原代码。use_latest 使用当前代码和已保存的步骤结果继续执行。进度不兼容时需要显式恢复。单次 Continue 命令可覆盖此选择。 |
| `execution.auto_resume_window_seconds` | `-1` | `live` | 中断后自动继续由重启流程管理的检查点。默认 -1 表示不限时间，0 禁用自动重启，正数指定截止时间（秒）。已有截止时间不会延长；用户暂停、取消及未确认的外部操作必须显式恢复。 |

## 端口

| 配置键 | 默认值 | 生效方式 | 说明 |
|---|---|---|---|
| `ui.web_port` | `18100` | `next_start` | 网页本身的服务端口，即浏览器访问地址。必须与后端端口不同。 |
| `ui.open_browser` | `True` | `next_start` | 执行 `openprogram web` 时同时打开指向界面的浏览器窗口。关闭后只启动服务器，可自行打开地址，例如用于无图形界面的服务器。 |
| `web.host` | `127.0.0.1` | `next_start` | 服务器监听的网络接口。默认仅接受本机连接。设置为 0.0.0.0 会将需认证的界面开放到其他接口，且必须至少配置一个精确的 web.allowed_origins 条目。在不可信网络中，优先通过同机反向代理提供 HTTPS。 |
| `web.allowed_origins` | `[]` | `next_start` | 允许访问此 OpenProgram 实例的精确浏览器 Origin。格式为 scheme://host[:port]，例如 https://agent.example.com。此列表校验请求 Origin 和 Host，不是供跨域前端使用的 CORS 列表。 |

## MCP 服务器

| 配置键 | 默认值 | 生效方式 | 说明 |
|---|---|---|---|
| `mcp_server.exposed_tools` | `[]` | `next_start` | 向已认证 MCP 客户端开放的运行时工具。默认空列表；修改在服务器下次启动时生效。 |

## 安全

| 配置键 | 默认值 | 生效方式 | 说明 |
|---|---|---|---|
| `security.outbound_url` | `{'exceptions': []}` | `live` | 仅所有者可设置的精确 Origin 或 CIDR 例外，供已声明的配置服务使用；也可指定明确承担目标策略执行职责的策略代理。 |

## 搜索

| 配置键 | 默认值 | 生效方式 | 说明 |
|---|---|---|---|
| `search.default_provider` | `auto` | `live` | `auto` 选择已配置服务中优先级最高的一项。 |

## 记忆

| 配置键 | 默认值 | 生效方式 | 说明 |
|---|---|---|---|
| `memory.backend` | `local` | `next_start` | `local` 使用磁盘上的记忆工具；`none` 禁用记忆。 |
| `memory.writer.model` | `` | `live` | 空值使用默认聊天 Agent 的模型服务和模型。设置 provider/model 仅覆盖后台记忆写入使用的模型。 |
| `memory.writer.enabled` | `True` | `live` | 在后台将已完成对话整理为主题记录。 |
| `memory.writer.trigger_tokens` | `16000` | `live` | 触发后台写入前累计的对话 token 数。 |
| `memory.retrieval.method` | `bm25` | `live` | 自动回忆和记忆搜索使用的检索方式。 |
| `memory.retrieval.top_k` | `5` | `live` | 每轮自动添加的匹配记录上限。 |
| `memory.retrieval.include_sources` | `True` | `live` | 在整理后的主题记录之外，同时检索归档证据。 |
| `memory.core.inject` | `True` | `live` | 将精简的核心记忆视图加入每次系统提示词。 |
| `memory.recent.limit` | `50` | `live` | Recent 派生视图保留的最新记录数量。 |

## 录制

| 配置键 | 默认值 | 生效方式 | 说明 |
|---|---|---|---|
| `record_replay.mode` | `off` | `next_start` | 下次进程启动时录制或严格回放全部模型服务调用。 |
| `record_replay.file` | `` | `next_start` | 受管理录制 ID 或显式回放文件路径；录制模式仅接受 ID。 |

## 目标

| 配置键 | 默认值 | 生效方式 | 说明 |
|---|---|---|---|
| `goal.max_turns` | — | `live` | 新目标的可选轮数预算。空值（默认）、0 或负数表示不限；只有显式正数才设置上限。达到上限会停止执行，但不会将目标标记为完成。已有目标保留已存预算；使用 /goal budget max_turns=0 可移除上限。 |
| `goal.judge_model` | `` | `live` | 目标完成判定使用的模型，格式为 `provider/model` 或模型名。空值（默认）使用会话所选模型。选择较便宜的模型可降低每轮判定成本。 |

## Agent

| 配置键 | 默认值 | 生效方式 | 说明 |
|---|---|---|---|
| `agent.output_style` | `default` | `live` | 在系统提示词末尾添加回复方式说明。`default` 不添加任何内容。将 `<name>.md` 放入 `~/.openprogram/output-styles/` 或 `./output-styles/` 可添加自定义样式。 |
| `agent.max_spawn_depth` | `1` | `live` | 一条协作链可创建的新 Agent 代数。默认 1 表示主 Agent 创建子 Agent，子 Agent 自行完成任务；2 允许子 Agent 再创建子 Agent；0 表示不限。只有创建 Agent 才计数，因此读取结果后仍可创建下一批。超过深度限制时拒绝创建，并提示当前 Agent 自行完成工作。 |
| `agent.max_messages` | `8` | `live` | 一条协作链允许的消息总数，包括创建 Agent、send_message 投递、agent(to=…) 调度和返回的回复。达到上限后停止相互重复发送。默认 8，0 表示不限。 |
| `agent.max_spawn_fanout` | `8` | `live` | 每个会话的单轮可创建的 Agent 数量。协作链预算限制深度和消息总数，此项限制单轮创建数量。默认 8，相当于任务池容量的两倍，可运行一批并让一批排队；超过后拒绝创建，并提示使用已有 Agent。0 表示不限。增加此值时也应调整 OPENPROGRAM_JOB_WORKERS，否则额外 Agent 只会延长排队。 |

## Agent 资源

| 配置键 | 默认值 | 生效方式 | 说明 |
|---|---|---|---|
| `agent.resource_limits.max_live_per_session` | — | `live` | 空值表示继承或不限；非空值必须为正数。 |
| `agent.resource_limits.max_queued_per_session` | — | `live` | 空值表示继承或不限；非空值必须为正数。 |
| `agent.resource_limits.max_jobs_per_session` | — | `live` | 空值表示继承或不限；非空值必须为正数。 |
| `agent.resource_limits.max_total_tokens` | — | `live` | 空值表示继承或不限；非空值必须为正数。 |
| `agent.resource_limits.max_cost_usd` | — | `live` | 空值表示继承或不限；非空值必须为正数。 |
| `agent.resource_limits.max_runtime_seconds` | — | `live` | 空值表示继承或不限；非空值必须为正数。 |
| `agent.resource_limits.idle_timeout_seconds` | — | `live` | 空值表示继承或不限；非空值必须为正数。 |

## 钩子

| 配置键 | 默认值 | 生效方式 | 说明 |
|---|---|---|---|
| `hooks` | `{}` | `next_start` | 订阅总线事件的 shell 命令，格式为 {"&lt;event&gt;": [{"command": "...", "timeout": 60}]}。事件以 JSON 传入命令标准输入。审批事件（tool.before、turn.stop）采用 Claude Code hooks 退出码协议：0 允许，2 拒绝并以 stderr 为原因，其他退出码被忽略（允许继续）。通知事件（turn.start、turn.end、session.start、goal.update）在后台运行并忽略退出码。每个命令默认超时 60 秒。worker 启动时读取一次，修改后需重启。 |

## 沙箱

| 配置键 | 默认值 | 生效方式 | 说明 |
|---|---|---|---|
| `sandbox.mode` | `auto` | `live` | `auto` 在后端可用时启用沙箱，否则允许无沙箱运行本地命令。`danger-full-access` 使用当前用户的完整权限运行模型发起的本地命令。`workspace-write` 使用平台原生沙箱（macOS sandbox-exec、Linux bubblewrap，或 Windows 默认 WSL2 发行版中的 bubblewrap），将写入限制在工作目录及配置目录内，禁止读取拒绝列表中的路径并禁用网络。每条命令都会读取设置，因此修改从下一条命令生效，也适用于后台线程和子进程。 |
| `sandbox.writable_roots` | `[]` | `live` | 沙箱命令在工作目录外可写入的目录，以 JSON 列表指定。支持展开 `~`。 |
| `sandbox.deny_read` | `['~/.ssh/**', '~/.aws/**', '~/.gnupg/**', '~/.openprogram/auth/**', '~/.claude.json', '~/.claude/.credentials.json', '~/.config/gh/**', '~/.netrc', '~/Library/Keychains/**', '**/.env']` | `live` | 禁止沙箱命令读取的 glob 路径，以 JSON 列表指定。默认包含凭据路径，因为读取到的密钥即使无网络也可能通过记忆写入结果进入后续会话上下文。`**` 匹配任意深度；Linux 的 bubblewrap 按路径屏蔽，不支持中间含通配符的模式，此类模式会被跳过。Linux 上应使用精确路径或具体目录前缀，例如 `/absolute/path/to/secrets/**`，不要依赖 `**/.env`。 |
| `sandbox.allow_read` | `[]` | `live` | 在较宽泛的 sandbox.deny_read 规则内重新允许读取的具体路径。更具体的路径优先；同等具体的拒绝规则仍生效。不能开放 ~/.openprogram/auth 或 agentics 目录。 |
| `sandbox.deny_write` | `[]` | `live` | 即使位于工作目录内也禁止沙箱命令写入的 glob 路径，以 JSON 列表指定，主要用于阻止设置后续在沙箱外执行的代码。函数监听器自动导入的目录始终被禁止，不在此列表中，因为放入其中的 `.py` 会在数秒内于 Agent 进程执行。其他路径默认不限制；添加 `**/.git/hooks/**` 可阻止相应执行风险，但也会使需要写入该目录的 `git init` 和 `git clone` 失败。 |
| `sandbox.network` | `False` | `live` | 关闭时沙箱命令完全无法联网，可防止读取到的信息经网络离开机器。打开后允许沙箱内下载依赖，也同时允许其他所有出站连接。 |
| `sandbox.network_domains` | — | `live` | 可选的 macOS 域名映射，例如 {"example.com": "allow", "*.example.org": "deny"}。需要开启网络。null 保留普通网络模式，空映射拒绝全部目标。deny 优先。仅支持公网 HTTP 端口 80 和 HTTPS CONNECT 端口 443。命令无法绕过受管理代理；不支持的平台明确拒绝执行。 |
| `sandbox.pass_env` | `[]` | `live` | 沙箱命令只继承 PATH、HOME、SHELL、USER、LOGNAME、TERM、TMPDIR、TZ、PWD、LANG 和 LC_*，因此环境中的 API 密钥不会传入。需要传入的其他变量在此指定。 |
| `sandbox.unavailable_policy` | `refuse` | `live` | 沙箱模式已启用但平台后端缺失或无法建立所需隔离时的行为。`refuse` 拒绝命令并说明原因；`warn` 无沙箱执行并记录警告，此时安全设置不会提供预期隔离。 |

## Git

| 配置键 | 默认值 | 生效方式 | 说明 |
|---|---|---|---|
| `git.co_author` | `True` | `live` | 在 OpenProgram 创建的提交中添加 `Co-Authored-By: <model> <noreply@openprogram.dev>`，使 `git log` 显示 AI 贡献。已知模型名称时使用其显示名，否则使用 `OpenProgram`。关闭后不再添加贡献署名。 |
| `git.allow_remote_write` | `False` | `live` | 允许 `commit-push-pr` 流程运行 `git push` 和 `gh pr create`。默认关闭：分支、暂存和提交只在本地发生且可撤销；推送和拉取请求对其他人可见，重置本地目录不能撤销。保持关闭时流程在提交后停止，可用 `git push --dry-run` 查看将推送的内容。 |

## 更新

| 配置键 | 默认值 | 生效方式 | 说明 |
|---|---|---|---|
| `update.channel` | `stable` | `live` | `openprogram upgrade` 使用的发布渠道。受管理安装使用最新稳定 GitHub Release，源码检出使用 origin/main。 |
