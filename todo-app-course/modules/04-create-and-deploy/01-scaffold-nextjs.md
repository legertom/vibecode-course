---
id: "4.1"
module: 4
lesson: 1
title: "Scaffold a Next.js app with Claude Code"
estimated_minutes: 7
objectives:
  - "Have a ready-to-run Next.js starter app created in the workspace/todo-app folder"
prerequisites: ["3.3"]
success_criteria:
  - "workspace/todo-app/package.json exists and lists \"next\" as a dependency"
  - "workspace/todo-app/app/page.js exists"
badge: null
---

## Learn

You could build a web app by typing hundreds of files from scratch. Or you could press a button
and get all of them at once, ready to run. We're pressing the button.

That button is a tool called **`create-next-app`** — a small program that builds a complete
**Next.js** starter app in seconds. (Next.js is a popular, free, open-source toolkit for making
websites and web apps.) It creates a folder full of starter files: the app's home page, its
styling, its settings — everything wired together and working, before you write a single line.

Ada runs this for you. In a moment you'll have a real app sitting in a folder called
`workspace/todo-app`, waiting for us to make it our own.

Money check: **this is $0.** Next.js and `create-next-app` are free and open-source. Running this
just creates files on your computer — nothing to install a subscription for, nothing that bills.

## Practice

Ask Ada to scaffold the app. Ada will run this command **from inside your `workspace` folder** so
the new app lands at `workspace/todo-app`:

```
npx create-next-app@latest todo-app --js --app --tailwind --eslint --no-src-dir --import-alias "@/*" --use-npm
```

What those options mean, in plain English: build the app in a folder named `todo-app`, use plain
JavaScript (not the more advanced TypeScript), use the modern "App Router" layout, include
Tailwind (a styling helper), and use `npm` to manage everything. You don't need to memorize any of
this — Ada handles it.

If the tool still stops to ask you a yes/no question, just accept the default answer it's already
showing (press Enter). The options above are chosen so it usually asks nothing at all.

When it finishes, you'll have a new folder, `workspace/todo-app`, full of starter files. That's the
whole task.

## Check

Ada confirms the starter app exists by checking for two files:

- `workspace/todo-app/package.json` exists, and reading it shows `"next"` listed as a dependency.
- `workspace/todo-app/app/page.js` exists (this is the app's home page — the file you'll edit most
  later).

**Pass:** both files are present and `package.json` mentions `next`. That means the scaffold
worked. Nice — the foundation of your app now exists.

**Common mistakes:**

- *Ran in the wrong folder.* If `todo-app` landed somewhere other than inside `workspace`, Ada can
  move it, or re-run the command from the `workspace` folder. Ada should double-check the current
  folder first.
- *`npm`/Node not installed.* If the command fails with something like "command not found" or
  "npx not recognized," Node.js may be missing. That's what Module 1 set up — pop back to lesson
  1.2 to install it, then try again.

## Challenge

Peek inside the new folder (ask Ada to list what's in `workspace/todo-app`). Can you spot the
`app` folder, the `package.json` file, and a file whose name ends in `globals.css`? Don't change
anything — just notice how much came for free. That's the head start `create-next-app` gave you.

## Hints

- You don't type anything yourself here — ask Ada to run the scaffold command, and make sure it's
  run from your `workspace` folder.
- The exact command is the `npx create-next-app@latest todo-app ...` line in Practice. If it pauses
  to ask a question, press Enter to accept the default.
- If it fails with "command not found," Node.js probably isn't installed yet — revisit lesson 1.2
  to set it up, then have Ada run the command again from `workspace`.
