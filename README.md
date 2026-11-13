# Zavus humanizer skill

A skill that tells your AI agent when to run finished writing through [Zavus](https://zavus.ai), and the MCP server that does the rewriting. Zavus is a separate model built only to make writing sound human. Your agent writes the draft, Zavus rewrites it, and your agent checks the rewrite before you see it.

- **Skill:** [`skills/humanize-with-zavus/SKILL.md`](skills/humanize-with-zavus/SKILL.md). It covers when to humanize (client emails, proposals, posts, READMEs, release notes), when not to (code, commits, notes), and how to check the result.
- **MCP server:** `https://api.zavus.ai/mcp`, with the tools `humanize`, `usage` and `feedback`. You sign in in your browser the first time, so there's no API key to copy.

New accounts get 500 words free, with no card. Plans start at $20 a month for 50,000 words ([pricing](https://zavus.ai/pricing/)).

## Install

### Claude Code

```
/plugin marketplace add Zavus-ai/humanizer-skill
/plugin install zavus@zavus
```

This adds the MCP server and the skill. Then run `/mcp`, choose zavus and sign in. [Full Claude Code setup](https://zavus.ai/setup/claude-code/).

### Codex

```
codex mcp add zavus --url https://api.zavus.ai/mcp
mkdir -p ~/.codex/skills && cp -r skills/humanize-with-zavus ~/.codex/skills/
```

[Full Codex setup](https://zavus.ai/setup/codex/).

### Cursor

Add the server to `~/.cursor/mcp.json`:

```json
{ "mcpServers": { "zavus": { "url": "https://api.zavus.ai/mcp" } } }
```

Then copy `skills/humanize-with-zavus` into `~/.cursor/skills/` (or `.cursor/skills/` in a project). [Full Cursor setup](https://zavus.ai/setup/cursor/).

### GitHub Copilot (VS Code)

```
code --add-mcp '{"name":"zavus","type":"http","url":"https://api.zavus.ai/mcp"}'
```

Then copy `skills/humanize-with-zavus` into `.github/skills/` in your repo. [Full Copilot setup](https://zavus.ai/setup/github-copilot/).

### Anything else

Add the MCP server at `https://api.zavus.ai/mcp` in your client, and paste the body of `SKILL.md` into its instructions file (`AGENTS.md`, `GEMINI.md`, custom instructions). Setup for every client: [zavus.ai/setup](https://zavus.ai/setup/).

## Check it works

```
Write a 60-word note to a client confirming Thursday's call, then run it through Zavus.
```

## Questions

- How Zavus handles your text: [privacy](https://zavus.ai/privacy/)
- Help: [zavus.ai/support](https://zavus.ai/support/)

## License

MIT
