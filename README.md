# How to Use AI Like a Software Engineer

The course repo. Clone it, work inside it, and pull when a new lesson goes up.

```
git clone https://github.com/drakegriffith/ai-course.git ~/ai-course
cd ~/ai-course/00-terminal-fluent/follow-along
```

That second line is your desk. Bookmark it. Every time you sit back down to
this course, that is the line you type first.

## Start here

**Course 0: Terminal Fluent** is the prerequisite. Two written lessons that take
you from never having opened a terminal to driving Claude Code and Codex from
one. Course 1 assumes all of it.

| Lesson | Read |
|--------|------|
| 1. The Terminal Itself | [00-terminal-fluent/lessons/01-the-terminal-itself.md](00-terminal-fluent/lessons/01-the-terminal-itself.md) |
| 2. GitHub and the Cockpits | [00-terminal-fluent/lessons/02-github-and-the-cockpits.md](00-terminal-fluent/lessons/02-github-and-the-cockpits.md) |

Course 0's own front page, with the pass test you are working toward, is
[00-terminal-fluent/README.md](00-terminal-fluent/README.md).

## What is in this repo

- `00-terminal-fluent/lessons/` is the written course. Read these.
- `00-terminal-fluent/follow-along/` is your desk. Work here. It arrives
  furnished: a scratch folder per part of the lesson, a starter memory file for
  each AI tool, and a runbook to fill in.
- `COURSES.md` is the planning record for every course.
- `index.html` is the course page.

## Clone it, do not download the ZIP

GitHub's green Code button offers Download ZIP. It works once. A ZIP is a
photocopy: it has no memory and no way to catch up, so when a lesson lands you
download everything again and your own notes are stranded in the old folder.
Cloning costs the same click and stays alive. When a lesson goes up:

```
cd ~/ai-course
git pull
```

Your own files stay put. `git pull` only adds and updates the files I track, so
name your notes after yourself rather than after the lesson and the two sets
cannot collide.

## You cannot push here, and that is normal

Public means anyone can read. It does not grant write access, so you can pull
from this repo and you cannot push to it. That is how nearly every project you
join works: you get the folder, not the keys.

To say something back, open an issue. The Issues tab on this repo, or from the
terminal:

```
gh issue create --repo drakegriffith/ai-course --title "Finished Course 0 - your name"
```

I read each one.

## Who this is for

You have never opened a terminal, or you have opened one and closed it fast.
No programming background assumed. The doctrine for the whole thing: the
terminal is not a programmer thing, it is the front door your AI tools already
use.

Drake Griffith
