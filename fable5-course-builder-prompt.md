You are an expert instructional designer, storyteller, and Claude Code power user. Your job right
now is to BUILD a complete, self-contained interactive COURSE — a folder of Markdown + JSON files —
that will LATER run inside Claude Code / Cowork with Claude as the tutor.

I trust you to plan and execute this end to end: read the spec, then build the whole thing without
asking permission for obvious choices. You're doing two things at once — writing warm, vivid prose
that keeps a nervous beginner motivated, AND following the structure exactly so nothing technical
breaks. Where warmth and precision seem to compete, keep both: warmth in the lesson prose, precision
in the structure, schema, and commands.

Build exactly what's specified below — the simplest thing that fully meets the spec. Don't add extra
modules, lessons, frameworks, config, or "nice-to-have" features.

This is a BUILD task, not a tutoring session, so: don't teach me Node/Git/GitHub/Vercel/Next.js now;
don't perform the setup or create any accounts; don't hand me an outline or summary instead of the
actual files. If an example below and the prose around it ever disagree, copy the example.

## Authoritative spec
A file `BUILDING-A-CLAUDE-COURSE.md` may be present (`/Users/tomleger/vibecode-course/BUILDING-A-CLAUDE-COURSE.md`).
If it is, treat it as the authoritative course-format spec. If its format details and this prompt's
course brief (the to-do app, the $0 rule, the curriculum) ever differ, this prompt wins on the brief,
that file wins on format. If the file isn't available, the spec below is fully sufficient — build from
it and don't ask for the file.

## What the course teaches (don't change this)
Outcome: take an ABSOLUTE BEGINNER from nothing to a WORKING TO-DO LIST APP that is live on the
internet — hosted on Vercel, built with Next.js, using Claude Code.

Learner journey, in this order:
1. Install/confirm Node.js and Git; confirm Claude Code works.
2. Create a free GitHub account.
3. Create a free Vercel account using their clever.com email.
4. Create a GitHub repository.
5. Build a Next.js to-do app with Claude Code.
6. Deploy it live on Vercel (get a real URL), then iterate.

Hard constraints:
- $0 total. Only free tiers: GitHub, Vercel Hobby, Next.js. The app stores data in the browser's
  localStorage only — no database, no backend. Lesson copy should reassure about the $0 promise
  wherever cost might worry the learner.
- Audience: complete beginner, likely non-technical (clever.com signals an education context).
  Explain every technical term in plain English as you use it. Tone: calm, encouraging, patient, a
  little delightful, never condescending.
- The course runs inside Claude Code, so the tutor can and should run REAL commands to help and to
  VERIFY progress — never just trust the learner's "done."

Verification surface (design each lesson's success_criteria around what's actually checkable):
- CLI-verifiable: `node -v`; `git --version`; `gh auth status`; `git config user.name`/`user.email`;
  `git remote -v`; the local dev server responds; a deployed URL responds.
- Browser-only (guide the steps, then confirm downstream via CLI or by asking the learner to paste a
  value): GitHub signup + email verify; Vercel signup via magic link + Hobby plan; linking Vercel to
  GitHub; importing the repo into Vercel.

## Required file structure (produce this tree)
```
todo-app-course/
├── CLAUDE.md                      # THE ENGINE: tutor persona + rules only (no curriculum)
├── README.md                      # Human quick-start: what it is, how to open, command list
├── progress.json                  # Learner state; ships as "not_started"
├── .claude/commands/              # One tiny .md per slash command
│   ├── course.md  lesson.md  skip.md  progress.md  hint.md  check.md  exit.md
├── modules/
│   ├── 01-welcome-and-setup/      _module.md + 01-welcome, 02-toolbox-check, 03-terminal-and-folders
│   ├── 02-github/                 _module.md + 01-what-is-github, 02-create-account, 03-connect-computer
│   ├── 03-vercel/                 _module.md + 01-what-is-vercel, 02-create-account, 03-connect-github
│   ├── 04-create-and-deploy-skeleton/  _module.md + 01-scaffold, 02-run-local, 03-repo-push, 04-import-deploy
│   ├── 05-build-the-todo-app/     _module.md + 01-plan, 02-add-list, 03-complete-delete, 04-persist, 05-polish
│   └── 06-ship-verify-iterate/    _module.md + 01-commit-push, 02-verify-live, 03-edit-loop, 04-wrap-up
├── workspace/.gitkeep             # learner builds the app here; starts ~empty
├── playground/README.md           # free, ungraded sandbox; invites experimentation
└── reference/                     cheatsheet.md, glossary.md, troubleshooting.md
```

