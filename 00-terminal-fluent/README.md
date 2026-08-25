# Course 0: Terminal Fluent (prerequisite mini-course)

Written prerequisite for "How to Use AI Like a Software Engineer." Four markdown
lessons, no streaming schedule. Lessons 02 and 03 each back one companion video
(Claude ecosystem, Codex ecosystem). Expected reach is small; the job is to make
Course 1 episode 1 land for a viewer who has never opened a terminal.

**Doctrine for the whole mini-course:** the terminal is not a programmer thing,
it is the front door your AI tools actually use.

## Order

| Lesson | File | Companion video |
|--------|------|-----------------|
| 1 | 01-the-terminal-itself.md | none (written only) |
| 2 | 02-claude-code-cockpit.md | Video A: the Claude cockpit |
| 3 | 03-codex-cockpit.md | Video B: the Codex cockpit |
| 4 | 04-github-basics.md | none (written only) |

## The pass test

You are terminal fluent for this course when, without looking anything up, you can:

1. Open a terminal and say what folder you are standing in.
2. Move to any folder by path and list what is inside it.
3. Start Claude Code or Codex, log in, and read your usage and context numbers.
4. Compact a long session instead of abandoning it.
5. Call one skill (Claude) or one custom prompt (Codex) by name.
6. Name where your tool's memory file lives (CLAUDE.md or AGENTS.md).
7. Define repo, commit, clone, push, and pull in plain English, and clone the
   course repo onto your machine.

Course 1 assumes all seven. Nothing else is assumed.

## Filming and publishing

SHOOT-SCRIPT.md is the follow-along runbook: pre-flight checks, beat-by-beat
command lists for Videos A and B, and the publish steps.

COURSE-0-DECK.md is the slide source. Build the deck with `./build_deck.sh`,
which skips image slots you have not filled yet and prints which ones those are.
Slides stay sparse and everything you say lives in the speaker notes; photos are
openly licensed and credited on the last slide.

Pictures: `images/IMAGE-MAP.md` lists every slide, the filename it expects, and
the seven slots still empty. Drop a file into `images/` under the listed name and
rebuild; PowerPoint itself never needs editing.

Diagrams (the `d-*.png` files) are drawn by code in `diagrams.ipynb`, one cell
per diagram. To open it:

    cd ~/AICourse
    .venv/bin/jupyter lab 00-terminal-fluent/diagrams.ipynb

Choose the `AICourse (Pillow)` kernel, run the setup cell once, then press play
on whichever diagram you want to change. `make_diagrams.py` is the same code as a
single script, for rebuilding all seven without opening Jupyter.

## Maintenance note

CLI command surfaces change between versions. Before filming either companion
video, re-verify every slash command in lessons 02 and 03 against the installed
version that will appear on stream.
