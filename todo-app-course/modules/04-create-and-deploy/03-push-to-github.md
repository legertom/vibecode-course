---
id: "4.3"
module: 4
lesson: 3
title: "Create the GitHub repo and push your code"
estimated_minutes: 8
objectives:
  - "Create a GitHub repository for the app and push the starter code to it"
prerequisites: ["4.2"]
success_criteria:
  - "git remote -v shows an \"origin\" pointing at the learner's GitHub todo-app repo"
  - "the repo exists on GitHub (gh repo view succeeds)"
badge: null
---

## Learn

Your starter app works on your computer. Now let's give it a home on **GitHub** — the online place
that stores your code, keeps a history of changes, and (importantly) is where Vercel will look to
find your app in the next lesson.

Two quick words:

- A **repository** (or "repo") is just a project folder that lives on GitHub.
- A **commit** is a saved snapshot of your code. Good news: `create-next-app` already made your
  first commit for you when it built the app. So there's nothing to save by hand — we just need to
  create the online repo and send your code up to it (that sending is called a **push**).

Money check: **$0.** GitHub is free, and a public repo like this costs nothing.

## Practice

Ask Ada to create the repo and push. Ada runs, from inside `workspace/todo-app`:

```
gh repo create todo-app --public --source=. --remote=origin --push
```

In plain English: "Make a new public GitHub repo named `todo-app`, connect it to this folder, call
that connection `origin`, and push my code up now." One command does all of it.

If Ada finds there's no saved snapshot yet (rare, since the scaffolder usually makes one), it will
first run:

```
git add -A && git commit -m "Initial commit"
```

...to save a snapshot, then run the `gh repo create` command above.

When it finishes, your starter code is on GitHub. That's the task.

## Check

Ada confirms two things:

- Running `git remote -v` (from `workspace/todo-app`) shows a connection named **origin** pointing
  at your GitHub `todo-app` repo (a URL with your username and `/todo-app`).
- Running `gh repo view` succeeds and shows the repo's details — proof it really exists on GitHub.

**Pass:** `origin` points at your repo **and** `gh repo view` shows it. Your code now lives safely
online. Ada can also share the repo's web link if you'd like to see it in your browser.

**Common mistakes:**

- *Not signed in to GitHub.* If you see an "authentication" or "not logged in" message, the GitHub
  connection from Module 2 needs redoing — revisit lesson 2.3 (`gh auth login`), then try again.
- *The name `todo-app` is already taken* on your account. Pick a different name (for example
  `todo-app-clever`) and have Ada run the command with that name instead. If you rename it, use the
  same name when you import it into Vercel next lesson.
- *Ran from the wrong folder.* The command must run from inside `workspace/todo-app`. Ada should
  confirm the folder before running.

## Challenge

Ask Ada for the repo's web address, then open it in your browser. Look around: you can see every
file the scaffolder created, and if you find the "commits" view, you'll see that "Initial commit"
snapshot. This is your code's history — every future change will show up here too.

## Hints

- You don't need to click around GitHub's website — Ada can create the repo and push with a single
  command from the `workspace/todo-app` folder.
- The command is `gh repo create todo-app --public --source=. --remote=origin --push`. Afterwards,
  `git remote -v` should show `origin` pointing at your repo.
- If it complains about authentication, your GitHub sign-in needs refreshing — go back to lesson
  2.3 and run `gh auth login`, then have Ada re-run the create command. If the name is taken, pick
  another name like `todo-app-clever`.
