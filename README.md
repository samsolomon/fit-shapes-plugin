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

## Install just the skill

Plan meals around your remaining calories and protein, even without a Fit Shapes account.
Install the skill in your current project with the skills CLI:

```sh
npx skills add samsolomon/fit-shapes-plugin --skill fit-shapes
```

Choose your agent when prompted. To install specifically for Claude Code:

```sh
npx skills add samsolomon/fit-shapes-plugin --skill fit-shapes -a claude-code
```

The skills CLI requires Node.js 22.20 or later. Start a new agent session after installing
so it can load the skill.

Try this without connecting an account:

> I have 650 calories and 45 grams of protein left today. Suggest two dinners using chicken,
> rice, and vegetables. Show portions and estimated nutrition for each.

If you do not supply targets, the skill asks for your calorie and protein targets or what you
have left today. Meal suggestions are estimates; they are not saved to a food log.

### Connect your own food log

Installing the skill this way adds instructions only. It does not install or authenticate the
Fit Shapes MCP connection. To read your targets and history or save food and weigh-ins, follow
the connection instructions for your assistant at https://fitshapes.com/docs/ and sign in with
your own Fit Shapes account. Connected tools require a Fit Shapes membership; you choose
read-only access or permission to log.

If you already installed the full Claude Code plugin above, it includes this skill and the
MCP connection configuration. You do not need to install the standalone skill as well.

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