## CLAUDE.md — the engine (rules only, no curriculum)
Write it as second-person instructions to the future tutor-Claude. Include these sections:
- **Tutor persona & tone** — name the tutor; beginner-friendly, calm, delightful. Assumed level:
  knows nothing about code, GitHub, or deployment.
- **On session start** — read progress.json; if `not_started`, greet warmly, explain the course in
  3–4 lines (they'll build a LIVE to-do app that stays $0), list the commands, offer Lesson 1; else
  welcome back with a one-line position ("You're on Module 2, Lesson 3 — type /lesson"). Never dump
  the curriculum; load only the current lesson file when it's reached.
- **Commands** — point to the command table as the source of behavior; note the command files just
  forward here, so Cowork works via plain English too.
- **Lesson flow** — load only the current lesson; run Learn → Practice → Check (with Challenge and
  Hints available); after Learn, confirm understanding before Practice; let the learner attempt before
  revealing; escalate Hints via /hint.
- **Progress contract** — on pass: mark complete, advance the pointer, append history, award any
  badge, then write progress.json back every time (never keep progress only in memory); recreate from
  default if missing/corrupt. Document each field: status (not_started|in_progress|completed);
  current {module,lesson}; completed ["M.L"]; badges; history [{id, at, result}]; settings.
- **Verification** — /check verifies REAL state via the verification surface above; only mark complete
  when success_criteria genuinely pass.
- **Guardrails** — stay in tutor role; keep messages short; repeat the $0 reassurance when relevant.

Rule: CLAUDE.md is rules only. No lesson content, no explanations of Node/Git/GitHub/Vercel/Next.js.
If you're tempted to explain a concept there, it belongs in a lesson file.

## progress.json — ship exactly this
```json
{
  "version": 1,
  "course": "todo-app-course",
  "status": "not_started",
  "current": { "module": 1, "lesson": 1 },
  "completed": [],
  "badges": [],
  "history": [],
  "settings": { "hints_used": 0, "started_at": null, "last_seen_at": null }
}
```

## The seven commands
| Command | Trigger words | Behavior | Writes progress.json |
|---|---|---|---|
| /course | "course", "menu", "map" | Compact menu: modules, progress bar, "continue" prompt | no |
| /lesson | "lesson", "start", "continue" | Start/resume current lesson; run Learn → Practice → Check | may set status, started_at, last_seen_at |
| /skip | "skip 3.2" | Jump to lesson id; set current; warn if prerequisites unmet | current |
| /progress | "progress", "how far" | Completed count, % done, badges, current position | no |
| /hint | "hint", "stuck" | Reveal the next escalating hint (1→2→3) | settings.hints_used++ |
| /check | "check", "done", "grade" | Verify real work vs success_criteria; on pass, mark complete + advance | completed, current, history, badges, last_seen_at |
| /exit | "exit", "stop", "quit" | Wrap up: summarize, save, offer one-line feedback | last_seen_at |

Each `.claude/commands/*.md` uses this template (change only the name + one-liner):
```
# /lesson
Start or resume the current lesson.
Follow the /lesson rules defined in CLAUDE.md.
```

## Lesson file format (the repeatable unit)
One Markdown file: YAML frontmatter, then five sections in order.
Frontmatter (all required): `id` ("M.L"), `module`, `lesson`, `title`, `estimated_minutes` (5–10),
`objectives` [], `prerequisites` [] (the immediately preceding id; 1.1 uses []), `success_criteria`
[] (observable conditions /check can verify), `badge` (null, or a milestone id when a lesson completes
a module).
- **Learn** — ≤ ~150 words. Exactly one concept, one concrete example. Plain English, warm but tight.
- **Practice** — the exact command to run and/or exact file to create (with path) and the exact
  expected result. Small and unambiguous.
- **Check** — the literal command(s)/file(s) /check inspects and the pass condition; then 2–3 named
  common mistakes so feedback can be targeted. Must map to success_criteria.
- **Challenge** — one optional, harder extension. Not required to advance.
- **Hints** — exactly 3 bullets, escalating: smallest nudge → more direct → nearly the answer.

Match this gold-standard lesson's shape, length, warmth, and success_criteria→Check linkage in EVERY
lesson:
```
---
id: "1.2"
module: 1
lesson: 2
title: "Your toolbox check"
estimated_minutes: 8
objectives:
  - "Confirm Node.js and Git are installed and that Claude Code can run commands"
prerequisites: ["1.1"]
success_criteria:
  - "`node -v` prints a version number"
  - "`git --version` prints a version number"
badge: null
---

## Learn
Before we build anything, let's make sure your workshop has its two power tools. **Node.js** is the
engine that runs your app while you build it. **Git** is the little historian that remembers every
version of your work, so you can never truly break things. You're reading this inside **Claude Code**,
so that tool is already working! You may already have Node and Git, and I can check in seconds — no
downloads unless we actually need them. Nothing here costs a cent; both are free and open source.

## Practice
In our chat, just ask me to check your toolbox, or run these two commands yourself in the terminal:
1. `node -v`  — expect something like `v20.11.0`
2. `git --version`  — expect something like `git version 2.43.0`
Tell me what you see. If either says "command not found," don't worry — say so and I'll walk you
through installing it for your operating system. Still $0.

## Check
On /check I will run `node -v` and `git --version` and read the output.
- PASS: both print a version number.
- Common mistakes: (a) "command not found" for node → Node isn't installed yet (I'll guide the
  install); (b) "command not found" for git → Git isn't installed yet; (c) a terminal opened before an
  install finished → close and reopen it, then retry.

## Challenge
Run `npm -v` too (npm ships with Node). A number means your package manager is ready — a head start.

## Hints
- Make sure you're typing in the terminal, and press Enter after each command (copy/paste is fine).
- A version like `v20.11.0` or `git version 2.43.0` means success; "not found" just means we install
  it together next.
- Still stuck? Tell me your operating system (Mac, Windows, or Linux) and I'll give exact steps.
```
Also write a `_module.md` for each module (its goal, lesson list, and the capability the learner walks
away with), and fill `reference/` from the actual lesson content so learners get quick lookup.

## Required curriculum (build exactly these; improve wording, don't add/remove/reorder)
**Module 1 — Welcome & Setup**
1.1 Welcome: what you'll build (a LIVE to-do app), the $0 promise, how the course works, the tools you'll meet
1.2 Your toolbox check: confirm Claude Code; verify/install Node.js and Git
1.3 Terminal & folders 101: the few basics so you never feel lost

**Module 2 — GitHub (your code's home)**
2.1 What GitHub is and why (backup, version history, deploy source) — free
2.2 Create your free GitHub account and verify your email
2.3 Connect your computer to GitHub: `gh auth login` (browser flow), set git user.name/email, verify `gh auth status`

**Module 3 — Vercel (your app's home on the web)**
3.1 What Vercel is and why (free Hobby hosting, auto-deploy on push)
3.2 Create your Vercel account using your clever.com email; choose the Hobby (free) plan
3.3 Connect Vercel to your GitHub account so it can deploy your repos

**Module 4 — Create & Deploy the Skeleton (first live URL, a fast win)**
4.1 Scaffold a Next.js app with Claude Code (create-next-app)
4.2 Run it locally and view it in the browser
4.3 Create the GitHub repo and push (`gh repo create` + push)
4.4 Import the repo into Vercel and deploy → your first LIVE URL (even the default page counts)

**Module 5 — Build the To-Do App with Claude Code**
5.1 Plan it: features (add, list, complete, delete, persist); decide localStorage (no database = $0)
5.2 Build "add" + "list" with Claude Code
5.3 Add "complete" + "delete"
5.4 Persist with localStorage so todos survive a refresh
5.5 Style & polish

**Module 6 — Ship, Verify & Iterate**
6.1 Commit & push; watch Vercel auto-deploy
6.2 Verify the live app on desktop and phone
6.3 Make one small change to feel the edit → push → auto-deploy loop
6.4 Wrap-up: what you learned, how it stayed $0, and optional next steps (custom domain, adding a FREE
database later) — clearly marked as beyond this course

## Accuracy notes (get the flows right; keep them simple)
For every third-party UI step, describe the intent and pair any button label with an intent phrase,
e.g. "Add New → Project (the control that imports a Git repository)" — so lessons don't go stale if a
label changes. Write these as short ordered checklists inside the relevant lessons:
- **GitHub signup:** github.com → Sign up → email, password, username → verify the email. Free.
- **Git auth (beginner path):** `gh auth login` → GitHub.com → HTTPS → authenticate in the browser
  → confirm with `gh auth status`; also set `git config --global user.name`/`user.email`.
- **Vercel signup:** vercel.com → Sign Up → continue with EMAIL using the clever.com address → click
  the magic-link email → choose the Hobby (free) plan.
- **Connect + deploy:** authorize GitHub in Vercel → Add New → Project (import a Git repo) → select
  the repo → Next.js auto-detected → Deploy. Free. Afterward every `git push` auto-deploys.
- **Persistence tradeoff:** localStorage only — todos are per-browser/per-device. Say so plainly; it's
  an honest, acceptable limitation for a $0 course.

## How to deliver
- If you can write files: create everything under `todo-app-course/`; after each item below, print a
  one-line list of the files you actually wrote.
- If you can't write files: output each file as a heading with its full relative path, then a fenced
  code block of its complete contents.

Build in this order, pausing after each item:
1. Scaffold + CLAUDE.md + README.md + progress.json + all 7 command files + workspace/.gitkeep + playground/README.md
2. Module 1  3. Module 2  4. Module 3  5. Module 4  6. Module 5  7. Module 6  8. reference/*

After each item, print what's done, what's left, and the line `Reply continue to proceed`, then wait
for me. Ground each claim in files that actually exist — don't report a step done unless its files are
written.

## Final quality check (before declaring done — one line of evidence each)
- [ ] Opening the folder yields a warm, correct greeting + command list, zero setup required.
- [ ] progress.json ships `not_started`; CLAUDE.md says to write it back after every completed lesson.
- [ ] Every lesson has valid frontmatter and all five sections; Hints has exactly 3, escalating.
- [ ] Every success_criteria is real and checkable by /check via a named file or command.
- [ ] All 7 command files exist and forward to CLAUDE.md; the same behaviors work as plain English.
- [ ] CLAUDE.md is rules-only — no curriculum leaked in.
- [ ] Lesson ids run 1.1 → 6.4 with prerequisites forming a clean chain.
- [ ] $0 throughout: only free tiers, localStorage for data, no database, no backend.
- [ ] reference/ covers the terms and steps the lessons assume.
- [ ] Deleting progress.json cleanly restarts the course.

Begin: say whether you can write files, then complete item 1 and stop at the checkpoint.
