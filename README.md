# check-agent-trailer

A Git `commit-msg` hook to validate `Co-authored-by:` trailers in commit messages.

## Format

```
Co-authored-by: <agent> + <model>[/<level>] <email>
Co-authored-by: <agent> <model>[/<level>] <email>
```

Optional thinking level: `/off`, `/minimal`, `/low`, `/medium`, `/high`, `/xhigh`.

### Known Agents

| Agent | Description |
|-------|------------|
| `omp` | Oh My Pi (the harness) |
| `codewhale` | CodeWhale |
| `Claude` | Anthropic's Claude |
| `opencode` | OpenCode |
| `Codex` | OpenAI Codex |
| `Windsurf` | Codeium's Windsurf |
| `Cursor` | Cursor |

### Model Vendor → Email Domain

| Model Vendor | Domain |
|-------------|--------|
| DeepSeek | `@deepseek.com` |
| Claude / Anthropic | `@anthropic.com` |
| OpenAI / GPT / Codex | `@openai.com` |
| opencode | `@openai.com` |
| Google / Gemini / Gemma | `@google.com` |
| xAI / Grok | `@x.ai` |
| Mistral | `@mistral.ai` |
| Meta / Llama | `@meta.com` |
| Qwen | `@alibaba.com` |
| Kimi | `@moonshot.cn` |
| GLM / Zhipu | `@zhipuai.cn` |
| Amazon / Nova / Titan | `@amazon.com` |
| Cohere / Command | `@cohere.com` |
| Groq | `@groq.com` |
| Cerebras | `@cerebras.ai` |
| MiniMax | `@minimax.ai` |

Model names must include a version/descriptor (e.g. `v4 Pro`, `Sonnet 4`). Bare vendor names like `DeepSeek` or `Claude` alone are rejected.

## Examples

```
Co-authored-by: omp + DeepSeek v4 Pro <deepseek-v4-pro@deepseek.com>
Co-authored-by: omp DeepSeek v4 Pro/high <deepseek-v4-pro@deepseek.com>
Co-authored-by: Claude + Claude Sonnet 4 <claude-sonnet-4@anthropic.com>
Co-authored-by: omp + GPT-5 <gpt-5@openai.com>
Co-authored-by: opencode GPT-5/xhigh <gpt-5@openai.com>
Co-authored-by: Codex + Gemini 2.5 Pro <gemini-2.5-pro@google.com>
Co-authored-by: Cursor Grok 4/medium <grok-4@x.ai>
```
## Install

### Via pre-commit (recommended)

```yaml
# .pre-commit-config.yaml
repos:
  - repo: https://github.com/rurban/check-agent-trailer
    rev: v0.2
    hooks:
      - id: check-agent-trailer
```

### Manual

```bash
cp commit-msg /path/to/repo/.git/hooks/commit-msg
chmod +x /path/to/repo/.git/hooks/commit-msg
```

## License

MIT
