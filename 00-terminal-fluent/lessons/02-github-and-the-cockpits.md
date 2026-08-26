# Lesson 2: GitHub and the Cockpits

**Doctrine:** learn the concept once, then map it per tool; vendors rename things, the concepts hold still.
**Prerequisites:** Lesson 1. Node.js from nodejs.org if `npm` is missing. A free GitHub account for the last section.
**Artifact:** the course cloned onto your machine, both AI cockpits started inside it, and one issue on the course repo with your name in the title.

## Why this exists

Claude Code and Codex both work on folders, and folders travel between
machines through GitHub. So this lesson runs in that order: bring the course
folder down, sit in both cockpits inside it, then send one message back up. By
the end you will have stopped caring which tool you sat down at.

## Five words

Definition first, tool second. One breath each.

- A **repo** (short for repository) is a folder with a memory. It remembers
  every version of itself.
- A **commit** is a snapshot with a note attached, one entry in that memory.
- **Clone** is copy it down: the whole folder, memory included, onto your
  machine.
- **Push** is send yours up.
- **Pull** is get theirs.

A sixth word, "issue," is deliberately absent; it belongs to GitHub, not to
git, and arrives at the end of the lesson.

## Git is the tool, GitHub is the place

Git is a program on your computer that gives folders that memory. GitHub is a
website where repos live so other people can reach them. Email and Gmail: one
is the system, the other is a popular place to use it. You can use git with no
GitHub account at all.

## The Download ZIP trap

On any GitHub repo page there is a green Code button, and inside it a
"Download ZIP" option. Most people take that one, and it works, once. A ZIP is
a photocopy. A clone is a subscription. The photocopy has no memory and no way
to catch up: next week the author adds a lesson, and your ZIP does not know,
cannot ask, and cannot update. You download the whole thing again, and
whatever notes you wrote into your copy are stranded in the old folder.

One line up in that same menu sits the clone link. It costs you the same click
and it stays alive. When the repo changes, one `git pull` brings your copy up
to date while your own files stay put. If you have ever downloaded someone's
project as a ZIP and wondered why you kept falling behind it, this is why.

## Clone the course

Cleanup first. Lesson 1 had you make a practice folder named `~/ai-course`
holding one `notes.md`. The real course replaces it now, and `git clone`
refuses to clone into a folder that already has files in it, so delete the
practice folder:

```
rm -rf ~/ai-course
```

New command: `rm` removes files, and the `-rf` flags make it remove a whole
folder and everything inside, without asking. Nothing goes to the Trash. Read
an `rm -rf` line twice before pressing Enter.

Now go home and clone:

```
cd ~
git clone https://github.com/drakegriffith/ai-course.git
cd ai-course
ls
cat README.md
```

The `cd ~` matters. Clone drops the new folder wherever you are standing, and
beginners who skip that step end up with a repo inside a repo. The README you
printed is the same front page GitHub shows in the browser: two views of one
folder. Clone once, not every time.

## What the clone delivered

```
ls 00-terminal-fluent
```

Two folders matter. `lessons/` is the written course, the thing you read.
`follow-along/` is your desk, the thing you work in. Nothing was installed and
nothing ran; the desk arrived furnished with the clone: a scratch folder per
part of the lesson, a starter memory file in each cockpit folder, a runbook to
fill in, and a README with the house rules.

```
cd 00-terminal-fluent/follow-along
pwd
cat README.md
```

That folder is home for the rest of this lesson; the `cd` line above is what
you type when you sit back down. The README's short version: what you make
here stays on your machine, and pulling new lessons will not eat it.

## The Claude Code cockpit

Walk into the Claude folder and start the tool:

```
cd 02-claude
claude
```

If `claude` is not found, install it once with
`npm install -g @anthropic-ai/claude-code`. `npm` is Node's installer, and
`-g` makes the program available from any folder; if `npm` itself is missing,
install Node.js from nodejs.org first. Logging in happens once, in the
browser.

