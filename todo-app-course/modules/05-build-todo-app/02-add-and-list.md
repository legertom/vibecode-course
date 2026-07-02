---
id: "5.2"
module: 5
lesson: 2
title: "Build add + list: type a task, see it appear"
estimated_minutes: 10
objectives:
  - "Direct Claude Code to build an add-and-list to-do page, and confirm it works locally."
prerequisites: ["5.1"]
success_criteria:
  - "workspace/todo-app/app/page.js starts with the \"use client\" directive, uses useState for the todo list, has an add handler wired to a button/input, and renders the list; the dev server serves it (HTTP 200) and adding a task shows it in the list."
badge: null
---

## Learn

Now we build the first real feature — and here's the surprising part: **you won't write the code.
You'll describe what you want, and Claude Code writes it.** That's the whole skill of this module,
so let's learn to ask well.

A clear request to Claude Code says two things in plain words: **what you want to *see*** and
**what you want to *do*.** Vague ("make a to-do app") gives fuzzy results. Specific gives good
ones. For example:

> "In `workspace/todo-app/app/page.js`, make a to-do app. There should be a text box and an Add
> button. When I type a task and click Add, the task appears in a list below. Keep it in
> JavaScript."

That's it — plain English, but concrete about what shows up on screen and what happens when you
click.

One technical must-know so nothing breaks: our page needs to *react* to what you type and click.
For that, the very first line of `page.js` must be the words `"use client"` (with the quotes).
That tiny line tells Next.js "this page runs interactive code in the browser." Without it, the
interactive bits won't work and the app can error. Don't worry about typing it — just know it
belongs there, and I'll make sure it's present when I check.

## Practice

Time to direct Claude Code. In your own words, ask me to build the add-and-list feature. Aim for a
request that names **where** (the page file), **what you see** (a box + Add button + a list), and
**what happens** (typing and clicking Add adds it to the list).

A good ask sounds like:

> "In `workspace/todo-app/app/page.js`, build a to-do app in JavaScript: a text box, an Add button,
> and a list underneath. When I type a task and click Add, it shows up in the list. Ignore empty
> tasks. Put `"use client"` at the top."

I'll then update `workspace/todo-app/app/page.js` for you and start the app locally so you can try
it. Type a task, click Add, and watch it appear. When it works for you, say you're done or run
`/check`.

## Check

Here's what I'll verify:

1. **I'll read `workspace/todo-app/app/page.js`** and confirm four things:
   - The first line is `"use client"`.
   - It uses React's `useState` to hold the list of tasks.
   - There's an add handler wired to the Add button / input (typing + clicking adds a task).
   - The list is rendered on screen (usually a `.map` over the tasks).
2. **I'll run the app** in the background and check `http://localhost:3000` returns **200** (that
   means the page loaded without errors). Then I'll confirm adding a task shows it in the list.
   I'll stop the server when we're done so nothing lingers.

**Pass looks like:** the page loads, you type "Buy milk", click Add, and "Buy milk" appears below.

**Common slips I'll catch and fix with you:**
- **Missing `"use client"`** — the app errors or the buttons don't respond. I'll add that top line.
- **Empty tasks get added** (clicking Add with an empty box makes a blank row). I'll have the code
  ignore blank/whitespace-only entries.
- The app won't start — usually a small code hiccup; I'll read the error and fix it. Errors are
  normal, we just tidy them up.

## Challenge

Ask me to also add the task when you press **Enter** in the text box (not only when you click Add).
It's a small, satisfying touch that makes the app feel natural to use. Optional — skip it freely.

## Hints

- Describe two things: what you want to *see* (box, Add button, list) and what happens when you
  *click Add* (the task joins the list). Name the file: `workspace/todo-app/app/page.js`.
- Add "ignore empty tasks" and "put `"use client"` at the top" to your request so the common
  mistakes are handled from the start.
- If you're stuck on wording, paste this to me: "In `workspace/todo-app/app/page.js`, build a
  JavaScript to-do app with a text box, an Add button, and a list below; typing a task and clicking
  Add adds it; ignore empty tasks; `"use client"` at the top." I'll build it and run it for you.
