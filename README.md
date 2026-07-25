# vibecode-course

Two documents for generating a **self-contained interactive course that runs inside Claude Code
or Cowork** — a folder of Markdown + JSON where Claude itself is the tutor. No website, no video
platform, no LMS, no code to run.

This repo is the *recipe*, not the course. Running the builder prompt is what produces the actual
course folder.

## What's here

| File | What it is |
|---|---|
| [BUILDING-A-CLAUDE-COURSE.md](BUILDING-A-CLAUDE-COURSE.md) | The **format spec** — subject-agnostic. Defines the file tree, the `CLAUDE.md` engine, the `progress.json` state contract, the lesson template, the seven commands, and a pre-ship quality checklist. |
| [fable5-course-builder-prompt.md](fable5-course-builder-prompt.md) | A **build prompt** for one specific course: take an absolute beginner from nothing to a live to-do app on Vercel, for $0. Hand it to Claude and it writes the course. |

## How the format works

A course is just a folder. When a learner opens it:

1. Claude auto-reads `CLAUDE.md` — the tutor persona and rules, no curriculum.
2. It reads `progress.json` to find where the learner left off. That file is the entire database:
   delete it to restart, copy it to back up, edit it to jump around.
3. It loads only the current lesson from `modules/` and runs a **Learn → Practice → Check** arc.
4. `/check` inspects the learner's real work in `workspace/` — a learner saying "done" isn't done.

Seven commands drive it: `/course`, `/lesson`, `/skip`, `/progress`, `/hint`, `/check`, `/exit`.
In Claude Code they're files in `.claude/commands/`; in Cowork the learner types the plain-English
equivalent, which is why the real logic lives in `CLAUDE.md`.

## The to-do app course (what the builder prompt makes)

Six modules, absolute beginner to a live URL:

1. **Welcome & setup** — Node, Git, Claude Code, terminal basics
2. **GitHub** — account, email verify, `gh auth login`
3. **Vercel** — account, Hobby (free) plan, connect to GitHub
4. **Create & deploy the skeleton** — scaffold Next.js, run local, push, import → first live URL
5. **Build the to-do app** — add, list, complete, delete, persist, polish
6. **Ship, verify, iterate** — push, verify live, feel the edit → deploy loop

Constraints it holds to: **$0 total** (free tiers only, localStorage instead of a database, no
backend), a non-technical audience with every term explained in plain English, and success criteria
the tutor can actually verify — `node -v`, `gh auth status`, a deployed URL that responds.

## Using it

Open this repo in Claude Code and paste the contents of `fable5-course-builder-prompt.md` as your
message. It builds `todo-app-course/` in stages, pausing after each module for you to reply
`continue`. Then open that folder in a fresh Claude Code session (or zip it for Cowork) and the
tutor greets you.

To build a course on a different subject, use `BUILDING-A-CLAUDE-COURSE.md` alone plus your own
topic brief — the scaffold never changes, only the lesson bodies and where *Practice* happens.

> Note: the builder prompt points at `/Users/tomleger/vibecode-course/BUILDING-A-CLAUDE-COURSE.md`
> for the spec, but this repo now lives at `~/repo/vibecode-course`. Fix the path before running it,
> or just leave it — the prompt is written to be sufficient on its own if the file isn't found.
