---
id: "5.1"
module: 5
lesson: 1
title: "Plan it: the five features (and why it's free)"
estimated_minutes: 7
objectives:
  - "Write a short plan naming the five to-do features and noting that saving in the browser keeps the app free."
prerequisites: ["4.4"]
success_criteria:
  - "workspace/todo-app/PLAN.md exists and lists the five features (add, list, complete, delete, persist) and notes that localStorage keeps it free (no database)."
badge: null
---

## Learn

Before we build anything, let's do one small, calm thing: write down what we're building. Good
building starts with a tiny plan. It doesn't need to be fancy — a short list is enough to keep us
pointed in the right direction, so we're never guessing what to do next.

Here are the five features our to-do app will have:

1. **Add** a task — type it and it joins the list.
2. **List** — see all your tasks.
3. **Complete** — mark a task done (we'll show it with a line through it).
4. **Delete** — remove a task you don't want.
5. **Persist** (a fancy word for *save*) — your tasks stick around even after you refresh the page.

For that last one, we'll use something called **localStorage** — a small, free storage space
built right into your web browser. Think of it as a little notepad your browser keeps for our app.

Here's the money part, and it's good news: because we save into the browser, we need **no
database and no server** — which means there is **nothing that could ever bill you**. This whole
app stays **$0**. The one honest trade-off: localStorage saves tasks *per browser, per device*.
So your list on your laptop won't automatically appear on your phone. For a free personal to-do
app, that's a perfectly fair deal — and we'll note it right in our plan so we remember why.

## Practice

Let's write the plan. You don't need to know any code for this — it's just a short note to
ourselves.

Create a file called **`PLAN.md`** inside `workspace/todo-app/` that lists the five features and
adds one line about saving.

Tell me — in your own words is totally fine — the five features and one sentence on why saving in
the browser (localStorage) keeps this free. I'll create the `workspace/todo-app/PLAN.md` file for
you from what you say (or, if you'd like to type it yourself, I'll show you exactly what to put
in). Something like:

- Add a task
- See the list of tasks
- Mark a task complete
- Delete a task
- Save tasks so they survive a refresh (using the browser's localStorage — free, no database)

When the file's there, say you're done or run `/check`.

## Check

To pass, I'll open `workspace/todo-app/PLAN.md` and confirm two things:

1. **All five features are named:** add, list (see tasks), complete, delete, and persist (save/survive
   a refresh). The wording can be casual — "cross off a task" counts as complete.
2. **A localStorage / saving note is present** that ties saving to it being free or having no database.

**Pass looks like:** a short markdown list with those five ideas plus a line such as "saved in the
browser with localStorage — free, no database."

**Common slips I'll gently catch:**
- Only four features listed (people often forget **persist/save**) — I'll point out which one's missing.
- The file saved in the wrong place. It must be `workspace/todo-app/PLAN.md`, not the course root.
  I'll check the path and help move it.
- No mention of *why* it's free — add one short line about localStorage / no database and you're set.

## Challenge

Add a tiny "Nice to have (later)" line at the bottom of `PLAN.md` — one feature you'd love someday
(like sorting tasks or a dark mode). We won't build it now, but naming a dream is a great habit.
It won't affect your pass either way.

## Hints

- The plan is just a note to ourselves — no code. Five features plus one line about saving.
- The five are: add, list, complete, delete, and *save so it survives a refresh*. The last one is
  the one folks forget.
- Tell me these lines and I'll write the file: "Add a task / See the list / Mark complete / Delete a
  task / Save tasks with the browser's localStorage — free, no database." That's a passing `PLAN.md`.
