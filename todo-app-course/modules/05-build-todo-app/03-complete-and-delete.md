---
id: "5.3"
module: 5
lesson: 3
title: "Add complete + delete: check off and remove tasks"
estimated_minutes: 10
objectives:
  - "Direct Claude Code to add mark-complete and delete features, and confirm the app still runs locally."
prerequisites: ["5.2"]
success_criteria:
  - "workspace/todo-app/app/page.js has a toggle-complete handler (a checkbox that strikes the task through) and a delete handler that removes a task; the dev server still responds 200."
badge: null
---

## Learn

Your app can add and list tasks — that's a real win. Now we'll grow it, and this is how apps
*always* grow: **one small change at a time.** We won't rewrite everything; we'll ask Claude Code
to add just two things on top of what's already working.

The two things:

1. **Mark a task complete.** We'll add a little checkbox next to each task. Checking it marks the
   task "done" and shows it with a line through the text (struck through), so finished tasks look
   clearly finished. Unchecking it brings it back.
2. **Delete a task.** A small delete button next to each task removes just that one.

There's one quiet detail that makes delete reliable, and it's worth knowing so you can ask for it:
each task needs a **stable id** — a permanent little label — so "delete this one" removes the
*right* one and never the wrong one. If tasks are deleted by their position in the list instead,
things can go sideways when the list changes. You don't have to implement this — just include "give
each task a unique id" in your request and I'll make sure it's handled.

## Practice

Direct Claude Code to add both features. Keep it plain and specific — remember: what you want to
*see* and what happens when you *interact*.

A good ask:

> "In `workspace/todo-app/app/page.js`, add two things to my to-do app. First, a checkbox next to
> each task — checking it marks the task done and shows the text with a line through it. Second, a
> Delete button next to each task that removes just that task. Give each task a unique id so delete
> always removes the right one."

I'll update `workspace/todo-app/app/page.js` and start the app so you can try it: add a couple of
tasks, check one off (line through it), and delete another. When it behaves the way you expect, say
you're done or run `/check`.

## Check

What I'll verify:

1. **I'll read `workspace/todo-app/app/page.js`** and confirm:
   - A **toggle-complete handler** exists — a checkbox that flips a task's done state, and the
     completed task is shown struck through (look for a line-through / strikethrough style).
   - A **delete handler** exists that removes a single task (typically by filtering out its id).
   - Tasks carry a stable **id** used as the list key and for delete.
2. **I'll run the app** and confirm `http://localhost:3000` still returns **200**, then try checking
   and deleting to see it work. I'll stop the server afterward.

**Pass looks like:** you check a task and it gets a line through it; you click Delete on a task and
only that one disappears; everything else stays.

**Common slips I'll catch and fix with you:**
- **Delete removes the wrong task** — a sign tasks are identified by position, not a stable id.
  I'll switch it to delete by id.
- **Checking a box doesn't visibly change anything** — usually the state wasn't updated as a *new*
  list, so the screen didn't refresh. I'll fix the update so the strikethrough appears immediately.

## Challenge

Ask me to show a small count like "2 of 5 done" somewhere on the page, updating as you check tasks
off. It's a nice sense of progress. Totally optional — it won't affect your pass.

## Hints

- You're adding to what already works — ask for just the two new things, not a rebuild.
- Name them precisely: a checkbox that marks done and strikes the text through, and a per-task
  Delete button that removes only that task.
- Add "give each task a unique id so delete removes the right one" to your request — that single
  phrase prevents the most common bug here.
