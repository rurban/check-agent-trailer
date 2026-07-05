# check-agent-trailer

A Git `commit-msg` hook to validate `Co-authored-by:` trailers in commit messages.

## Format

```
Co-authored-by: <agent> + <model> <email>
```

### Known Agents

| Agent | Description |
|-------|------------|
| `omp` | Oh My Pi (the harness) |
| `codewhale` | CodeWhale |
| `Claude` | Anthropic's Claude |
| `opencode` | OpenCode |

### Model Vendor → Email Domain

| Model Vendor | Domain |
|-------------|--------|
| DeepSeek | `@deepseek.com` |
| Claude / Anthropic | `@anthropic.com` |
| OpenAI / GPT | `@openai.com` |
| opencode | `@openai.com` |

Model names must include a version/descriptor (e.g. `v4 Pro`, `Sonnet 4`). Bare vendor names like `DeepSeek` or `Claude` alone are rejected.

## Examples

```
Co-authored-by: omp + DeepSeek v4 Pro <deepseek-v4-pro@deepseek.com>
Co-authored-by: Claude + Claude Sonnet 4 <claude-sonnet-4@anthropic.com>
Co-authored-by: omp + GPT-5 <gpt-5@openai.com>
Co-authored-by: opencode + GPT-5 <gpt-5@openai.com>
```

## Install

### Via pre-commit (recommended)

```yaml
# .pre-commit-config.yaml
repos:
  - repo: https://github.com/rurban/check-agent-trailer
    rev: v0.1
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
