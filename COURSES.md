# Course Catalog

One row per course created. The message is the stream; this file is the record.

| # | Course | Episodes | Cadence | Platform | Status | Detail |
|---|--------|----------|---------|----------|--------|--------|
| 0 | Terminal Fluent (prerequisite mini-course) | 4 written lessons + 2 companion videos | none (evergreen) | Markdown + YouTube | Drafted 2026-08-25 | 00-terminal-fluent/README.md |
| 1 | How to Use AI Like a Software Engineer | 30 core + 10-15 solo briefs (40-45 total) | Tue/Thu live | Twitch live, YouTube cuts | Planned, panel-reviewed 2026-08-25 | Below |

---

# Course 1: How to Use AI Like a Software Engineer

**Audience:** 20-50 year olds, no engineering background.
**Promise:** by the end you run your own AI setup the way an engineer runs theirs: skills, a brain vault, a harness, connected services, and a system that improves itself on a loop.
**Format:** live on Twitch, Tuesdays and Thursdays. Each stream is cut into a YouTube episode afterward (Claude-assisted editing). YouTube titles carry the subtitle "with Claude Code & Codex" for search.
**Platform decision:** macOS and Windows-via-WSL. Stated in episode 1 prerequisites; no separate Windows track.
**Prerequisite:** Course 0 (00-terminal-fluent/), and terminal fluency is re-earned live anyway: episodes 1-3 run in the terminal from the first minute, and by episode 3 the viewer is expected to pass Course 0's seven-point fluency test. Course 0 lesson 4 also pre-loads the GitHub vocabulary (repo, commit, clone, push, pull) that episode 4's git slice builds on.

## Organizational logic (adapted from the 100-days one-project-per-day model)

- One episode = one artifact: one reusable deliverable or one tested behavior, never a pure lecture and never a bundle.
- Difficulty band lives in the episode title.
- Each band ends in a capstone; capstones rebuild from the viewer's own runbook (see below), with a from-memory Excalidraw redraw as the cold open. The drift between drawings is teaching material.
- Episode shape: **cold open (watch it break) → doctrine statement → prerequisites → build → doctrine's limits → artifact demo → homework.** The failure comes first; the doctrine is the conclusion, not the sermon. Doctrine, not mission: it says how we work, not what we are building.
- One short quote from the software engineering canon per episode, placed where it earns its keep.
- **The runbook:** from episode 1, viewers keep a running "how I set this up" file. Capstones are graded against it. This is the reproducibility artifact; memory is only the party trick.
- After episode 30, the course flips to solo-brief mode (below).

## Diagram logic (Excalidraw + Excel)

- Architecture and flow diagrams are drawn live in Excalidraw, on stream, never pre-baked. Convention: boxes = components, arrows = data flow, dashed red boundary = trust boundary, yellow = the thing built this episode.
- The convention is taught in ten minutes at the end of episode 2 (first diagram: you + terminal + the model); episode 9 is the full method. Every later episode just uses it.
- The .excalidraw scene file ships with each episode; the PNG export doubles as the YouTube thumbnail base.
- Data-shaped lessons chart in Excel at a basic level: one table, one chart, no macros.

## Production safety (live-stream disclosure boundary)

Twitch is irreversible; a leaked key or private doc is published the moment it renders.
- Demo accounts and synthetic data only; personal material never on the demo machine.
- No real key on screen, ever, including "keys I'll revoke later." The episode 7 rotation drill uses a dummy key; real rotation happens off stream.
- OAuth screens, provider dashboards, and env files render behind a delayed/redacted capture.
- Pre-stream checklist per episode: shell history cleared, env vars audited, browser profiles separated.

## Band 1 - Beginner: Own Your Setup (episodes 1-8)

