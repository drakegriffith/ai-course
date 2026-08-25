# Lesson 2: The Claude Code Cockpit

**Doctrine:** know your gauges before you fly; usage and context are the fuel dials.
**Prerequisites:** Lesson 1 (terminal basics), a Claude account with a paid plan.
**Artifact:** a logged-in Claude Code session where you can read every gauge and call one skill by name.
**Companion:** Video A.

## Install and log in

```
npm install -g @anthropic-ai/claude-code
claude
```

If `npm` is missing, install Node.js first (nodejs.org, LTS version). The
first `claude` run walks you through login in the browser; `/login` does the
same thing later if you switch accounts. `/status` confirms who you are, what
plan you are on, and which model you are talking to.

## The gauges: usage and context visibility

Two different dials, easy to conflate:

- **Usage** is how much of your plan you have spent this period. Check with
  `/status` (and `/usage` where your build has it). This is the money dial.
- **Context** is how much of the model's working memory this one conversation
  has filled. Check with `/context`, which shows what is eating the window.
  This is the attention dial. A full context makes the model worse before it
  makes it stop.

Plain-English rule: usage resets on a clock, context resets when you start a
new conversation.

## Compact commands

When a session runs long, you have two moves:

- `/compact` squeezes the conversation into a summary and keeps going. Use it
  mid-task when the work must continue.
- `/clear` wipes the conversation and starts fresh. Use it between tasks.

Habit worth building: `/compact` is for "same job, long day"; `/clear` is for
"new job." Abandoning a window because it got long is the beginner tell.

## Skills commands

A skill is a saved way of working that you call by name. Skills live as
folders at `~/.claude/skills/<name>/SKILL.md`; each one is just a markdown
file with instructions. Invoke one by typing `/` followed by its name, e.g.
`/daily-brief`. Type `/` alone to see what is available in your session.
Course 1, episode 1 builds your first one; this lesson only requires you to
call an existing one and understand where it lives on disk.

## Plugins

Plugins bundle skills, commands, and connections other people built.
`/plugin` opens the marketplace view where you browse and install. Treat
plugins like phone apps: install few, know what each one can touch.

## The memory file

Claude Code reads `CLAUDE.md` files automatically: a global one at
`~/.claude/CLAUDE.md` and one per project folder. Whatever is written there
is standing instruction for every session. This file is the seed of what
Course 1 calls the harness.

## Exercises

1. Log in, run `/status`, and write down your plan and model.
2. Run `/context` on a fresh session, chat for a while, run it again, and
   explain the difference.
3. Run `/compact` on that session and watch what survives.
4. Find `~/.claude/skills` in your terminal (`ls ~/.claude/skills`) and open
   one SKILL.md with `cat`.

## You can move on when

You can read both gauges, choose correctly between `/compact` and `/clear`,
call a skill by name, and point at your CLAUDE.md on disk.

*Verify all slash commands against the installed version before filming.*
