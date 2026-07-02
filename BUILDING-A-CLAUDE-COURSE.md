# How to Build a Self-Contained Course Inside Claude Code / Cowork

> **Audience:** An AI/LLM (or a human directing one) tasked with generating a complete,
> interactive course that runs *entirely inside Claude Code or Claude Cowork* — no website,
> no video platform, no external LMS. Claude itself is the tutor.
>
> **Works for any subject:** programming, cooking, music theory, financial literacy,
> language learning, a company's internal onboarding — anything teachable in text +
> hands-on practice. The format is content-agnostic; only the lesson bodies change.

---

## 1. The core idea (read this first)

A course in this format is **a folder of Markdown + JSON files**. When a learner opens the
folder in Claude Code (or unzips it in Cowork), Claude reads a single instruction file
(`CLAUDE.md`), discovers where the learner left off (`progress.json`), and becomes an
**interactive tutor** for the duration of the session.

There is no code to run and no server. The "software" is the prompt. Three properties make
it work:

1. **The medium is the message.** The learner practices *inside the same tool they're being
   taught in* (or a tool well-suited to the subject). Learning and doing share one surface.
2. **Claude is the LMS.** Navigation, grading, hints, and progress tracking are all behaviors
   described in plain English in `CLAUDE.md` — not features of an app.
3. **State lives in a file.** `progress.json` is the entire database. Delete it to restart;
   copy it to back up; edit it to jump around.

Your job as the builder is to produce that folder so that the *first message a learner sees
is a working, welcoming tutor* — with zero setup beyond opening the folder.

---

## 2. Required file structure

Produce exactly this layout (rename `workspace`/`playground` to fit the subject if helpful):

```
<course-name>/
├── CLAUDE.md              # THE ENGINE. Tutor persona + rules + how to run the course.
├── README.md             # Human-facing quick start: what it is, how to open, commands.
├── progress.json         # Learner state. Ships with a "not started" default.
├── .claude/
│   └── commands/         # One .md file per slash command (Claude Code only).
│       ├── course.md
│       ├── lesson.md
│       ├── skip.md
│       ├── progress.md
│       ├── hint.md
│       ├── check.md
│       └── exit.md
├── modules/              # THE CURRICULUM. One folder per module, one file per lesson.
│   ├── 01-<module-slug>/
│   │   ├── _module.md    # Module intro: goal, lesson list, what they'll be able to do.
│   │   ├── 01-<lesson>.md
│   │   ├── 02-<lesson>.md
│   │   └── ...
│   ├── 02-<module-slug>/
│   └── ...
├── workspace/            # Where the learner builds graded exercises. Starts ~empty.
│   └── .gitkeep
├── playground/           # Free, ungraded sandbox. A README inviting experimentation.
│   └── README.md
└── reference/            # Cheat sheet, glossary, troubleshooting, further reading.
    ├── cheatsheet.md
    ├── glossary.md
    └── troubleshooting.md
```

**Why each piece exists**

| Path | Role |
|---|---|
| `CLAUDE.md` | Auto-loaded by Claude on open. Contains everything Claude needs to *behave* as the tutor. This is 80% of the work. |
| `README.md` | For the human before Claude takes over. Setup + command list. |
| `progress.json` | Single source of truth for "where am I." |
| `.claude/commands/` | Turns `/lesson`, `/check`, etc. into real slash commands in Code. In Cowork, learners just say the same thing in plain English. |
| `modules/` | The content. Kept out of `CLAUDE.md` so the engine stays small and lessons load on demand. |
| `workspace/` | Keeps graded work separate from course machinery. |
| `playground/` | Lowers the stakes — a place to try things without "failing" a check. |
| `reference/` | Quick lookup so lessons don't have to re-explain basics. |

---

## 3. `CLAUDE.md` — the engine (the most important file)

This file is auto-read when the folder opens. Write it *as instructions to Claude*, in the
second person. It must define six things:

### 3.1 Persona & tone
Give the tutor a name and a voice appropriate to the subject and audience (patient, concise,
encouraging; never condescending). State the audience's assumed starting level.

### 3.2 Startup behavior
Exactly what to do on the first message of a session:
1. Read `progress.json`.
2. If `status` is `not_started`, greet the learner, explain the course in 3–4 lines, list
   the commands, and offer to begin Lesson 1.
