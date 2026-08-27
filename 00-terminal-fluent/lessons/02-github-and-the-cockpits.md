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

If `claude` is not found, install it once with:

```
npm install -g @anthropic-ai/claude-code
```

### Taking that line apart

Three unfamiliar words, worth taking apart once so they stop being scary.

**Node**, or Node.js, is a program that runs JavaScript outside a web browser.
JavaScript used to live only on web pages; Node let it run on your machine like
any other program, and a lot of command line tools got built on top of it,
including this one. Installing Node is installing the engine a certain class of
tool needs in order to start. If `npm` is missing, install Node.js from
nodejs.org and npm arrives with it.

**npm** ships with Node and is Node's app store, where the package you want is
sitting. `npm install` means fetch that package and set it up.

**`-g`** stands for global, and it is the piece worth remembering.

### Global install, local session

You are standing in `02-claude`, so the fair question is whether this installs
Claude Code into that folder. It does not, and `-g` is why. The program lands
on your whole computer once, and afterward `claude` runs from any folder on the
machine. You install it one time, not one time per project.

So why walk into a folder first? Because installing and starting are two
different acts. Installing puts the program on your computer. Starting it
decides which folder it looks at: the files there, and the `CLAUDE.md` sitting
there. Same program, different desk.

A plumber owns one set of tools and drives them to whichever house called.
`npm install -g` buys the tools. Walking into a folder and running `claude`
picks today's house. Nobody buys a new wrench per house.

Global is what you want here and in most cases later. A tool installed into one
folder works only in that folder, and a year from now you will not remember
which folders have it.

Logging in happens once, in the browser.

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
If `codex` is not found, install it with `npm install -g @openai/codex`. You can
read that line now: npm, install, global. Different vendor, different package,
same whole-computer install.

On a Mac `brew install codex` does the same job. Homebrew is a package installer
for Mac software in general, where npm covers Node packages. Either one puts
`codex` on your whole machine, so pick one rather than running both.

Notice the order again: walk into `03-codex` first, then start the tool. The
program is global, the session is local. Codex is reading this folder and the
`AGENTS.md` in it, not the folder next door.

| Command | Plain English |
|---------|---------------|
| `/status` | The money dial: your plan, your model, and the limit bars with their refill times |
| `/statusline` | The attention dial, as a switch: turn on `context-remaining` and it sits in the footer of every screen |
| `/compact` | Same word, same job as Claude's |
| `/permissions` | Same word, same job as Claude's: what it may do without asking |
| `/model` | Pick which model answers you |

Codex does not show the attention dial until you ask. Run `/statusline`, type
`context`, press space on `context-remaining`, then Enter. It reads unknown on
an empty session and fills in after your first message. Claude gave you a
command for the same number; Codex gives you a switch you flip once.

Quit the session, run `codex resume`, and it comes back where you left it.
Claude has the same move as `/resume` inside a session; Codex makes it a verb
on the command line.

Codex skills are the same file in the same shape as Claude's, in a folder next
door. Create the demo one, then call it inside a `codex` session by typing `$`
and picking `hello-course` from the list:

```
mkdir -p ~/.codex/skills/hello-course
printf -- '---\nname: hello-course\ndescription: Greet the user and state what folder they are standing in.\n---\nGreet the user in one sentence and state the folder they are standing in.\n' > ~/.codex/skills/hello-course/SKILL.md
```

The one thing that moved is the key you press: slash in Claude, dollar sign in
Codex. The file did not change.

The memory file here is `AGENTS.md`, doing what `CLAUDE.md` did next door
under a different name. The starter copy is already there; read it with
`cat AGENTS.md` and add a line of your own.

## One table, two tools

| Concept | Claude Code | Codex |
|---------|-------------|-------|
| Memory file the tool always reads | `CLAUDE.md` | `AGENTS.md` |
| Reusable named routine | Skill in `~/.claude/skills/`, called as `/<name>` | Skill in `~/.codex/skills/`, called as `$<name>` |
| Gauges | `/usage` money, `/context` attention | `/status` money, `/statusline` switch for attention |
| Squeeze a long session | `/compact` | `/compact` |
| Guardrails on what it may do | `/permissions` | `/permissions` |
| Extensions / connections | `/plugin`, `/mcp` | `/plugins`, `/mcp` |
| Pick the model | `/model` | `/model` |

Seven rows, two columns. Five rows are the same word or one letter apart.
Learn the row, not the column; the rows hold still.

Checked against Claude Code 2.1.247 and codex-cli 0.150.1 on 2026-08-27. Tools
rename commands between releases; if a name here does not match your screen,
type `/` alone and read the menu.

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
5. Call the `hello-course` skill in both tools: `/hello-course` in Claude, `$hello-course` in Codex.
6. Name where your tool's memory file lives (CLAUDE.md or AGENTS.md).
7. Define repo, commit, clone, push, and pull in plain English, and clone the
   course repo onto your machine.

Course 1 assumes all seven and nothing else.

## You can move on when

You can tick all seven without reopening this file, and there is an issue on
the course repo with your name in the title.
