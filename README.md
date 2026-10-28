# Fit Shapes plugin

The Fit Shapes connector and skill for AI assistants and coding agents. Fit Shapes is a calorie
and macro tracker for iPhone and Android. Its MCP server at `https://mcp.fitshapes.com/mcp` lets
an assistant read your food log, targets, weight trend, and estimated expenditure, and log food
and weigh-ins when you ask. You sign in with your own Fit Shapes account and choose whether the
assistant may only read or may also log.

This repository holds only the plugin manifests and the skill. The server is not here.

## Claude Code

```
claude plugin marketplace add samsolomon/fit-shapes-plugin
claude plugin install fit-shapes@fit-shapes
```

Then run `/mcp` and sign in to Fit Shapes.

## Everything else

Steps for Claude, ChatGPT, Gemini, Grok, Perplexity, Mistral, Cursor, Codex, VS Code, OpenCode,
and Antigravity CLI are at https://fitshapes.com/docs/. The tools and their units are at
https://fitshapes.com/docs/tools/. What the assistant can see, and how to take access back, is at
https://fitshapes.com/docs/access/.

## License

MIT. See `LICENSE`.

## Layout

Two manifests describe the same plugin. `.claude-plugin/plugin.json` and `.mcp.json` are the Claude Code plugin (install from the marketplace in `.claude-plugin/marketplace.json`). `plugin.json` and `mcp.json` at the root follow the Agent Plugins specification, which Cursor and cursor.directory read. Both point at the one server, `https://mcp.fitshapes.com/mcp`, and the skill in `skills/fit-shapes/`.

## Gemini CLI and Antigravity CLI

`gemini-extension.json` at the root makes this repo a Gemini CLI extension, listed in the gallery under the `gemini-cli-extension` topic. Install it with

```
gemini extensions install https://github.com/samsolomon/fit-shapes-plugin
```

then run `/mcp auth fit-shapes` to sign in. Antigravity CLI reads the same server address; the steps are at https://fitshapes.com/docs/connect/gemini-cli/.
