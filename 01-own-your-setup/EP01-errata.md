# EP01 errata: what really happened to `.claude` on camera

Recorded 2026-08-27, take stopped in Part 4. Written the same night, all
claims re-derived with commands on this machine. Read this before the retake.

## The thing I said on camera, and why it was only half right

I ran `ls`, `.claude` did not appear, and I told the camera it did not appear
**because it is a hidden file.** That sentence is true about `ls`, and it is
not a diagnosis. Two completely different situations print the exact same
nothing:

1. **Hidden.** The folder is there. `ls` refuses to print any name starting
   with a dot. `ls -a` prints it.
2. **Absent.** The folder was never created. `ls -a` prints nothing either.

`ls` alone cannot tell those apart, so on camera I picked the friendlier one
and stated it as fact. The command that separates them is `ls -a`, or
`ls -d ~/.claude`, which prints the folder if it exists and prints
`No such file or directory` if it does not. Silence is not evidence of
presence; ask the question that can come back "no".

## When `~/.claude` actually gets created (verified, not remembered)

Both of these were run tonight against a throwaway empty home folder, so the
answer is measured rather than recalled:

```
# A. install/version only: home folder stays completely empty
HOME=/tmp/fakehome claude --version     ->  2.1.250, and /tmp/fakehome has nothing in it

# B. first real run of the program: the folder appears
HOME=/tmp/fh2 claude mcp list           ->  creates /tmp/fh2/.claude/ and /tmp/fh2/.claude.json
```

So:

- **`npm install -g` does not create `~/.claude`.** Installing puts the
  program on disk. Nothing about installing writes to your home folder.
- **`~/.claude` appears the first time you actually run `claude`.** Until
  then a viewer following Course 0 has no `~/.claude` at all, and their `ls -a`
  is honestly empty.
- **A brand new `~/.claude` has no `skills/` folder inside it.** The fresh one
  contained only `backups/`. That is exactly what the `-p` in
  `mkdir -p ~/.claude/skills/hello-course` is for: it creates `skills` and
  `hello-course` in one go, silently, whether or not `skills` was there. On
  camera I have been describing `-p` as "no complaint if it already exists",
  which is half of it. The other half is "creates every missing parent on the
  way down", and that half is the one doing the work here.

## What actually broke the Part 4 take

Filesystem evidence, found after the fact:

```
~/ai-course/.claude/skills/tidy-notes/    created 18:43:58, empty
no SKILL.md for tidy-notes anywhere under ~
```

An empty `tidy-notes` folder sits **inside the project**, at
`~/ai-course/.claude/`, not in my home folder. That is where a
`mkdir -p .claude/skills/tidy-notes` lands when it is typed without the `~/`
in front while standing in `~/ai-course`. The `~/` is not decoration: `~/`
means "start at my home folder", and a path with no leading `~/` or `/` means
"start from wherever I am standing right now". Same eleven characters after
that, two different folders on disk.

Then `nano ~/.claude/skills/tidy-notes/SKILL.md` opened an empty buffer
happily, because nano always opens a buffer for a file that does not exist
yet, and only failed at Control-O, where it cannot write into a folder that
was never made. That is the mismatch I hit live: the folder went one place,
the file went another. The exact keystroke is not recoverable, my shell
history never flushed that terminal, but the empty project-local folder and
the missing `SKILL.md` are only consistent with the two commands pointing at
different places.

**Fix for the retake:** after the `mkdir`, prove it landed before opening the
editor. One line, `ls -d ~/.claude/skills/tidy-notes`, which prints the path
or says `No such file or directory`. It is also the honest teaching moment:
check that a step worked before building on top of it.

**Stage cleanup:** `rmdir ~/ai-course/.claude/skills/tidy-notes` and
`rmdir -p` the empty parents, or the stray folder shows up in a later take.

## The `-g` confusion, cleared up

I also wondered out loud whether my `CLAUDE.md` was missing "because I told
viewers to do `-g` and I did `-g` too". Those are unrelated.

`-g` in `npm install -g @anthropic-ai/claude-code` decides **where the program
goes**: global, one copy on your PATH so `claude` runs from any folder, versus
without `-g`, a copy inside the current project's `node_modules` that only
works there. That is a fact about the program's location. It says nothing
about config, and neither install writes `~/.claude`, `~/.claude/skills`, or
any `CLAUDE.md`.

Memory files are separate again, and nothing creates them for you:

- `~/.claude/CLAUDE.md`, global memory, read in every folder on this machine.
- `<project>/CLAUDE.md`, project memory, read only while standing in that
  project. `~/ai-course/CLAUDE.md` does not exist; the one from Course 0 lives
  at `~/ai-course/00-terminal-fluent/follow-along/02-claude/CLAUDE.md`, which
  is why it only takes effect inside that folder.

Three separate things that all happen to live near the word "global": the
program (`-g`), the memory file (`~/.claude/CLAUDE.md`), and the skills folder
(`~/.claude/skills/`). Episode 1 is where a viewer is most likely to fuse
them, so it is worth saying that sentence out loud on camera.
