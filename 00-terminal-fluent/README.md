# Course 0: Terminal Fluent (prerequisite mini-course)

Written prerequisite for "How to Use AI Like a Software Engineer." Two markdown
lessons, no streaming schedule. Each lesson backs one companion video. Expected
reach is small; the job is to make Course 1 episode 1 land for a viewer who has
never opened a terminal.

**Doctrine for the whole mini-course:** the terminal is not a programmer thing,
it is the front door your AI tools use.

## Order

| Lesson | File | Ends with | Video |
|--------|------|-----------|-------|
| 1 | lessons/01-the-terminal-itself.md | a folder you made, `ai-course`, holding your `notes.md` | about 20 min |
| 2 | lessons/02-github-and-the-cockpits.md | the course cloned, both cockpits driven, one issue filed | about 110 min |

Lesson 2 opens where Lesson 1 stopped: that practice folder gets replaced by the
real course repo.

## What the videos cover

Lesson 1 walks the eight commands (pwd, ls, cd, cd .., cd ~, mkdir, cat, open .),
paths, the home folder, Tab completion, and Ctrl+C, then makes the `ai-course`
folder and `notes.md` live on screen. Lesson 2 is one long sitting: git versus
GitHub, clone versus Download ZIP, branches and pull requests, npm and Homebrew,
then both AI cockpits driven side by side (login, usage, context, compact,
permissions, models, skills, memory files), model tiers and effort levels, and a
close on push, pull, a live backslash-bug fix, and opening an issue.

## Follow along

`follow-along/` is your desk. Clone this repo, walk into that folder, and work
there while you watch:

    git clone https://github.com/drakegriffith/ai-course.git ~/ai-course
    cd ~/ai-course/00-terminal-fluent/follow-along

Read `follow-along/README.md` first. Everything you make in that folder stays on
your machine; there is no push for you to run.

## The pass test

You are terminal fluent for this course when, without looking anything up, you can:

1. Open a terminal and say what folder you are standing in.
2. Move to any folder by path and list what is inside it.
3. Start Claude Code or Codex, log in, and read your usage and context numbers.
4. Compact a long session instead of abandoning it.
5. Call the `hello-course` skill in both tools: `/hello-course` in Claude, `$hello-course` in Codex.
6. Name where your tool's memory file lives (CLAUDE.md or AGENTS.md).
7. Define repo, commit, clone, push, and pull in plain English, and clone the
   course repo onto your machine.

Course 1 assumes all seven. Nothing else is assumed.

## What lives where

- `lessons/` is the written course, the source of truth.
- `follow-along/` is the viewer's scratch space, shipped with starter files.
- `script/`, `deck/`, `documents/`, and `images/` are production files. They stay
  on the instructor's machine and are not published here.

## Maintenance note

CLI command surfaces change between versions. Before filming, re-verify every
slash command in Lesson 2 against the installed version that will appear on
stream.
