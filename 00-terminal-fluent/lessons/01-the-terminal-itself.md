# Lesson 1: The Terminal Itself

**Doctrine:** the terminal tells the truth; learn to read it.
**Prerequisites:** a Mac, or Windows with WSL installed. Nothing else.
**Artifact:** you, standing in a folder you made, knowing exactly where you are.

## Why this exists

Every AI tool in this course runs inside a terminal. The terminal is a text
conversation with your computer: you type a command, it answers. That is the
whole trick. Apps hide the computer behind buttons; the terminal shows it to
you directly, which is exactly why AI tools live there.

## Opening it

- Mac: press Cmd+Space, type "Terminal", press Enter.
- Windows: install WSL once (Microsoft's guide, "wsl --install"), then open
  the Ubuntu app. Everything in this course happens inside that window.

## Reading the prompt

The line waiting for you is the prompt. It usually shows your username, your
machine, and the folder you are standing in. One idea unlocks everything:
**you are always standing somewhere.** Every command runs from that spot.

## The eight commands that make you dangerous

| Command | Plain English | Try it |
|---------|---------------|--------|
| `pwd` | Where am I standing? | `pwd` |
| `ls` | What is in this folder? | `ls` |
| `cd foldername` | Walk into a folder | `cd Documents` |
| `cd ..` | Step back out | `cd ..` |
| `cd ~` | Go home from anywhere | `cd ~` |
| `mkdir name` | Make a new folder | `mkdir ai-course` |
| `cat file` | Show a file's contents | `cat notes.md` |
| `open .` (Mac) / `explorer.exe .` (WSL) | Show this folder in the normal file window | `open .` |

Two habits that separate the fluent from the frustrated:

- **Tab completion.** Type the first letters of a folder or file, press Tab,
  the terminal finishes it. Never type a full path by hand.
- **Ctrl+C.** The escape hatch. If something is running and you want out,
  Ctrl+C stops it. You cannot break your computer with it.

Also useful: press the up arrow to repeat earlier commands, and type `clear`
when the screen gets noisy. The history is still there; `clear` only tidies
the view.

## Paths in one paragraph

A path is a folder address. `/Users/you/ai-course` is absolute: the full
address from the top. `ai-course` alone is relative: measured from where you
are standing. `~` is shorthand for your home folder. When a tool says "file
not found," the answer is almost always "you are standing in the wrong place";
`pwd` first, then look again.

## Exercises

1. Go home (`cd ~`), make a folder called `ai-course`, walk into it, prove
   you are there with `pwd`.
2. Make a file: `echo "day one" > notes.md`, then read it back with `cat`.
3. Walk two folders away, then get back to `ai-course` using Tab completion
   the whole way.
4. Start typing a command, change your mind, and get out with Ctrl+C.

## You can move on when

You can open a terminal, say where you are, get anywhere by path, and make
and read a file, all without touching the mouse.
