---
id: "5.4"
module: 5
lesson: 4
title: "Save with localStorage: tasks that survive a refresh"
estimated_minutes: 10
objectives:
  - "Direct Claude Code to save and reload tasks with localStorage using the safe on-mount / on-change pattern, and confirm tasks survive a refresh."
prerequisites: ["5.3"]
success_criteria:
  - "workspace/todo-app/app/page.js still begins with the \"use client\" directive, reads localStorage with getItem inside a mount useEffect and writes with setItem inside a useEffect keyed on todos (never at top-level render), and todos survive a page refresh (dev server responds 200)."
badge: null
---

## Learn

Try this in your app right now: add a few tasks, then refresh the page. Poof — they're gone.
That's because, so far, the tasks only live in the page's short-term memory, which resets every
time the page reloads. Let's fix that so your list *sticks*.

We'll use **localStorage** — the browser's free, built-in mini-storage from our plan. It remembers
your tasks between visits, with **no database and no server**, so the app stays firmly **$0**.
This is exactly why we don't need anything that bills: the saving happens right in your own browser.

Now the one important detail — please don't skip this, it's the thing that trips everyone up.
In Next.js, your page is first prepared on a **server** (a computer that has *no browser*), and
only then handed to your browser. On that server, `localStorage` **does not exist**. So if the
code tries to touch `localStorage` while the page is first being built, the app crashes with an
error like *"localStorage is not defined."*

The safe pattern — the one to ask Claude Code for — has two rules:

1. **Load** saved tasks *after* the page has loaded in the browser: read `localStorage` inside a
   `useEffect` that runs once on mount (React's word for "after the page first appears").
2. **Save** whenever the tasks change: write to `localStorage` inside a `useEffect` that runs each
   time the task list changes.

Both use `localStorage` **only inside `useEffect`** — never in the main body of the page. Saving
and loading use `JSON.stringify` (to store the list) and `JSON.parse` (to read it back). You won't
type any of this; you just need to ask for the safe pattern, and I'll verify it's exactly right.

## Practice

Ask Claude Code to make your tasks survive a refresh — and specifically request the safe pattern so
we get it right the first time:

> "In `workspace/todo-app/app/page.js`, save my tasks in the browser's localStorage so they survive
> a page refresh. Load saved tasks inside a `useEffect` that runs on mount, and save them inside a
> `useEffect` that runs whenever the tasks change. Never read localStorage during the initial
> render — only inside useEffect — so it doesn't crash on the server."

I'll update `workspace/todo-app/app/page.js` and run the app. Then the real test: add a couple of
tasks and **refresh the page**. They should still be there. When they survive the refresh, say
you're done or run `/check`.

## Check

What I'll verify:

1. **I'll read `workspace/todo-app/app/page.js`** and confirm the safe pattern:
   - the file **still starts with `"use client"`** (this is what lets `useEffect` run in the
     browser instead of on the server — without it, the localStorage code can't run safely).
   - `localStorage.getItem(...)` is called **inside a `useEffect` that runs on mount** (loads saved
     tasks after the page appears).
   - `localStorage.setItem(...)` is called **inside a `useEffect` keyed on the tasks** (saves when
     they change).
   - `localStorage` is **not** referenced in the main render body — only inside `useEffect`.
2. **I'll run the app**, confirm `http://localhost:3000` returns **200**, and check that tasks
   persist across a reload. I'll stop the server afterward.

**Pass looks like:** you add tasks, refresh, and the exact same list is still there.

**Common slips I'll catch and fix with you:**
- **`localStorage` read during render** → the *"localStorage is not defined"* crash. I'll move that
  read into a mount `useEffect`.
- **Saving before the first load runs** → the empty starting list overwrites your saved tasks, so
  they vanish. I'll make sure loading happens first (a common fix is a small "have we loaded yet?"
  guard before the first save).
- Nothing persists at all — usually the save effect isn't watching the tasks. I'll wire it to run
  whenever the list changes.

## Challenge

With saving in place, ask me: "If I open the app in a different browser or on my phone, will my
tasks be there?" The honest answer is no — localStorage is *per browser, per device* (that's the
free trade-off from your plan). Try opening the live URL on your phone and adding a task there to
*see* that it keeps its own separate list. Nothing to submit — just a satisfying "aha."

## Hints

- The fix is localStorage, but the *how* matters: it must be touched only inside `useEffect`, never
  during the page's first render.
- Ask for two effects: one that **loads** saved tasks on mount, and one that **saves** whenever the
  task list changes.
- Paste this if you're stuck: "In `workspace/todo-app/app/page.js`, save tasks to localStorage —
  load them in a `useEffect` on mount, save them in a `useEffect` when tasks change, and never read
  localStorage during render so it won't crash on the server." I'll build it and test the refresh.