### The two dials

The most common beginner confusion in this course is mashing two dials into
one. **Usage is the money dial**: how much you may spend in a window of time.
It refills on a schedule whether you type or not. **Context is the attention
dial**: how much of the conversation the model is holding, its working desk. A
full desk makes answers worse before it makes them stop, and it clears when
you start a new conversation, not when a clock ticks.

| Command | Plain English |
|---------|---------------|
| `/status` | The dashboard: your plan, your model, your login |
| `/usage` | The money dial |
| `/context` | The attention dial |
| `/compact` | Summarize the conversation so far, then keep going |
| `/clear` | Throw the conversation away and start fresh |
| `/` | Show the whole menu |

### Compact, do not abandon

The beginner tell is closing a long session and starting over, which loses
everything it knew. `/compact` keeps the thread and drops the noise. `/clear`
discards the conversation entirely. Compact for a long day on the same job;
clear for when you changed jobs.

### Calling a skill

A skill is a saved way of working, a decision you do not have to make twice:
you write down once how you want something done, then call it by name. It is a
plain-English text file, no syntax, no programming. Create the course's demo
skill by pasting this block once:

```
mkdir -p ~/.claude/skills/hello-course
printf -- '---\nname: hello-course\ndescription: Demo skill for Course 0\n---\nGreet the user and state what folder they are standing in.\n' > ~/.claude/skills/hello-course/SKILL.md
```

Two new pieces there: `mkdir -p` makes a folder plus any missing folders above
it, and `printf` writes text into a file, like `echo` with control over line
breaks. Read back what you made:

```
cat ~/.claude/skills/hello-course/SKILL.md
```

Then, inside a `claude` session, call it by name: `/hello-course`. Course 1
has you build your own; today you only call one. `/plugin` opens a marketplace
of other people's skills and extensions, phone apps for how your AI works.
Browse it, install sparingly, and know what each one may touch.

### The memory file

A skill runs when you call it. `CLAUDE.md` applies each session without being
asked: Claude Code reads it at start and treats the contents as standing
instructions, a sticky note left on the desk. A starter copy sits in
`02-claude`; read it, then add one instruction of your own to the bottom of it:

```
cat CLAUDE.md
echo "Always answer in one short paragraph." >> CLAUDE.md
claude
```

Note the doubled `>>`. Lesson 1 used a single `>`, which empties the file and
writes your line into it. `>>` adds to the end and keeps what was already
there. Single arrow replaces, double arrow adds. Reach for the wrong one on a
file you care about and the old contents are gone with no warning.

Ask it anything and watch the answers come back short. That file is the seed
of what Course 1 calls the harness.

## The Codex cockpit

Same gauges, different dashboard. The point of this part is proving the
concepts transfer, so next year's tool does not scare you.

```
cd ../03-codex
codex
```