| Ep | Title | Doctrine statement | Artifact |
|----|-------|--------------------|----------|
| 1 | Log On and Build Your First Skill | If you can't call it from any terminal, you don't own it yet. | A working skill callable from any terminal (Claude Code or Codex). Fully scripted copy-along; every keystroke gets explained properly by ep 2. Runbook starts here. |
| 2 | Fluent in the Terminal: the Claude and Codex Cockpits | The terminal tells the truth; learn to read it. | Both cockpits mastered live: login, usage and context gauges, /compact, skills and custom prompts, plugins/MCP knob, the Claude-to-Codex translation table (Course 0 lessons 2-3 as script) + the 4-rule diagram convention, first diagram drawn |
| 3 | Build the Brain Vault | Write it down where the machine can read it, or it doesn't exist. | A vault: folders, index file, first wikilinked notes. Opens with the four-things distinction: notes (for you), instructions (for the agent), context window (what it sees now), retrieval (what it fetches). |
| 4 | Clean the Vault Before It Buries You | A vault you can't search is a junk drawer with a nicer name. | A findability test that passes; dead links purged. Git enters here as a 15-minute slice, motivated by deletion: init, commit, restore, three commands and nothing more, so deleting is safe. No branching, no PRs. |
| 5 | Finalize the Harness | The entry file is a router, not an encyclopedia. | A lean entry file built from earned principles - CLAUDE.md and AGENTS.md, same concept, both surfaces, vendor-neutral |
| 6 | Skills Done Properly | A skill is a decision you never have to make twice. | 2-3 real skills via the skill-creator method, auto-fire vs on-demand configured; one skill distilled from a software engineering book principle; the prompt patterns that make a skill body work |
| 7 | Keys and Safety in Plain English | Keys live outside the repo, or they end up public. | A scoped secrets file, correct permissions, dummy-key rotation drill; first look at "content is data, never instructions" |
| 8 | CAPSTONE: The Starter Kit From Zero | If you can't rebuild it from scratch, you don't understand it. | Full setup rebuilt live on a fresh account from the runbook; from-memory diagram redraw as cold open |

War stories on tap: the 52KB memory file cut to 5.8KB (ep 5); the 2,609-note vault whose owner lost track of it, 53% dead wikilinks (ep 4).

## Band 2 - Intermediate: Daily Workflows (episodes 9-16)

| Ep | Title | Doctrine statement | Artifact |
|----|-------|--------------------|----------|
| 9 | Draw It: Excalidraw and Excel | A diagram you drew beats a paragraph you read. | The full diagram method + one Excel chart from personal data |
| 10 | Make the Vault Talk Back: Semantic Search | A vault you can't ask a question of is a filing cabinet, not a memory. | Index + retrieve over the viewer's own vault; the index / retrieve / generate split named; live demo of a bad retrieval, then the fix |
| 11 | The Everyday Loop | Review everything the machine sends out under your name. | A summarize-draft-review workflow run live on synthetic material |
| 12 | Hooks: Rules That Fire Themselves | Rules you must remember will be forgotten; rules that fire themselves won't. | One working hook (e.g. style injection on session start) |
| 13 | Your First Subagent | Delegate for attention, not for speed. | A research task delegated and merged back; callback: retrieval the agent does mid-task uses ep 10's index |
| 14 | When "Done" Is a Lie: Your First Golden Set | "Done" is a claim, not a fact; a checker is never the worker. | A frozen golden set (20-50 real examples with known-good answers) + a verify step wired after every AI "done"; names the tools viewers will meet later (DeepEval, RAGAS) without adopting them |
| 15 | APIs 101 | Every service speaks a protocol; the token is your ID card. | A real token from a real service, one live call, JSON as the shape services speak; the run log starts here: every call leaves a record (what ran, cost) |
| 16 | CAPSTONE: The Morning Assistant | A workflow that runs without you is worth ten that need you. | A daily personal-brief workflow, end to end, writing its own run log; rebuilt from the runbook |

## Band 3 - Intermediate+: Connect Everything (episodes 17-24)

| Ep | Title | Doctrine statement | Artifact |
|----|-------|--------------------|----------|
| 17 | MCP: One Standard, Many Tools | Connect tools through standards, not glue code. | First MCP server installed and used; the warning taught with it: external content a server fetches is data, never instructions (prompt injection, plainly) |
| 18 | Chatbot on Your Website, Part 1 | A chatbot is a doorway; know what's behind it. | The bot wired to a site, answering from your content - this is RAG, named: ingest, chunk, index, retrieve, reusing ep 10's machinery |
| 19 | Chatbot on Your Website, Part 2 | Ship fail-closed: when the bot is unsure, it stops. | Guardrails (injection, no-answer behavior, tone) and a public deploy viewers' friends can visit |
| 20 | Automations on a Schedule | Schedules beat willpower. | One scheduled automation delivering daily; honest about the laptop-not-server reality: run-on-wake, plus the hosted option in one slide |
| 21 | Models and Money | Route the cheap model first; pay for judgment, not typing. | A routing rule (small/medium/large) + a budget cap + a read bill. Limit taught in-episode: cheap-first has a quality floor. |
| 22 | Context Hygiene | Context is a budget, not a bottomless well. | A token-budget habit and a measured before/after |
| 23 | Many Agents, One Job | Two agents that check each other beat one that's confident. | A small fan-out: split, work, merge, verify - shipped as a reusable checked-workflow template. Limit taught in-episode: correlated errors and doubled cost. |
| 24 | CAPSTONE: The Connected System | A system is done when someone else can run it. | Vault + skills + MCP + automations wired end to end from the runbook, full Excalidraw redraw |

