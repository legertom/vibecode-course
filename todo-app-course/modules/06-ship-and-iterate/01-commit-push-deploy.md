---
id: "6.1"
module: 6
lesson: 1
title: "Commit & push — and watch your app go live"
estimated_minutes: 8
objectives:
  - "Save a labeled snapshot of the to-do app, send it to GitHub, and have Vercel put the real app live at your web address."
prerequisites: ["5.5"]
success_criteria:
  - "The latest commit is pushed: `git status` in workspace/todo-app shows the branch up to date with origin."
  - "The live URL responds HTTP 200 and its HTML now contains the real to-do app (e.g. the app's heading text), not the default Next.js starter page."
badge: null
---

## Learn

Your to-do app is finished and working on your computer. But the version living on the
internet is still the plain starter page from Module 4. Let's fix that — and this is where
three words start to feel like second nature.

- **Commit** = save a labeled snapshot of your work. Like taking a photo of your project
  right now and writing a caption on the back ("Build the to-do app"). Your earlier snapshots
  are never lost, so you can always look back.
- **Push** = send those snapshots up to GitHub, your code's free online home.
- **Deploy** = Vercel notices the new code on GitHub and automatically rebuilds your live
  site. You don't click anything — it just happens.

So the whole trip is: **commit → push → Vercel deploys, on its own.** That last part is the
magic. Once it's set up (and you did that in Module 4), sending your app live is as simple as
pushing your code. No servers, no bills — your free Vercel Hobby plan handles it.

## Practice

Time to send the real app live. Ada will run these for you, from inside the
`workspace/todo-app` folder:

```bash
git add -A && git commit -m "Build the to-do app" && git push
```

In plain English:
1. `git add -A` — gather up everything you changed.
2. `git commit -m "Build the to-do app"` — save the snapshot with that caption.
3. `git push` — send it to GitHub.

Then, in your browser, open your **Vercel dashboard** and look at your project. Within a
minute or so you should see a **new deployment appear** (a fresh entry, usually showing it
building and then finishing). That's Vercel automatically rebuilding your live site from the
code you just pushed. Tell Ada when you see it.

## Check

Say `/check` when you're ready. Here's what Ada confirms:

**Pass looks like:**
- Ada runs `git status` in `workspace/todo-app` and sees something like *"nothing to commit,
  working tree clean"* and *"Your branch is up to date with 'origin/…'."* That means your
  snapshot was saved and pushed.
- Ada fetches your live URL (`curl -sI <your-url>` for the status, and the page's HTML) and
  finds **HTTP 200** *and* your app's real heading text in the page — proof the live site is
  now the actual to-do app, not the old starter page.

**Common mistakes Ada will gently help with:**
- *"nothing to commit"* right away — your files may not have been saved in the editor, or the
  work was already committed. Ada will check what's actually changed.
- The push is **rejected** with an auth or permission message — this is a GitHub sign-in
  hiccup. Ada will re-check `gh auth status` and get you reconnected (no cost, quick fix).
- The live URL still shows the starter page — the deploy may still be finishing. Ada waits
  about a minute and checks again.

## Challenge

Ask Ada to show you your project's history with `git log --oneline`. Each line is one of your
saved snapshots, newest at the top. Can you spot the very first one from Module 4 and your new
"Build the to-do app" one? That whole list is your safety net — nothing you've done is lost.

## Hints

- Everything happens from your app's folder, `workspace/todo-app`. The trip has three steps:
  save a snapshot, then send it up. Vercel does the rest without you clicking anything.
- The three commands are `git add -A` (gather changes), `git commit -m "..."` (save a labeled
  snapshot), and `git push` (send to GitHub). Then watch the Vercel dashboard for a new
  deployment.
- Run them together: `git add -A && git commit -m "Build the to-do app" && git push`. If the
  push is rejected, it's a sign-in issue — ask Ada to check `gh auth status` and reconnect.
