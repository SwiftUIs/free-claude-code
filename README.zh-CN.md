<div align="center">

# Free Claude Code

[English](README.md) · **简体中文**

> 独立开源项目，与 Anthropic 没有隶属或背书关系。Claude 和 Claude Code 是 Anthropic 的商标。

</div>

## 你将获得什么

- **50 个符合 ToS 的 providers，每月 1.3B+ free tokens。** 在一个可搜索的 Admin UI 中统一使用 free、paid、subscription 和 local models。FCC 遵循各 provider 的条款；如果某项 integration 不再被允许，项目会移除它。
- **10 个 coding agents，共用一个 model catalog。** 你可以使用 Claude Code、Codex、Pi、OpenCode、Cline、Hermes、DeepSeek Harness、Grok Build、Muse Code 或 Aider，并通过 FCC 使用配置好的 models。
- **provider outage 时继续 coding。** 当 retries 用尽后，FCC 会自动尝试下一个 configured model，不需要重新开始当前 turn；所有 client 都支持此行为。
- **最多减少 90% 的 terminal-output tokens。** 可选的 RTK 会过滤常见 command output；FCC 还会在不调用 provider 的情况下完成 quota probes、command-prefix detection、titles、suggestions 和 filepaths 等优化。
- **Terminal、desktop、IDE 或 phone。** 支持 native launchers、VS Code、Codex App、JetBrains、Discord 和 Telegram。
- **Voice notes in，code out。** 可使用 local Whisper 或 NVIDIA NIM 进行 transcription。
- **保留 agent capabilities。** 支持 stream responses、tools、native interleaved thinking、images，并可为 Fable、Opus、Sonnet 和 Haiku 分别路由到 compatible models。

Free-tier availability 和 limits 由各 provider 控制，可能随时变化。

## Quick Start

### 1. Install Or Update

macOS/Linux：

```bash
curl -fsSL "https://raw.githubusercontent.com/Alishahryar1/free-claude-code/main/scripts/install.sh" | sh
```

Windows PowerShell：

```powershell
& ([scriptblock]::Create((irm "https://raw.githubusercontent.com/Alishahryar1/free-claude-code/main/scripts/install.ps1")))
```

再次运行相同命令即可 update。安装过程中选择至少一个 coding agent，也可以选择 RTK。执行前可先查看 [install.sh](scripts/install.sh) 和 [install.ps1](scripts/install.ps1)。

### 2. Start FCC

Windows：从 desktop 或 Start menu 打开 **Free Claude Code**。

macOS：从 Applications folder 或 menu-bar icon 打开 **Free Claude Code**。

Linux：

```bash
fcc-server
```

FCC 启动后会打开 Admin UI。Windows 和 macOS 用户可以通过 tray 或 menu-bar icon 打开 Admin、restart 或 quit。使用 `fcc-server` 时请保持 terminal 打开。

### 3. Configure NVIDIA NIM

