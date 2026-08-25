# Lesson 4: GitHub, the Words and the One Move

**Doctrine:** a repo is a folder with a memory; GitHub is where folders with memories live in public.
**Prerequisites:** Lessons 1-3, a free GitHub account (github.com, free tier is enough).
**Artifact:** this course, cloned onto your machine, opened from your terminal.
**Companion:** none (written only).

## Why this exists

Every lesson in Course 1 assumes you can say "clone the repo" without flinching.
This lesson defines the five words that sentence depends on, then has you do
the one move you need: copying this course to your machine. Making changes and
saving history come later, live, in Course 1 episode 4. Here you only read.

## The five words

| Word | Plain English |
|------|---------------|
| repository (repo) | A folder whose entire change history is saved with it |
| commit | One saved snapshot of that folder, with a note saying what changed |
| clone | Copy a repo from GitHub onto your machine, history included |
| push | Send your new commits up to GitHub |
| pull | Bring down commits someone else pushed |

### Words you will meet later

Not on the pass test. You only need to recognize them when GitHub uses them.

- **README** is the file GitHub shows first, the repo's front page.
- **fork** is your own copy of someone else's repo, under your account.
- **issue** is a public note on a repo: a bug report, a question, a request.

Git is the tool that tracks the history on your machine. GitHub is the website
where repos are shared. Same relationship as email and Gmail: one is the thing,
the other is a popular place the thing lives.

## The one move: clone this course

1. Make a GitHub account at github.com if you do not have one. Off this page:
   pick a username you can say out loud.
2. Check git is installed: `git --version`. Mac has it (a popup may offer to
   install developer tools; accept). WSL: `sudo apt install git`.
3. Stand somewhere sensible and clone:

```
cd ~
git clone https://github.com/drakegriffith/ai-course.git
cd ai-course
ls
```

4. Read the front page from the terminal: `cat README.md`. You are now holding
   the same files the course is taught from.
5. Later, when the course updates, `git pull` inside that folder brings the
   new material down. That is the only git command Course 0 asks you to reuse.

## Exercises

1. On github.com, open the course repo in the browser and find the same
   README you just `cat`ed. Two views of one folder.
2. Open the repo's Issues tab and read one. You now know where questions go.
3. From memory, explain the difference between clone and pull in one sentence
   each.

## You can move on when

You can define all five words in plain English, and you have this course
cloned, entered, and listed from your own terminal.

*Verify the clone URL against the published repo before posting this lesson.*