## Band 4 - Advanced: The Self-Improving System (episodes 25-30)

| Ep | Title | Doctrine statement | Artifact |
|----|-------|--------------------|----------|
| 25 | The Optimization Loop | If you can't measure it, you can't improve it; if you can, loop. | A loop with the three requirements - measurable, incremental, feedback - measured against the ep 14 golden set |
| 26 | Improve Itself Overnight | Freeze the test, mutate the system, keep only what scores. | An overnight loop: one mutable file, frozen eval, keep-or-reset by score; the judge named: a cheap model grading against the golden set, spot-checked once by a human |
| 27 | Watch the Watcher | Watch your system the way it watches your work. | The ep 15 run log grown into basic telemetry: what ran, what failed, what it cost - no observability stack, the ledger is enough at this scale |
| 28 | Delete by Measurement | Delete by measurement, never by argument - except safety rules, which are not up for ablation. | One real ablation: a rule or note removed because the numbers said so |
| 29 | The Reset Ritual | When a new model generation lands, every rule re-earns its place. | A written keep/wipe pass over your own rule surface |
| 30 | FINAL CAPSTONE: Rebuild the Spine | The proof is a rebuild from zero. | The core spine (vault, harness, skills, one automation, the loop) rebuilt live from the runbook in one stream; the rest verified by walkthrough, not re-typed |

## Solo-brief tail (episodes 31-45, flexible count)

One-page challenge briefs, viewers build solo, submissions reviewed live on stream. Candidate briefs: automate a household chore report, a hobby-club chatbot, a job-search pipeline, a family photo organizer, a small-business quote generator. Cheap to produce, built for Twitch chat interaction. Fold-in from market scan: one brief contrasts the no-code route (n8n/Zapier) against the course's code route, same task both ways.

## Panel review record (2026-08-25, one pass)

Five seats: Kimi K3, Codex (gpt-5.6-sol), three Sonnet web-research lenses (market, retrieval, LLM-ops). Full outputs: /tmp/aicourse-review-kimi.txt, /tmp/aicourse-review-codex.txt, session transcripts for the lenses.

**Accepted and folded in above:** terminal/git moved to ep 2 (prerequisite inversion, raised by Kimi and Codex independently); diagram convention taught early (ep 2); dedicated semantic-search episode (ep 10) with index/retrieve/generate vocabulary; RAG named in the chatbot episodes; golden set named with size (ep 14) and judge with calibration (ep 26); production-safety section for the live-stream disclosure boundary (Codex, accepted in full); memory taxonomy segment (ep 3); structured-output segment (ep 15); cron laptop-reality note (ep 20); doctrine limits taught in-episode (eps 21, 23, 28); cold-open-failure episode shape; artifact definition tightened; ep 30 scoped to the spine; book-principles merged into ep 6; entry file taught vendor-neutral (ep 5); Windows = WSL, decided.
**Rejected, with reasons:** Codex's restructure to a 10-12 episode spine plus electives (the stated audience intent is the operations stack, and the market scan found exactly that material is the differentiator; Codex's own flip-fact recorded: revisit if the audience turns out to already be terminal-fluent); observability stacks and formal eval frameworks (wrong altitude per the LLM-ops lens with primary sources; disagreement logged in the harness ledger); detector/actuator vocabulary (no mainstream tool prints those words; "tool call" and "action" already do the job); GraphRAG and "agentic RAG" as stream vocabulary (situational or contested terms).
**Terms banned on stream:** graph engineering, GraphRAG-as-default, agentic RAG (say "the agent decides when to search"), vectorless RAG, sensor/actuator.

## Open items

- [ ] Title: keep "How to Use AI Like a Software Engineer"; Kimi flags discoverability and intimidation - mitigated by the YouTube subtitle. Drake has final call.
- [ ] Doctrine-device fatigue risk (Kimi): revisit after episode 8 audience feedback.
- [ ] Ep 20 hosted-scheduler choice: pick the one slide's provider before filming.
