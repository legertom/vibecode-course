---
id: "1.2"
module: 1
lesson: 2
title: "Toolbox check: Node.js and Git"
estimated_minutes: 10
objectives:
  - "Confirm your Mac has Node.js (version 18.18 or newer) and Git installed, and install whatever is missing with Ada's step-by-step help."
prerequisites: ["1.1"]
success_criteria:
  - "node -v prints a version 18.18 or newer, npm -v prints a version, and git --version prints a version; anything missing has been installed."
badge: null
---

## Learn

Before we build, let's make sure your computer has two small helpers. You won't use them directly — they just work quietly in the background — but the app-building tools depend on them, so we check now to avoid surprises later. Good news up front: both are **free**, and there's a decent chance they're already installed.

- **Node.js** — the *engine* that runs the tools we use to build your app. When you install Node.js, you also get **npm**, its helper for downloading the free building blocks (called *packages*) that the app needs. Think of Node.js as the motor and npm as the parts delivery.
- **Git** — a tool that quietly saves *versions* of your files as you go, like an unlimited undo history for your whole project. Later it's also how your code travels to GitHub.

We don't need to understand how they work — we just need them present and recent enough. Node.js updates often, so we want version **18.18 or newer**. I'll check all of this for you; nothing here can harm your computer. And if anything's missing, no problem — I've got a step-by-step **Mac install guide** and I'll walk you through it.

## Practice

**First, a quick choice — how would you like to work through the hands-on steps?** (This is the first time we run commands, so it's a good moment to pick. You can switch anytime.)

- **🤝 Auto — "do it with me":** I run each command for you, showing it first and asking your OK each time. You only step in for the few things I *can't* do — typing your Mac password, clicking an install pop-up, or anything in a web browser.
- **🧑‍💻 DIY — "I'll drive":** I explain each step and give you the exact command; you run it; I check the result.

Tell me which you'd like (or say "you decide"), and I'll remember it for the rest of the course.

**Now, let me check what you already have.** Either way, I run these three checks and read the results to you:

1. `node -v` — shows your Node.js version (we want 18.18 or higher).
2. `npm -v` — shows npm's version (any version is fine).
3. `git --version` — shows your Git version (any version is fine).

If everything prints a version and Node.js is 18.18+, you're done — just say `/check`. 🎉

**If something's missing or too old, I'll guide you through installing it — free.** The one rule that never changes: installing needs your **Mac password** or a **click**, which only you can do. So:

- **In Auto mode**, the smoothest route is **Homebrew** (one tool that installs everything): you paste the Homebrew install command into your Terminal and type your password *once*, and after that I can run `brew install node gh git` for you (with your OK each time). Steps are in **`reference/installing-on-mac.md`**.
- **In DIY mode** (or if you'd rather not use Homebrew), use the simple installers: **Node.js** from **nodejs.org** (click **LTS**, open the `.pkg`, click through), and **Git** via `xcode-select --install` (click **Install** on the pop-up).

After you install, tell me and I'll re-run the three checks. If a tool *still* isn't found right after installing, the fix is usually to **fully quit and reopen Claude Code** so it notices the new tool — I'll let you know if that's needed.

## Check

To pass, all three commands must succeed **and** Node.js must be 18.18 or newer.

- I verify by running `node -v`, `npm -v`, and `git --version` and reading the output. Pass = three real version numbers, with `node -v` at 18.18 or above.
- **Common mistake 1 — Node.js too old:** if `node -v` shows something like v16 or v14, we install the current LTS from nodejs.org (the `.pkg` installer), then I re-check. If you already had an old Node, you may need to **quit and reopen Claude Code** so the new version is picked up — I'll flag it.
- **Common mistake 2 — "command not found":** that means the tool isn't installed yet (or the window was opened before installing). For Git on a Mac that's `xcode-select --install`; for Node it's the nodejs.org installer. After installing, if it's still "not found," quit and reopen Claude Code, then I re-check. Full steps live in `reference/installing-on-mac.md`.
- I'll always confirm by re-running the checks myself — your word that "it installed" isn't enough; I want to see the version print.

## Challenge

Optional and curiosity-driven: ask me to also run `npx --version`. `npx` comes bundled with npm and is the little helper we'll use in Module 4 to create your app in one command. Seeing it respond now means your toolbox is truly complete.

## Hints

- You don't need to run the checks yourself — just ask me to check your tools, and I'll run the three commands and tell you what I find.
- If I report something is missing, don't worry — it's a normal, free download, and I have a Mac guide (`reference/installing-on-mac.md`). Just say "help me install it" and I'll walk you through each step.
- Missing Node.js? Go to **nodejs.org**, click the **LTS** button, open the `.pkg` file it downloads, click through (enter your Mac password when asked), then tell me it's done — I'll re-check. Missing Git? Run `xcode-select --install` in the Terminal and click **Install**. Still "not found" after installing? Quit and reopen Claude Code, then I'll re-check.
