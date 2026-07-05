# check-agent-trailer

A Git `commit-msg` hook to validate `Co-authored-by:` trailers in commit messages.

## Format

```
Co-authored-by: <agent> + <model> <email>
```

| Field | Valid Values |
|-------|-------------|
| agent | `omp`, `codewhale`, `Claude`, `opencode` |
| model | Must include version, e.g. `DeepSeek v4 Pro`, `Claude Sonnet 4` |
| email | Domain must match model vendor (`@deepseek.com` or `@anthropic.com`) |

## Examples

```
Co-authored-by: omp + DeepSeek v4 Pro <deepseek-v4-pro@deepseek.com>
Co-authored-by: Claude + Claude Sonnet 4 <claude-sonnet-4@anthropic.com>
```

## Install

Per repo:
```bash
cp commit-msg /path/to/repo/.git/hooks/commit-msg
```

Per worktree (hooks are shared in main repo):
```bash
cp commit-msg /path/to/main/.git/hooks/commit-msg
```

Global (git >= 2.9):
```bash
git config --global core.hooksPath /path/to/check-agent-trailer
```

## License

MIT