3. Otherwise, welcome them back and summarize where they are ("You're on Module 2, Lesson 3.
   Type `/lesson` to continue.").
4. Never dump the whole curriculum unprompted.

### 3.3 The command set (behaviors)
Define what each command *does*. (The files in `.claude/commands/` just forward to these
rules; the actual logic lives here so Cowork works too.) See §6.

### 3.4 Lesson-running rules
- Load only the current lesson file; don't paste future lessons.
- Follow the **Learn → Practice → Challenge** arc (see §5).
- After *Learn*, pause and check for understanding before *Practice*.
- During *Practice*, let the learner attempt before revealing answers. Use `/hint` for nudges.
- On `/check`, evaluate the learner's actual work in `workspace/` (or their described answer)
  against the lesson's success criteria; give specific, kind feedback; only mark complete when
  criteria are genuinely met.

### 3.5 Progress-tracking rules
- After a lesson is completed, update `progress.json` (mark the lesson done, advance the
  pointer, append to history, award any badge).
- Always write the file back; never keep progress only in memory.
- If the file is missing or corrupt, recreate it from the default and tell the learner.

### 3.6 Guardrails
- Stay in tutor role; if asked off-topic questions, answer briefly then steer back.
- Don't let the learner skip a `/check` by asserting they're done — verify.
- Keep responses short enough to read in the chat; break long lessons into steps.

> **Rule of thumb:** `CLAUDE.md` should be readable in a few minutes. All *content* lives in
> `modules/`. `CLAUDE.md` is *rules*, not curriculum.

---

## 4. `progress.json` — the state file

Ship this default (course "not started"):

```json
{
  "version": 1,
  "course": "<course-name>",
  "status": "not_started",
  "current": { "module": 1, "lesson": 1 },
  "completed": [],
  "badges": [],
  "history": [],
  "settings": { "hints_used": 0, "started_at": null, "last_seen_at": null }
}
```

Field contract (document this inside `CLAUDE.md` so Claude updates it consistently):

- `status`: `not_started` | `in_progress` | `completed`.
- `current`: pointer to the next lesson to serve.
- `completed`: array of `"M.L"` ids, e.g. `["1.1","1.2"]`.
- `badges`: earned milestone ids (e.g. `"module-1-complete"`).
- `history`: append-only log entries `{ "id": "1.1", "at": "<iso>", "result": "passed" }`.
- `settings`: lightweight counters / timestamps.

Keep it small and human-editable — that portability is a feature.

---

## 5. Lesson file format (the repeatable unit)

Every lesson is one Markdown file with a fixed skeleton. Consistency lets Claude parse and run
any lesson the same way. Use this template:

```markdown
---
id: "2.3"
module: 2
lesson: 3
title: "<Lesson title>"
estimated_minutes: 8
objectives:
  - "<what the learner will be able to do>"
prerequisites: ["2.2"]
success_criteria:
  - "<observable, checkable condition for /check to pass>"
badge: null            # or an id if this lesson completes a milestone
---

## Learn
<Concise explanation of the concept. Prefer one clear idea per lesson.
Use a concrete example. Keep it to what's needed for the Practice below.>

## Practice
<A guided, hands-on task. Tell the learner exactly what to produce and WHERE
(e.g. "create workspace/my-note.md with ..."). Make it small and unambiguous.>

## Check
<What Claude should verify on /check. Reference success_criteria. Describe both
the pass case and common mistakes to give targeted feedback on.>

## Challenge (optional)
<A harder, open-ended extension for motivated learners. Not required to advance.>

## Hints
- <Hint 1 — smallest useful nudge>
- <Hint 2 — more direct>
- <Hint 3 — nearly the answer>
```

Design guidance:
- **One idea per lesson.** 5–10 minutes each. If it's bigger, split it.
- **Practice must be checkable.** Vague tasks make `/check` meaningless. Anchor to a file, an
  output, or a specific answer.
- **Escalating hints.** Three tiers so `/hint` can reveal progressively.
- **Objectives are promises.** The success criteria should test exactly those objectives.

Also give each module a `_module.md` with its goal, its lesson list, and the capability the
learner walks away with.

---

## 6. The command set

Define these seven. In Claude Code each is a file in `.claude/commands/`; in Cowork the learner
just types the plain-English equivalent, so the real behavior must live in `CLAUDE.md`.

| Command | Behavior |
|---|---|
| `/course` | Show a compact menu: modules, progress bar, and "continue" prompt. |
| `/lesson` | Start or resume the `current` lesson; run the Learn→Practice arc. |
| `/skip [id]` | Jump to a lesson (e.g. `/skip 3.2`). Update `current`; warn if prerequisites unmet. |
| `/progress` | Show completed count, % done, badges earned, current position. |
| `/hint` | Reveal the next escalating hint for the active exercise. |
| `/check` | Evaluate the learner's work against `success_criteria`; pass → mark complete + advance. |
| `/exit` | Wrap up: summarize the session, save progress, offer a one-line feedback prompt. |

Each `.claude/commands/*.md` file can be as short as: a title, a one-line description, and
"Follow the `<command>` rules defined in CLAUDE.md." Keep the logic centralized.

---

## 7. Authoring workflow (the order to build in)

Follow these steps to generate a course from a topic brief:

1. **Scope it.** Nail down: subject, audience level, the single "you can now do X" outcome,
   and roughly how many modules/lessons (aim 4–8 modules, 4–8 lessons each).
2. **Draft the outline.** Module titles → lesson titles → one-line objective per lesson.
   Sequence so each lesson only depends on earlier ones.
3. **Write `CLAUDE.md`.** The engine, per §3. Do this before content so the rules are fixed.
4. **Write the default `progress.json`.** Per §4.
5. **Generate lessons module by module.** Use the §5 template. Fill Learn/Practice/Check/
   Challenge/Hints and the frontmatter for every lesson.
6. **Write `_module.md`** for each module.
7. **Create the command files** in `.claude/commands/` (§6).
8. **Populate `reference/`** — cheat sheet, glossary, troubleshooting — pulled from lesson
   content so learners get quick lookup.
9. **Seed `workspace/` and `playground/`** with a `.gitkeep` / inviting README.
10. **Write `README.md`** — human quick start, both Code and Cowork paths, command table.
11. **Self-test (§9)** — dry-run the first-open experience and one full lesson.

---

## 8. Adapting to any content type

The scaffold never changes; the "hands-on surface" does. Pick where *Practice* happens:

- **Coding / tools:** learner edits files in `workspace/`; `/check` inspects those files.
- **Writing / language / marketing:** learner drafts text in `workspace/`; `/check` critiques
  against rubric criteria.
- **Analytical subjects (math, finance, logic):** learner submits answers in chat or a file;
  `/check` verifies the reasoning and result.
- **Physical / offline skills (cooking, fitness, music):** learner *describes* what they did or
  uploads a photo/notes; `/check` evaluates the description against criteria. Practice is
  reflection + planning rather than file output.
- **Knowledge / onboarding:** Practice = short scenarios or quizzes; `/check` grades responses.

The invariant: **every lesson ends in something the learner produces, and `/check` can judge
it.** If you can't define a checkable artifact, redesign the Practice.

---

## 9. Quality checklist (verify before shipping)

- [ ] Opening the folder produces a warm, correct greeting with commands — no setup needed.
- [ ] `progress.json` ships as `not_started` and is updated after every completed lesson.
- [ ] Every lesson has valid frontmatter, all four sections, and 3 escalating hints.
- [ ] Every `success_criteria` is observable and testable by `/check`.
- [ ] Lessons are 5–10 min and cover one idea each; prerequisites form a clean chain.
- [ ] All seven commands work in Code (files present) AND as plain English in Cowork
      (logic in `CLAUDE.md`).
- [ ] `CLAUDE.md` is rules-only; no curriculum leaked into it; it stays short.
- [ ] `reference/` covers the terms and steps lessons assume.
- [ ] Nothing depends on the internet, an account, or a running server.
- [ ] Restart works: deleting `progress.json` cleanly starts over.

---

## 10. Design principles (the spirit, not just the mechanics)

1. **Load on demand.** Keep `CLAUDE.md` lean; pull lessons only when reached. Context is finite.
2. **State is a file, and files are portable.** Everything survives a restart because it's on disk.
3. **Verify, don't trust.** `/check` inspects real artifacts; a learner saying "done" isn't done.
4. **Small, frequent wins.** Short lessons + visible progress + badges keep momentum.
5. **Meet the learner where they are.** Resume exactly, skip freely, hint gradually.
6. **Practice on the real surface.** Collapse the gap between learning and doing — that collapse
   is what makes this format feel like magic.

---

*This document is a build spec. Hand it (plus a topic brief) to an LLM and it can generate a
complete, self-contained Claude Code / Cowork course.*
