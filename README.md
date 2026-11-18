<img src="assets/logo.png" alt="" width="64" height="64">

# Spring Prompt for your agent

[Spring Prompt](https://springprompt.com) tests the prompts in your app the way you would if you had the time: on realistic inputs, across several models, with every answer checked. Your coding agent finds the prompts in your repo and sends them; Spring Prompt tells you which model passes most often and what it costs, and can improve the prompt from its failures.

This repository holds Spring Prompt's listing and plugin files. Spring Prompt itself is a hosted service at `https://springprompt.com/mcp`, so there is nothing here to install or run.

## Connect

The address is the same everywhere:

```
https://springprompt.com/mcp
```

It is a remote MCP server (Streamable HTTP) with OAuth sign-in. The first time, your agent opens a Spring Prompt page in the browser to sign in. A new email address starts a free trial with test credit; no card needed.

**Claude:** find Spring Prompt in Claude's connector directory and choose Connect, or add a custom connector with the address above.

**ChatGPT:** find Spring Prompt in ChatGPT's apps and choose Connect.

**Cursor:** install Spring Prompt from the Cursor Marketplace, or add this to `.cursor/mcp.json`:

```json
{
  "mcpServers": {
    "springprompt": { "url": "https://springprompt.com/mcp" }
  }
}
```

**VS Code:**

```sh
code --add-mcp '{"name":"springprompt","type":"http","url":"https://springprompt.com/mcp"}'
```

**Claude Code** (in your repo):

```sh
claude mcp add --transport http springprompt https://springprompt.com/mcp
```

Then type `/mcp`, choose springprompt, and sign in.

**Codex:**

```sh
codex mcp add springprompt --url https://springprompt.com/mcp
```

The browser opens to sign in; if it doesn't, run `codex mcp login springprompt`.

**CI and servers:** make a personal key on the [keys page](https://springprompt.com/app/connect) and send it as `Authorization: Bearer <key>`. Keep it out of your repo. A key acts for your whole account, so tests it starts spend your credit.

## What to ask for

- "Use Spring Prompt to test the prompts in this repo across three cheap models, with a $1 limit."
- "Which models can Spring Prompt test with, and what do they cost?"
- "Improve the prompt from my last Spring Prompt test and test the new version on the same cases."
- "Check this prompt change against the saved test before I merge it."

Loading prompts, reading results and listing tests or models are free. A test spends credit, never more than the limit set on it.

## The tools

| Tool | What it does | Spends credit or changes things |
|---|---|---|
| `get_started` | Where the account stands: credit, loaded prompts, tests so far | No |
| `load_prompts` | Loads prompts, with cases and checks, for you to review | Saves prompts |
| `run_loaded_prompt` | Tests a loaded prompt | Spends credit |
| `test_prompt` | Tests a prompt across models | Spends credit |
| `get_test` | A test's results | No |
| `improve_prompt` | Improves a tested prompt and tests the new version | Spends credit |
| `list_tests` | Recent tests | No |
| `list_models` | The models and their prices | No |
| `get_recommendation` | A test's recommended model | No |
| `set_minimum_pass_rate` | Sets the pass rate a test's model must reach | Changes a setting |
| `list_recommendations` | Recommended models across tests | No |
| `rating_link` | A link for people to rate answers on their phone | Makes a link |
| `train_judge` | Trains a judge on people's ratings | Spends credit |
| `list_judges` | Trained judges | No |
| `score_answers` | Scores answers with a judge | Spends credit |
| `check_change` | Checks a prompt or model change against a saved test before it is merged | Spends credit |
| `get_check` | A check's verdict | No |
| `list_projects` | Live projects | No |
| `create_project` | Creates a Live project | Adds a project |
| `setup_status` | Whether a Live project is set up | No |
| `list_prompts` | The prompts a Live project has seen | No |
| `get_prompt` | One live prompt | No |
| `list_changes` | Recommended changes for a project | No |
| `mark_change` | Marks a change applied or dismissed | Changes a setting |
| `set_rules` | Sets a project's rules | Changes a setting |
| `draft_conversation` | Drafts a test for a multi-turn conversation | Spends credit |

## In this repository

- `server.json`: the entry in the [official MCP Registry](https://registry.modelcontextprotocol.io) (`com.springprompt/prompt-test`)
- `.cursor-plugin/plugin.json` and `mcp.json`: the Cursor plugin
- `assets/logo.png`: the icon

## Links

- For agents: https://springprompt.com/agents
- Privacy: https://springprompt.com/privacy
- Terms: https://springprompt.com/terms
- Help: hello@springprompt.com

The files in this repository are under the MIT licence. Spring Prompt is made by Incremento Ltd.
