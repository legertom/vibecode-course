---
id: "2.3"
module: 2
lesson: 3
title: "Connect your computer to GitHub"
estimated_minutes: 10
objectives:
  - "Log your computer in to GitHub with the GitHub CLI (gh auth login), and set your Git name and email so your saved work is labeled as yours."
prerequisites: ["2.2"]
success_criteria:
  - "gh auth status reports the learner is logged in to github.com, and both git config --global user.name and git config --global user.email return a non-empty value."
badge: "github-ready"
---

## Learn

You have a GitHub account on the web. Your computer, though, hasn't been introduced to it yet —
so right now your laptop can't send code up to GitHub. Let's make that introduction.

The easiest way for a beginner is a small helper tool called the **GitHub CLI** — its command
is `gh`. ("CLI" just means a tool you type commands to, in the terminal.) The nice part: `gh`
handles the login for you through your web browser. You click "approve," and it quietly sets up
the secure connection behind the scenes — no fiddly passwords or long secret codes to copy by hand.

There's one more small thing to set: your **name and email for Git**. Git is the tool that
records each saved version of your work, and it likes to stamp every save with *who* made it.
Setting this once means all your future saves are correctly labeled as yours. (This email is
just a label on your saves — it doesn't have to match your GitHub sign-up email, though it's
fine if it does.)

So this lesson has three quick steps: make sure `gh` is installed, log in with it, and set your
name and email. Ada can run the checks with you.

## Practice

**Step (a) — Make sure the GitHub CLI is installed.** In the terminal, check for it:

```
gh --version
```

If you see a version number, great — skip to step (b). If it says something like
"command not found," install it (free). On a Mac, the simplest way needs no extra tools:

- **Easiest (official installer):** go to **cli.github.com**, download the macOS installer (the
  file ending in `macOS.pkg`), open it, and click through — enter your Mac password when asked.
- **If you set up Homebrew:** `brew install gh` installs it in one command.
- Full step-by-step (including Homebrew) is in **`reference/installing-on-mac.md`**.

Then run `gh --version` again to confirm it's there. (If it still says "not found" right after
installing, quit and reopen Claude Code so it notices the new tool, then check again.)

**Step (b) — Log your computer in to GitHub.** Run:

```
gh auth login
```

It will ask you a few questions. Choose these answers (use the arrow keys and Enter):

1. Where do you use GitHub? → **GitHub.com**
2. Preferred protocol? → **HTTPS**
3. Authenticate how? → **Login with a web browser**

It will show you a short **one-time code** and open your browser. Type (or paste) that code into
the GitHub page, then click the button to **authorize**. When it says you're all set, return to
the terminal — it will confirm you're logged in.

**Step (c) — Set your name and email for Git.** Replace the example text with your own:

```
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
```

(Keep the quotation marks. The `--global` part means "use this for all my projects," so you only
do it once.)

When all three steps are done, run `/check`.

## Check

Ada verifies the connection and identity by running:

```
gh auth status
git config --global user.name
git config --global user.email
```

- **PASS** — `gh auth status` reports **Logged in to github.com** (as the learner's account), and
  **both** `git config` commands print a non-empty value (a name and an email). When all three are
  good, award the **github-ready** badge and celebrate — their computer can now talk to GitHub!

Common mistakes to check kindly:

- **`gh: command not found`** — the CLI isn't installed yet (or Claude Code was open before it
  was installed). Walk them through step (a) — the `macOS.pkg` installer from **cli.github.com**
  (or `brew install gh` if they have Homebrew) — and if it's still not found right after, have
  them quit and reopen Claude Code, then retry. Details in `reference/installing-on-mac.md`.
- **Login didn't finish** — if `gh auth status` says "not logged in," the browser tab was likely
  closed or the code entered too late (codes expire). Reassure them this is common: just run
  `gh auth login` again and complete the browser step, keeping the terminal and browser side by side.
- **Name or email is blank** — if either `git config` command prints nothing, that step was
  skipped or the quotes were dropped. Have them re-run step (c) exactly, keeping the quotation marks.

## Challenge

Optional: prove the whole introduction worked by asking GitHub who you are, straight from the
terminal:

```
gh api user --jq .login
```

If it prints your GitHub username, your computer and GitHub are officially on speaking terms.
Nice work.

## Hints

- Start by checking whether the tool exists: `gh --version`. If it's missing on a Mac, install it
  from **cli.github.com** (the `macOS.pkg` file) — or `brew install gh` if you have Homebrew.
- The login command is `gh auth login` — when it asks, choose **GitHub.com**, then **HTTPS**,
  then **Login with a web browser**, and enter the one-time code it shows you.
- To label your saves, run these two once (keep the quotes):
  `git config --global user.name "Your Name"` and
  `git config --global user.email "you@example.com"`. Then `gh auth status` should say you're
  logged in.
