# Troubleshooting — errors are normal, and every one has a fix

First, breathe. **Errors are a completely normal part of building** — every developer, on every
project, hits them constantly. An error is not you doing something wrong; it's just the computer
telling us what it needs. Ada reads these calmly and fixes them *with* you. Nothing here can break
your computer, and nothing here costs money to fix.

Each entry below is: **Symptom → Cause (plain English) → Fix.**

---

## "command not found" — node, git, or gh

**Symptom:** A command like `node -v`, `git --version`, or `gh --version` prints something like
`command not found` or `'npx' is not recognized`.

**Cause:** That tool isn't installed on your computer yet (or it's installed but your system can't
find it on its "PATH" — the list of places it looks for tools). Totally common on a fresh machine.

**Fix (all free; full Mac walkthrough in `reference/installing-on-mac.md`):**
- **Node.js missing:** at **nodejs.org**, click **LTS**, open the `.pkg`, and click through (enter
  your Mac password). Or, with Homebrew: `brew install node`.
- **Git missing:** in the Terminal run `xcode-select --install` and click **Install** on the pop-up
  (Apple's free tools include Git). Or `brew install git`.
- **GitHub CLI (`gh`) missing:** install the `macOS.pkg` from **cli.github.com**, or `brew install gh`.
- After installing, if it's **still** "command not found," **fully quit and reopen Claude Code** (a
  freshly installed tool is only seen by windows opened after it installed). Then Ada re-runs the
  check to confirm a version prints.

---

## Node.js is too old

**Symptom:** `node -v` prints a version like `v16.x` or `v14.x` — lower than **18.18**.

**Cause:** You have an older Node.js from a while back. The build tools need 18.18 or newer.

**Fix:** Install the current **LTS** from **nodejs.org** (the `.pkg` click-through installer). Then
**fully quit and reopen Claude Code** so the new version is the one in use — an old version lingering
in an open window is a common surprise. Ada re-runs `node -v` to confirm it now shows 18.18 or higher.

---

## GitHub CLI isn't authenticated (not logged in)

**Symptom:** `gh auth status` says you're **not logged in**, or a `git push` / `gh repo create` fails
with an "authentication" or "permission" message.

**Cause:** Your computer isn't logged in to GitHub yet, or a previous login didn't finish (the browser
tab was closed, or the one-time code was entered too late — codes expire quickly).

**Fix:** Run `gh auth login` again and complete the browser step, keeping the terminal and browser
side by side. Choose **GitHub.com → HTTPS → Login with a web browser**, then enter the one-time code
and click **authorize**. Then `gh auth status` should say **Logged in to github.com**. This is a
quick, free fix — no harm done.

Also worth a quick check: `git config --global user.name` and `git config --global user.email` should
each print a value. If either is blank, re-run (keep the quotes):
`git config --global user.name "Your Name"` and `git config --global user.email "you@example.com"`.

---

## Port 3000 is already in use

**Symptom:** After `npm run dev`, the app doesn't appear at `http://localhost:3000`, or the terminal
mentions port 3000 is busy and shows a different address like `http://localhost:3001`.

