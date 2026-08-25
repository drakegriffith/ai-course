# Lesson 3: The Codex Cockpit

**Doctrine:** same gauges, different dashboard; the concepts transfer, the buttons don't.
**Prerequisites:** Lessons 1-2, a ChatGPT account with a paid plan.
**Artifact:** a logged-in Codex session where you can read the gauges and map every Claude concept to its Codex twin.
**Companion:** Video B.

## Install and log in

```
npm install -g @openai/codex
codex
```

Homebrew works too on Mac (`brew install codex`). First run offers "Sign in
with ChatGPT"; that ties usage to your ChatGPT plan. `codex login` redoes it
later.

## The gauges

`/status` inside a Codex session is the one-stop dial: account, model, and,
critically, token usage and how much of the context window remains. Codex
puts both dials on one screen where Claude splits them across `/status` and
`/context`. Same two concepts from Lesson 2: usage is the money dial, context
is the attention dial.

## Compact

`/compact` exists here too and does the same job: squeeze the session,
keep working. Starting a fresh session is just quitting and running `codex`
again; `codex resume` picks an old session back up.

## The translation table

This is the heart of the lesson. Learn concepts once, map them per tool:

| Concept | Claude Code | Codex |
|---------|-------------|-------|
| Memory file the tool always reads | CLAUDE.md (`~/.claude/CLAUDE.md` + per project) | AGENTS.md (`~/.codex/AGENTS.md` + per project; `/init` creates one) |
| Reusable named routine | Skill: `~/.claude/skills/<name>/SKILL.md`, called as `/<name>` | Custom prompt: `~/.codex/prompts/<name>.md`, called as `/<name>` |
| Gauges | `/status`, `/context` | `/status` |
| Squeeze a long session | `/compact` | `/compact` |
| Guardrails on what it may do | `/permissions` | `/approvals` |
| Extensions / connections | `/plugin` marketplace; MCP servers | MCP servers via `codex mcp` / config.toml; no marketplace |
| Pick the model | `/model` | `/model` |

The ecosystems differ most on extensions: Claude has a plugin marketplace;
Codex configures connections directly. Course 1 covers what those
connections (MCP) actually are in episode 17; here you only need to know the
knob exists and where it lives.

## Exercises

1. Log in, run `/status`, and find the context-remaining number.
2. Create `~/.codex/prompts/hello.md` containing one instruction, start a
   new session, and call `/hello`.
3. Run `/init` in a project folder and read the AGENTS.md it makes.
4. From memory, fill in a blank translation table, both columns.

## You can move on when

You can sit down at either tool cold, log in, read the gauges, compact a
session, and call a named routine, without caring which of the two it is.
That indifference is the fluency Course 1 assumes.

*Verify all commands against the installed version before filming.*
