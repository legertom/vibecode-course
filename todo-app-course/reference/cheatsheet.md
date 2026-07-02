# Cheatsheet — your quick-lookup for the whole course

A friendly reminder up front: **you almost never type these yourself.** Ada (that's Claude Code)
runs the commands for you and reads the results out loud. This page is just a handy map so you can
peek at what's happening behind the scenes — and feel a little more at home each time.

Nothing here can hurt your computer. If a command errors, that's completely normal — errors are
part of building, and Ada will calmly sort it out with you.

---

## The $0 recap

This entire course costs **$0**, start to finish. No credit card, ever. Here's why, in one glance:

- **GitHub** — free (your code's online home).
- **Vercel Hobby plan** — free (puts your app on the web). Still free even with your Clever work email.
- **Next.js** — free and open source (the toolkit your app is built with).
- **Your tasks** save in the browser's **localStorage** — no database, no server, nothing that bills.

If you ever see a "choose a plan" or "Pro" screen, the answer is always the **free** one. When in
doubt, ask Ada — she'll point you to the no-cost choice before you worry.

---

## Setup checks (Module 1)

These confirm your computer has the small helpers the app needs. Ada runs them and reads the versions.

| Command | What it does (plain English) |
|---|---|
| `node -v` | Shows your Node.js version — the engine that runs the build tools. We want **18.18 or newer**. |
| `npm -v` | Shows npm's version — Node's helper for downloading free building blocks. Any version is fine. |
| `git --version` | Shows your Git version — the tool that quietly saves versions of your work. Any version is fine. |
| `npx --version` | Shows npx's version — the helper used to create your app in one command (optional to check). |
| `gh --version` | Shows the GitHub CLI version — the tool that connects your computer to GitHub. |

**If something's missing (all free; full Mac walkthrough in `installing-on-mac.md`):**

| Situation | What to do (on a Mac) |
|---|---|
| Node.js missing or too old | **nodejs.org** → click **LTS** → open the `.pkg` → click through (enter your Mac password). Or `brew install node`. |
| Git missing | In Terminal: `xcode-select --install` → click **Install** (includes Git). Or `brew install git`. |
| GitHub CLI (`gh`) missing | Install the `macOS.pkg` from **cli.github.com**. Or `brew install gh`. |
| Just installed it but still "command not found" | **Fully quit and reopen Claude Code** — new tools are only seen by windows opened after installing. |
| Want one tool to manage everything | Optional: set up **Homebrew** (see `installing-on-mac.md`), then `brew install node gh`. |

---

## GitHub (Module 2)

Connecting your computer to your free GitHub account, and labeling your saves as yours.

| Command / Action | What it does (plain English) |
|---|---|
| Sign up at **github.com** | Create your free account. Work email *or* personal email — both are fine. |
| `gh auth login` | Logs your computer in to GitHub through your browser. Choose **GitHub.com → HTTPS → Login with a web browser**, then enter the one-time code. |
| `git config --global user.name "Your Name"` | Sets the name that stamps every saved snapshot as yours (keep the quotes). |
| `git config --global user.email "you@example.com"` | Sets the email label on your saves (keep the quotes). |
| `gh auth status` | Checks you're logged in to github.com. |
| `gh api user --jq .login` | Asks GitHub who you are — prints your username if the connection works. |
| `curl -sI https://github.com/<username>` | Confirms your public profile exists online (looks for **HTTP 200**). |

---

## Vercel (Module 3)

The free service that publishes your app to the web. These steps happen in your browser.

| Action | What it does (plain English) |
|---|---|
| Sign up at **vercel.com** | Create your free account. **Use your Clever work email** (the `clever.com` one). |
| Choose **"Continue with email"** | Vercel emails you a "magic link" — click it to sign in (no password to invent). |
| Choose the **Hobby** plan | The free plan. Free even with a work email — no card required. |
| Connect **GitHub** as a Git provider | Authorize Vercel to read your repositories so it can publish your app. Choose **All repositories**. |
| Import a project (to test) | Start a "New Project" import to confirm your GitHub repos are listable — you don't have to finish. |

---

## Scaffolding & running Next.js (Module 4)

Building the starter app and previewing it privately on your own computer.

| Command | What it does (plain English) |
|---|---|
| `npx create-next-app@latest todo-app --js --app --tailwind --eslint --no-src-dir --import-alias "@/*" --use-npm` | Builds a ready-to-run Next.js starter app in a folder named `todo-app`, using plain JavaScript, the App Router, and Tailwind styling. Run from inside `workspace/`. |
| `npm run dev` | Starts the local **dev server** so you can preview the app at `http://localhost:3000`. Run from inside `workspace/todo-app/`. |
| `curl -s -o /dev/null -w "%{http_code}" http://localhost:3000` | Quietly asks the local app for a page and prints only the response code. **200** means "all good." |
| Open **http://localhost:3000** in your browser | See your app running privately, only on your computer. |

The main file you'll edit later lives at **`workspace/todo-app/app/page.js`** (with `app/layout.js`
and `app/globals.css` alongside).

---

## Git commit / push (Modules 4 & 6)

Saving snapshots of your work and sending them to GitHub. All run from inside `workspace/todo-app/`.

| Command | What it does (plain English) |
|---|---|
| `git add -A` | Gathers up everything you changed, ready to save. |
| `git commit -m "Your message"` | Saves a labeled snapshot (a "commit") with that caption. |
| `git push` | Sends your saved snapshots up to GitHub. |
| `git add -A && git commit -m "Build the to-do app" && git push` | All three at once: gather, save, send. |
| `gh repo create todo-app --public --source=. --remote=origin --push` | Creates a new public GitHub repo, connects it to this folder as `origin`, and pushes your code — all in one command. |
| `git remote -v` | Shows the connection named `origin` pointing at your GitHub repo. |
| `gh repo view` | Shows your repo's details — proof it exists on GitHub. |
| `git status` | Shows what's changed and whether your branch is up to date with GitHub (`origin`). |
| `git log --oneline` | Lists your saved snapshots, newest first — your project's history and safety net. |

---

## The dev loop (Module 6)

The heartbeat of every website: **edit → push → live.** Once set up (you did that in Module 4),
Vercel republishes automatically whenever you push.

1. **Edit** — tell Ada the change you want; she edits `workspace/todo-app/app/page.js`.
2. **Save & push** — Ada runs `git add -A && git commit -m "..." && git push` from `workspace/todo-app/`.
3. **Deploy (automatic)** — Vercel notices the new code on GitHub and rebuilds your live site. No buttons.
4. **Verify** — wait about a minute, then reload your `.vercel.app` URL (a hard refresh clears any cache).

To confirm what's *actually* live (bypassing your browser's cache):

| Command | What it does (plain English) |
|---|---|
| `curl -sI <your-live-url>` | Fetches your live app's headers — looks for **HTTP 200** ("it's up"). |
| `curl -s <your-live-url>` | Fetches the live page's HTML — Ada checks your real heading text is in there, not the old starter page. |

---

## Where things live

- **`workspace/`** — your personal folder for everything you build in this course.
- **`workspace/todo-app/`** — your app (created in Module 4).
- **`workspace/todo-app/app/page.js`** — the app's home page; the file you edit most.
- **`playground/`** — a free, no-pressure place to experiment. Nothing here is graded.

You're doing great. Peek at this page anytime — and remember, Ada does the typing.
