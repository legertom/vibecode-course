---
id: "5.5"
module: 5
lesson: 5
title: "Style & polish: make it look intentional"
estimated_minutes: 9
objectives:
  - "Direct Claude Code to style the app with Tailwind CSS into a clean, centered layout, and confirm it still runs locally."
prerequisites: ["5.4"]
success_criteria:
  - "workspace/todo-app/app/page.js uses Tailwind utility classes for a clearly styled, centered layout (a heading, styled input/buttons, and clear completed-task styling) and the dev server responds 200."
badge: "app-builder"
---

## Learn

Your app *works* — add, complete, delete, and it remembers. Now let's make it *look* like you
meant it. A few small styling touches turn "a working prototype" into "something I'm proud to
share," and they don't change any behavior — just the look.

We'll style with **Tailwind CSS** — a way of styling by adding short, readable labels (called
*classes*) right onto elements, like `text-center` to center text or `rounded` for rounded
corners. The good news: **Tailwind is already set up** in your project from when we scaffolded it,
so there's nothing to install and nothing to pay for — styling is free too. You just describe the
look you want, and Claude Code adds the right classes in `workspace/todo-app/app/page.js`.

A friendly, tidy to-do app usually has:

- A **centered card** with comfortable spacing (not stretched edge-to-edge).
- A clear **heading** at the top, like "My To-Do List."
- A **styled input and buttons** that look clickable.
- **Completed tasks** that read as done — the strikethrough plus a softer, greyed color.

That's plenty. Clean beats fancy.

## Practice

Ask Claude Code to style the app. Describe the *feel* you want in plain words — you don't need to
know any class names:

> "In `workspace/todo-app/app/page.js`, style my to-do app with Tailwind so it looks clean and
> friendly: center everything in a card with nice spacing, add a clear heading at the top, make the
> input and buttons look tidy and clickable, and make completed tasks look done (greyed out with the
> line through them)."

I'll update `workspace/todo-app/app/page.js` and run the app so you can look. This one's about
*your* taste — if something feels off (too big, wrong color, cramped), just tell me and I'll adjust.
When you like how it looks, say you're done or run `/check`.

## Check

What I'll verify:

1. **I'll read `workspace/todo-app/app/page.js`** and confirm real styling is in place:
   - A **heading** for the app.
   - Meaningful Tailwind `className` styling for a **centered layout** (e.g. centering + a
     max-width/card + padding), plus styled **input and buttons**.
   - **Completed-task styling** that clearly reads as done (strikethrough and a muted/greyed color).
2. **I'll run the app** and confirm `http://localhost:3000` returns **200** — styling shouldn't
   break anything. Then I'll ask you the most important question: **do you like how it looks?**
   I'll stop the server afterward.

**Pass looks like:** a centered, titled to-do app with tidy inputs and buttons, where finished
tasks look visibly finished — and it still works exactly as before.

**Common slips I'll catch and fix with you:**
- **Styling but the app broke** (blank page or error) — a class was added in the wrong spot. I'll
  read the error and fix it; your features stay intact.
- **It looks the same as before** — Tailwind classes may not be applying. I'll double-check the
  project's Tailwind setup and reapply the styling.

**Then we celebrate.** Passing this lesson earns your **`app-builder` badge** — your to-do app is
built: it adds, completes, deletes, remembers, and looks great, all for **$0**. That's a real,
finished app that *you* directed into existence. Beautiful work.

## Challenge

Ask me to add one small delightful touch — your pick: a gentle hover effect on buttons, a friendly
empty-state message like "No tasks yet — add your first one!" when the list is empty, or a bit of
color on the heading. One tasteful detail is often what makes an app feel truly *yours*. Optional,
and it won't affect your badge.

## Hints

- Describe the *feel*, not class names: centered, a heading, tidy input and buttons, completed
  tasks that look done.
- Remind me completed tasks should be both **struck through** and **greyed/muted** so "done" reads
  at a glance.
- Paste this if you'd like: "In `workspace/todo-app/app/page.js`, use Tailwind to center the app in
  a card with spacing, add a heading, style the input and buttons, and grey out completed tasks with
  a line through them." Then tell me any tweak and I'll adjust until you love it.