`cd ../03-codex` steps out of `02-claude` and into its neighbor in one move.
If `codex` is not found, install it with `npm install -g @openai/codex`, or
`brew install codex` on a Mac (Homebrew is the Mac's package installer).

| Command | Plain English |
|---------|---------------|
| `/status` | Both dials on one screen; Claude splits them across three commands |
| `/compact` | Same word, same job as Claude's |
| `/approvals` | What Codex may do without asking; the twin of Claude's `/permissions` |
| `/model` | Pick which model answers you |

One move Codex has that Claude lacks a one-word version of: quit the session,
run `codex resume`, and it comes back where you left it.

Codex's name for a skill is a custom prompt. Create the demo one, then call it
as `/hello` inside a `codex` session:

```
mkdir -p ~/.codex/prompts
printf 'Greet the user and state what folder they are standing in.\n' > ~/.codex/prompts/hello.md
```

The memory file here is `AGENTS.md`, doing what `CLAUDE.md` did next door
under a different name. The starter copy is already there; read it with
`cat AGENTS.md` and add a line of your own.

## One table, two tools

| Concept | Claude Code | Codex |
|---------|-------------|-------|
| Memory file the tool always reads | `CLAUDE.md` | `AGENTS.md` |
| Reusable named routine | Skill, called as `/<name>` | Custom prompt, called as `/<name>` |
| Gauges | `/status`, `/context`, `/usage` | `/status` |
| Squeeze a long session | `/compact` | `/compact` |
| Guardrails on what it may do | `/permissions` | `/approvals` |
| Extensions / connections | `/plugin` marketplace | MCP servers via config |
| Pick the model | `/model` | `/model` |

Seven rows, two columns. Learn the row, not the column; the rows hold still.

## Saying something back

Step back to your desk:

```
cd ~/ai-course/00-terminal-fluent/follow-along
```

### Push and pull, properly this time

Work gets saved in two places, and nearly every git confusion comes from
treating them as one. A commit saves on your machine: your own notebook,
private until you do something about it. Push copies your commits up to
GitHub, the shared shelf anyone can reach. Pull is the reverse: you bring back
whatever went up since you last looked. Push up, pull down; GitHub is up, your
machine is down. Hold that picture and you have both words for life.

### Why you cannot push here

You can pull from this repo and you cannot push to it. Public means anyone can
read; it does not grant write access. I am the only person who can push, and
that is how nearly all projects you will join work: you get the folder, not
the keys. That is normal and fine.

Your copy does not update itself; nothing changes on your machine until you
ask, and that is deliberate: nobody gets to edit your computer behind your
back. When a new lesson goes up, ask:

```
cd ~/ai-course
git pull
```

and the new files arrive. Pull only adds and updates files that I track. The
notes and experiments you made in `follow-along` stay untouched, as long as
none of your files shares its exact name with a file I later add. Name your
files after yourself, not after the lesson, and the two sets cannot collide.

### The issue: the sixth word

An issue is a public note pinned to a repo: a question, a bug report, a
request. It is how you say something to a project you cannot write to, which
early on is most of them. Issue is a GitHub word, not a git word; git has no
idea issues exist, which is what keeps the five words clean.

Your homework is one issue on this repo, and I read each one.

**In the browser.** On github.com, open the repo, click the Issues tab, then
New issue. Title: `Finished Course 0 - <your name>`. Body: one line saying
which lesson was hardest. Submit. No install, and it works on your phone.

**From the terminal.** `gh` is GitHub's own command line tool. Install it once
with `brew install gh` on a Mac or `sudo apt install gh` on WSL (`sudo` runs a
command with administrator rights; `apt` is Ubuntu's installer), then run
`gh auth login` once and choose the browser flow. After that:

```
gh auth status
gh issue create --repo drakegriffith/ai-course \
  --title "Finished Course 0 - <your name>" \
  --body "Hardest lesson for me was the context dial."
```

`gh auth status` proves you are logged in. `gh issue create` files the same
issue with no browser and prints the link back at you. The backslash at the
end of a line tells the terminal the command continues on the next one.

A third way: stand in `02-claude`, start `claude`, and ask for the issue in a
plain sentence. It reaches for the same `gh` command, and the permission
prompt it shows first is the guardrails from earlier doing their job.

## The pass test

You are terminal fluent for this course when, without looking anything up, you
can:

1. Open a terminal and say what folder you are standing in.
2. Move to any folder by path and list what is inside it.
3. Start Claude Code or Codex, log in, and read your usage and context numbers.
4. Compact a long session instead of abandoning it.
5. Call one skill (Claude) or one custom prompt (Codex) by name.
6. Name where your tool's memory file lives (CLAUDE.md or AGENTS.md).
7. Define repo, commit, clone, push, and pull in plain English, and clone the
   course repo onto your machine.

Course 1 assumes all seven and nothing else.

## You can move on when

You can tick all seven without reopening this file, and there is an issue on
the course repo with your name in the title.