**Cause:** Another program (often an earlier dev server you didn't stop) is already using port 3000.
Next.js politely moves to the next free port instead.

**Fix:** Use whatever address Next.js prints — if it says `3001`, open `http://localhost:3001` in your
browser, and Ada will `curl` that same port to confirm a **200**. (Alternatively, Ada can stop the old
dev server that's holding port 3000, then restart.) Either way, no cost and no drama.

---

## "localStorage is not defined"

**Symptom:** The app crashes or shows an error mentioning **"localStorage is not defined"**, often
right when the page loads.

**Cause:** In Next.js, your page is first prepared on a **server** — a computer that has *no browser* —
before it's handed to your browser. On that server, `localStorage` simply doesn't exist. So if the code
tries to touch `localStorage` while the page is first being built (during the initial render), it
crashes.

**Fix:** `localStorage` must only be touched **inside a `useEffect`**, never in the main render body.
The safe pattern:
- **Load** saved tasks with `localStorage.getItem(...)` inside a `useEffect` that runs **once on mount**
  (after the page appears in the browser).
- **Save** with `localStorage.setItem(...)` inside a `useEffect` that runs **whenever the tasks change**.

Ask Ada: "make sure localStorage is only read inside useEffect, never during render." Ada moves the
read into a mount `useEffect` and re-tests the refresh. Related slip: if tasks *vanish* after a refresh,
the empty starting list may be saving *before* the first load runs — a small "have we loaded yet?" guard
fixes it.

---

## My repo didn't show up in Vercel

**Symptom:** When you start a "New Project" import in Vercel, your `todo-app` repository isn't in the
list.

**Cause:** Vercel isn't connected to the right GitHub account, or it was only granted access to *some*
repositories and yours wasn't included.

**Fix:**
- Make sure Vercel is authorized to the **same GitHub account** you set up in Module 2 (the one your
  repo lives under). If it's connected to a different login, disconnect and reconnect the correct one
  in Vercel's Git/connections settings.
- If you chose "only select repositories" when authorizing, switch to **All repositories** (recommended)
  or add `todo-app` specifically. You can change this in GitHub → **Settings → Applications** → the
  Vercel GitHub app.
- Double-check the repo actually exists: `gh repo view` should show it. If you named it something other
  than `todo-app` (e.g. `todo-app-clever`), look for that name in Vercel's list.

This is all free to fix — it's just a permissions handshake between two free accounts.

---

## Deployment still building / I see a stale (old) version

**Symptom:** You pushed a change but the live site still shows the old version — or Vercel shows a
"building" / "please wait" screen.

**Cause:** Two possibilities. (1) The deploy simply isn't finished — very first builds can take a
minute or two. (2) Your browser is showing a **cached** (saved) copy of the old page.

**Fix:**
- **Give it a moment.** Wait about a minute for Vercel to finish, then reload.
- **Do a hard refresh** to bypass the cache (fully reload the page). On a phone, pull down to reload.
- **Trust the `curl` check.** Ada's `curl -sI <your-url>` (status) and `curl -s <your-url>` (the HTML)
  bypass your browser's cache, so they're the source of truth for what's *actually* live. When your new
  text shows up there, it's really deployed. Every one of these redeploys is included free in your Vercel
  Hobby plan.

---

## I used a personal email for Vercel instead of my Clever work email

**Symptom:** Your Vercel account email doesn't end in `clever.com` — you signed up with a personal
address by mistake.

**Cause:** For the Vercel (work) account, we want your Clever work email. (This is different from
GitHub, where a personal email was perfectly fine.)

**Fix:** Ada will help you sign out and sign up again using your `clever.com` address (or, if Vercel
allows it, add/switch the email in your account settings). Reassurance: using a work email does **not**
cost money — you're still on the free **Hobby** plan, and there's no card on file.

*(Related:* if you ever land on a paid or "Pro" plan by accident, no harm done — Ada helps you switch
back to the free **Hobby** plan in your account/billing settings. You won't be charged.)*

---

## I pasted the wrong URL

**Symptom:** Ada's `curl` check on your "live URL" doesn't return a **200** (or returns an error),
even though your app is deployed.

**Cause:** The address pasted was mistyped, was an old link, or was the Vercel **dashboard/settings**
page instead of the actual live app URL.

**Fix:** Copy the **live app URL that ends in `.vercel.app`** — not the dashboard address. Grab it from
your Vercel project page or from your browser's address bar while viewing the live app. Paste that exact
link to Ada, and she'll `curl -sI` it again to confirm a **200**. Your app *is* deployed — this is just
about pointing at the right address.

---

## Still stuck? That's okay too.

If none of these match, just tell Ada exactly what you did and what you saw (the error text, if there
is one, is gold). Ada will read it, explain it in plain words, and walk you through the fix. You truly
cannot break anything permanently here — and every error you clear is you getting a little more fluent.
You've got this.
