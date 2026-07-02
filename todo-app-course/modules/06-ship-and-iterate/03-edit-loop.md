---
id: "6.3"
module: 6
lesson: 3
title: "One small change → push → live (the loop)"
estimated_minutes: 8
objectives:
  - "Make one small, visible edit to the app, push it, and watch it appear on the live URL automatically — feeling the full edit → push → deploy loop end to end."
prerequisites: ["6.2"]
success_criteria:
  - "The new text appears in workspace/todo-app/app/page.js."
  - "After the redeploy finishes, the live URL responds HTTP 200 and its HTML contains that same new text."
badge: null
---

## Learn

This is the loop that runs under every website you've ever used: someone **edits** the code,
**pushes** it, and it goes **live** — automatically. You've done each piece already. Now let's
feel the whole thing in one smooth motion, with a change you can actually see.

The idea: change one small, visible thing (like the app's heading), send it up, wait a moment,
and watch it appear on your real web address — no clicking "publish" anywhere. Once you've felt
this once, you'll never be intimidated by "shipping" again. It's just edit, push, done.

And yes — still $0. Every one of these updates is included in your free Vercel Hobby plan.

## Practice

Let's make it personal. Pick a small, visible change to your app's **heading** — for example,
change it from "My To-Do List" to **"Alex's To-Do List"** (use your own name), or add a little
tagline like "Get it done ✨".

1. Tell Ada the exact new heading you want. Ada will make that one edit in
   `workspace/todo-app/app/page.js` for you.
2. Ada then saves and ships it, from `workspace/todo-app`:

   ```bash
   git add -A && git commit -m "Personalize the heading" && git push
   ```
3. Wait about a minute for Vercel to finish redeploying. Then reload your live URL and look for
   your new heading.

That's the loop: **edit → push → live.** Tell Ada once you see (or don't see) your new heading
on the live site.

## Check

Say `/check` when you've pushed your change.

**Pass looks like:**
- Ada reads `workspace/todo-app/app/page.js` and finds your new heading text in it.
- Ada fetches your live URL, confirms **HTTP 200**, and finds that same new text in the
  returned HTML. If the deploy is still finishing, Ada waits a few seconds and checks again —
  a couple of retries is normal.

Seeing your own words show up on a live web address that anyone can visit? That's the whole
loop working end to end. That's shipping.

**Common mistakes Ada will gently help with:**
- *"I don't see the change yet."* — you probably checked before Vercel finished the redeploy.
  Wait about a minute and reload; Ada will re-fetch the URL too.
- *"Still the old heading after waiting."* — your browser may be showing a cached copy. Do a
  hard refresh (fully reload). Ada's `curl` check bypasses the cache, so it's the source of
  truth for what's actually live.
- *Forgot to push* — the edit is on your computer but not sent up. Ada will confirm `git
  status` is clean and pushed.

## Challenge

Make a second tiny change — maybe tweak the wording of the "add" button or your tagline — and
run the loop again yourself, narrating each step to Ada: "editing… committing… pushing…
waiting… there it is!" The more times you feel it, the more it becomes muscle memory.

## Hints

- The goal is to see one change you make travel all the way to your live site on its own. Start
  by deciding the exact new heading text you want.
- Tell Ada the new text; Ada edits `workspace/todo-app/app/page.js`, then runs `git add -A &&
  git commit -m "..." && git push`. After that, Vercel redeploys by itself.
- If your new heading isn't live yet, you likely looked too soon or saw a cached page. Wait
  about a minute, do a hard refresh, and have Ada re-check the URL — the change is confirmed
  once that new text shows up in the live page's HTML.