1. 在 [build.nvidia.com/settings/api-keys](https://build.nvidia.com/settings/api-keys) 创建 API key。
2. 打开 server log 中显示的 Admin UI URL。
3. 将 key 填入 `NVIDIA_NIM_API_KEY`。
4. 保持 `MODEL` 默认值 `nvidia_nim/nvidia/nemotron-3-super-120b-a12b`，或在 model dropdown 中搜索并选择其他 model。
5. 点击 **Validate**，然后点击 **Apply**。

如需使用 bearer token 保护 local proxy，请在 Admin 中启用 **Proxy Authentication**。

### 4. Run Your Coding Agent

```bash
fcc-claude    # Claude Code
fcc-codex     # Codex
fcc-pi        # Pi
fcc-opencode  # OpenCode
fcc-cline     # Cline
fcc-hermes    # Hermes
fcc-dsh       # DeepSeek Harness Web
fcc-grok      # Grok Build
fcc-muse      # Muse Code
fcc-aider     # Aider
```

`fcc-aider` 会以 `anthropic/<provider>/<model>` 的形式暴露 FCC models。需要使用 Aider native providers 时，请直接运行普通的 `aider`。

## Choose A Provider

1. 打开下面的 provider link，获取 key、models 或 setup instructions。
2. 在 Admin UI 配置对应 setting。OpenAI 例外：请使用 **Providers → Connected accounts**。
3. 搜索 `MODEL` dropdown 并选择 model。如果 provider 无法列出 models，请手动输入 `<provider-id>/<exact-provider-model-id>`。
4. 点击 **Validate**，然后点击 **Apply**。

可选：在 **Model Config** 下添加有顺序的 **Fallback Models**。它会应用到每一个 connected client。一次 failed request 可能会在成功前触达并消耗多个 provider 的 usage。

| Provider | Admin UI setting | Example `MODEL` |
| --- | --- | --- |
| NVIDIA NIM | `NVIDIA_NIM_API_KEY` | `nvidia_nim/nvidia/nemotron-3-super-120b-a12b` |
| OpenRouter | `OPENROUTER_API_KEY` | `open_router/openrouter/free` |
| Groq | `GROQ_API_KEY` | `groq/llama-3.3-70b-versatile` |
| ClinePass | `CLINE_API_KEY` | `cline_pass/cline-pass/kimi-k3` |
| OpenAI / ChatGPT | Connect ChatGPT in the Admin UI | `openai/<model-id>` |
| xAI (Grok) | `XAI_API_KEY` | `xai/grok-4.5` |
| QwenCloud Token Plan | `QWENCLOUD_API_KEY` | `qwencloud/qwen3.7-plus` |
| QwenCloud Coding Plan | `QWENCLOUD_CODING_API_KEY` | `qwencloud_coding/qwen3.7-plus` |
| Together AI | `TOGETHER_API_KEY` | `together/zai-org/GLM-5.2` |
| DeepInfra | `DEEPINFRA_API_KEY` | `deepinfra/deepseek-ai/DeepSeek-V4-Flash` |
| SiliconFlow | `SILICONFLOW_API_KEY` | `siliconflow/Qwen/Qwen3-32B` |
| Nebius Token Factory | `NEBIUS_API_KEY` | `nebius/Qwen/Qwen3-30B-A3B` |
| Chutes | `CHUTES_API_KEY` | `chutes/Qwen/Qwen3-32B-TEE` |
| Featherless AI | `FEATHERLESS_API_KEY` | `featherless/Qwen/Qwen3-32B` |
| Agnes AI | `AGNES_API_KEY` | `agnes/agnes-2.0-flash` |
| ZenMux | `ZENMUX_API_KEY` | `zenmux/deepseek/deepseek-v4-flash-free` |
| W&B Inference | `WANDB_API_KEY` | `wandb/openai/gpt-oss-20b` |
| Azure OpenAI | `AZURE_OPENAI_API_KEY` and `AZURE_OPENAI_BASE_URL` | `azure_openai/<deployment-name>` |
| Google AI Studio (Gemini) | `GEMINI_API_KEY` | `gemini/models/gemini-3.1-flash-lite` |
| Google Vertex AI | `VERTEX_PROJECT_ID` + ADC | `vertex/google/gemini-3.5-flash` |
| DeepSeek | `DEEPSEEK_API_KEY` | `deepseek/deepseek-chat` |
| Mistral La Plateforme | `MISTRAL_API_KEY` | `mistral/devstral-small-latest` |
| Mistral Codestral | `CODESTRAL_API_KEY` | `mistral_codestral/codestral-latest` |
| OpenCode Zen | `OPENCODE_API_KEY` | `opencode_zen/gpt-5.3-codex` |
| OpenCode Go | `OPENCODE_API_KEY` | `opencode_go/minimax-m2.7` |
| Vercel AI Gateway | `AI_GATEWAY_API_KEY` | `vercel/openai/gpt-5.5` |
| Amazon Bedrock | `AWS_BEARER_TOKEN_BEDROCK` | `bedrock/openai.gpt-oss-120b` |
| Hugging Face Inference Providers | `HUGGINGFACE_API_KEY` | `huggingface/Qwen/Qwen3-Coder-480B-A35B-Instruct:fastest` |
| Cohere | `COHERE_API_KEY` | `cohere/command-a-plus-05-2026` |
| GitHub Models | `GITHUB_MODELS_TOKEN` | `github_models/openai/gpt-4.1` |
| Wafer | `WAFER_API_KEY` | `wafer/DeepSeek-V4-Pro` |
| Kimi API | `KIMI_API_KEY` | `kimi/kimi-k2.5` |
| Kimi Code | `KIMI_CODE_API_KEY` | `kimi_code/k3` |
| MiniMax | `MINIMAX_API_KEY` | `minimax/MiniMax-M3` |
| Cerebras Inference | `CEREBRAS_API_KEY` | `cerebras/gpt-oss-120b` |
| SambaNova | `SAMBANOVA_API_KEY` | `sambanova/Meta-Llama-3.3-70B-Instruct` |
| Kilo.ai | `KILO_API_KEY` | `kilo/kilo-auto/free` |
| Fireworks AI | `FIREWORKS_API_KEY` | `fireworks/accounts/fireworks/models/llama-v3p3-70b-instruct` |
| Novita AI | `NOVITA_API_KEY` | `novita/deepseek/deepseek-v4-flash-0731` |
| Cloudflare Workers AI | `CLOUDFLARE_API_TOKEN` and `CLOUDFLARE_ACCOUNT_ID` | `cloudflare/@cf/moonshotai/kimi-k2.6` |
| Z.ai Coding Plan | `ZAI_API_KEY` | `zai/glm-5.2` |
| Z.ai API (pay as you go) | `ZAI_API_KEY` | `zai_api/glm-4.7-flash` |
| TokenRouter | `TOKENROUTER_API_KEY` | `tokenrouter/moonshotai/kimi-k3-free` |
| NaraRoute | `NARAROUTE_API_KEY` | `nararoute/kimi-k3-free` |
| Poolside AI | `POOLSIDE_API_KEY` | `poolside/poolside/laguna-s-2.1` |
| LLM7.io | `LLM7_API_KEY` | `llm7/default` |
| Ollama Cloud | `OLLAMA_API_KEY` | `ollama_cloud/qwen3-coder:480b` |
| LM Studio | `LM_STUDIO_BASE_URL` | `lmstudio/<model-id>` |
| llama.cpp | `LLAMACPP_BASE_URL` | `llamacpp/<model-id>` |
| Ollama | `OLLAMA_BASE_URL` | `ollama/<model-tag>` |

### Provider-specific setup

OpenAI 使用 ChatGPT subscription，而不是 API key。请在 Admin UI 的 **Providers → Connected accounts** 中连接 ChatGPT；headless systems 可使用 device code。连接后请 restart 已运行的 agent。

Azure OpenAI 使用 resource 中的 deployment names。将 `AZURE_OPENAI_BASE_URL` 设置为完整 v1 endpoint，例如 `https://YOUR-RESOURCE-NAME.openai.azure.com/openai/v1/`，并选择支持 Chat Completions 的 deployment。若 deployment 没有出现在 model dropdown 中，请将 deployment name 作为 custom model slug 输入。

Mistral Codestral 使用与 Mistral La Plateforme 不同的 key。Kimi Code subscription keys 使用 `kimi_code/`，Kimi API credit keys 使用 `kimi/`。QwenCloud Coding Plan keys 使用 `qwencloud_coding/`，QwenCloud Token Plan keys 使用 `qwencloud/`；两者的 keys 和 endpoints 不可互换。

Vertex AI 使用 Google Application Default Credentials，而不是 API key。Cloudflare 需要同时配置 API token 和 account ID。Ollama Cloud 使用 model picker 中显示的 exact model IDs；local Ollama 使用独立的 `ollama/` prefix。对于 coding agents，优先选择支持 tools 且具有足够 context 的 models。

### Local provider setup

**LM Studio**：启动 LM Studio local server，加载 tool-capable model，使用 LM Studio 显示的 model identifier，并加上 `lmstudio/` prefix。默认 URL 为 `http://localhost:1234/v1`。

**llama.cpp**：使用 OpenAI-compatible Chat Completions API 启动 `llama-server`，并为 model 准备足够 context。使用带 `llamacpp/` prefix 的 local model ID。`LLAMACPP_BASE_URL` 默认是 `http://localhost:8080/v1`；FCC 同时接受 server root 和显式 `/v1` suffix。

**Ollama**：

```bash
ollama pull llama3.1
ollama serve
```

使用 `ollama list` 显示的 tag，并加上 `ollama/` prefix。`OLLAMA_BASE_URL` 默认是 `http://localhost:11434`；FCC 同时接受 root URL 和显式 `/v1` suffix。

### Optional model-tier routing

`MODEL` 是每个 request 的 fallback。设置 `MODEL_FABLE`、`MODEL_OPUS`、`MODEL_SONNET` 或 `MODEL_HAIKU`，即可覆盖对应的 Claude Code tier；选择 **None** 则使用 `MODEL`。

### Reasoning control

打开 **Admin UI → Model Config → Reasoning** 并选择所需行为。

| Selection | Behavior |
| --- | --- |
| **From client**（default） | 使用 Claude Code、Codex、Pi、OpenCode、Cline、Hermes、DeepSeek Harness、Grok Build、Muse Code 或 Aider 发送的 effort；未发送时保留 provider default。 |
| **Off** | 请求禁用 reasoning。 |
| **Low / Medium / High / X-High / Max** | 用选定 reasoning level 覆盖 client。 |
| **Inherit**（仅 Fable、Opus、Sonnet、Haiku） | 使用 root Reasoning selection。 |

不支持所选 control 的 providers 会保留自己的 behavior。

## Connect Your Client

Terminal 使用方式：先启动 `fcc-server`，再运行 `fcc-claude`、`fcc-codex`、`fcc-pi`、`fcc-opencode`、`fcc-cline`、`fcc-hermes`、`fcc-dsh`、`fcc-grok`、`fcc-muse` 或 `fcc-aider`。

### Claude Code in VS Code

安装 [Claude Code extension](https://marketplace.visualstudio.com/items?itemName=anthropic.claude-code)，打开 VS Code user settings as JSON，并添加：

```json
"claudeCode.disableLoginPrompt": true,
"claudeCode.environmentVariables": [
  { "name": "ANTHROPIC_BASE_URL", "value": "http://localhost:8082" },
  { "name": "ANTHROPIC_AUTH_TOKEN", "value": "freecc" },
  { "name": "CLAUDE_CODE_ENABLE_GATEWAY_MODEL_DISCOVERY", "value": "1" },
  { "name": "CLAUDE_CODE_AUTO_COMPACT_WINDOW", "value": "190000" },
  { "name": "DISABLE_AUTOUPDATER", "value": "1" },
  { "name": "DISABLE_FEEDBACK_COMMAND", "value": "1" },
  { "name": "DISABLE_ERROR_REPORTING", "value": "1" }
]
```

将 port 和 authentication token 与 Admin UI 保持一致，然后 reload extension。

### Codex App / Codex in VS Code

启动 FCC，然后编辑 Codex configuration：Windows 为 `%USERPROFILE%\.codex\config.toml`，macOS/Linux 为 `~/.codex/config.toml`。加入匹配的 model catalog path 和以下 shared FCC settings：

```toml
model_provider = "fcc"
model = "nvidia_nim/nvidia/nemotron-3-super-120b-a12b"

[model_providers.fcc]
name = "Free Claude Code"
base_url = "http://127.0.0.1:8082/v1"
wire_api = "responses"

[model_providers.fcc.auth]
command = "fcc-codex"
args = ["--print-proxy-auth-token"]
```

将 `model` 和 port 与 Admin UI 保持一致。auth command 会自动读取 FCC 当前的 proxy token。完成配置或修改 model 后，restart Codex App 或 VS Code；WSL-backed Codex 请编辑 WSL 内部的文件。

### Claude Code 仍然要求 login

如果配置 FCC URL 和 token 后 Claude Code 仍要求 login，请打开 state file：Windows 为 `%USERPROFILE%\.claude.json`，macOS/Linux/WSL 为 `~/.claude.json`。在现有 JSON 中合并以下 property，不要删除其他 fields：

```json
"hasCompletedOnboarding": true
```

如果文件不存在，请创建：

```json
{
  "hasCompletedOnboarding": true
}
```

保存后 restart Claude Code 或 IDE。

## Optional Integrations

从 **Admin UI → Messaging** 配置 integrations，然后点击 **Validate** 和 **Apply**。

### Discord bot

在 [Discord Developer Portal](https://discord.com/developers/applications) 创建 bot，启用 **Message Content Intent**，并授予 read、send、message-history 和 **Manage Messages** permissions。将 **Messaging Platform** 设置为 `discord`，填写 **Discord Bot Token**、**Allowed Discord Channels** 和绝对路径形式的 **Allowed Directory**，然后 Apply；如有提示则 restart server。

### Telegram bot

通过 [@BotFather](https://t.me/BotFather) 创建 bot，并从 [@userinfobot](https://t.me/userinfobot) 获取 numeric user ID。在 groups 中，授予 bot delete messages permission。将 **Messaging Platform** 设置为 `telegram`，填写 **Telegram Bot Token**、**Allowed Telegram User ID** 和绝对路径形式的 **Allowed Directory**，然后 Apply；如有提示则 restart server。

### Messaging commands

| Usage | Behavior |
| --- | --- |
| `/stats` | 显示 session state。 |
| standalone `/stop` | Cancel all work。 |
| reply with `/stop` | 只取消 selected request，其他 queued requests 继续。 |
| standalone `/clear` | Reset all FCC state，并删除 chat 中所有 tracked messages。 |
| reply with `/clear` | 删除 selected message 及其 literal platform reply subtree，同时保留 ancestors 和 siblings。 |

### Voice notes

使用对应 voice backend 的 command 重新运行 installer。安装完成后 restart `fcc-server`，在 **Admin UI → Messaging → Voice** 中启用 voice notes，选择 `cpu`、`cuda` 或 `nvidia_nim`，并选择 Whisper model。

NVIDIA NIM transcription：

```bash
curl -fsSL "https://raw.githubusercontent.com/Alishahryar1/free-claude-code/main/scripts/install.sh" | sh -s -- --voice-nim
```

Local Whisper：

```bash
curl -fsSL "https://raw.githubusercontent.com/Alishahryar1/free-claude-code/main/scripts/install.sh" | sh -s -- --voice-local
```

Local gated models 需要 `HUGGINGFACE_API_KEY`；NVIDIA NIM transcription 需要 `NVIDIA_NIM_API_KEY`。其他 voice options 请参阅 [English README](README.md) 的 Voice notes section。

## Manage Your Installation

运行 `fcc-server --version`，可在不启动 FCC 的情况下查看 installed version。

### Update

重新运行 [Install Or Update](#install-or-update) 中对应的 command。

### Uninstall

卸载前请停止所有正在运行的 FCC commands。

**Removes**：Free Claude Code（包括 desktop launcher 和 commands）以及 `~/.fcc/`。

**Keeps**：uv、Python、各 coding agents、RTK 和 shared PATH entries。

macOS/Linux：

```bash
curl -fsSL "https://raw.githubusercontent.com/Alishahryar1/free-claude-code/main/scripts/uninstall.sh" | sh
```

Windows PowerShell：

```powershell
& ([scriptblock]::Create((irm "https://raw.githubusercontent.com/Alishahryar1/free-claude-code/main/scripts/uninstall.ps1")))
```

## Project Links

- [Report bugs or request features](https://github.com/Alishahryar1/free-claude-code/issues)
- [Architecture and extension guide](ARCHITECTURE.md)
- [Contributing guide](CONTRIBUTING.md)

## License

MIT License。详情见 [LICENSE](LICENSE)。

> 本文档中的 product names、professional terms、commands、environment variables、API names、model IDs 和 config keys 保持原文，以避免与实际界面或命令不一致。
