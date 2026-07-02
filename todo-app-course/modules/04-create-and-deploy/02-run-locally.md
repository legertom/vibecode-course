---
id: "4.2"
module: 4
lesson: 2
title: "Run your app locally and see it in the browser"
estimated_minutes: 7
objectives:
  - "Start the local dev server and view the Next.js starter page in your own browser"
prerequisites: ["4.1"]
success_criteria:
  - "the local dev server responds with HTTP 200 at http://localhost:3000"
  - "the learner confirms they see the Next.js starter page in their browser"
badge: null
---

## Learn

Before we show your app to the world, let's look at it privately — on your own computer, where only
you can see it. Developers call this running the app **locally** ("locally" just means: on your own
machine, not on the internet). It's a safe rehearsal space to preview changes before publishing.

To do this, we start something called the **dev server** ("dev" is short for development). It's a
small program that runs your app and hands it to your web browser at a special local address:
**http://localhost:3000**. That address only works on *your* computer — nobody else can reach it.
Think of it as a private preview window.

Money check: still **$0.** This all runs on your own machine. Nothing is published, nothing is
billed.

## Practice

1. Ask Ada to start the dev server. Ada runs, from inside `workspace/todo-app`, the command
   `npm run dev` (kept running in the background so you can keep working).
2. Ada checks the server is actually answering by running:
   ```
   curl -s -o /dev/null -w "%{http_code}" http://localhost:3000
   ```
   This quietly asks the local address for a page and prints only the response code. A **200**
   means "here's your page, all good."
3. Now it's your turn: open a web browser and go to **http://localhost:3000**. You should see the
   Next.js starter page — a clean welcome page with the Next.js logo and some links. Tell Ada what
   you see.
4. When you're done admiring it, ask Ada to stop the dev server so it's not left running.

## Check

Ada verifies the app is running locally:

- The `curl` command above prints **200** (any 2xx number is a healthy "OK").
- You confirm, in your own words, that you see the starter page in your browser. Ada may ask: "What
  do you see at localhost:3000?" A reasonable answer mentions the Next.js welcome page, its logo, or
  the links on it.

**Pass:** the curl returns 200 **and** you confirm the page shows up in your browser. That's your
app running for real — privately, on your computer.

**Common mistakes:**

- *Port 3000 is busy.* If something else is already using 3000, Next.js will start on a different
  number (like 3001) and print the address it chose. Use whatever address it prints — and have Ada
  curl that same port.
- *Nothing loads in the browser.* Make sure the dev server is still running (Ada can check) and that
  you typed the address exactly, including `http://`.
- *Command failed.* The `npm run dev` command must be run from inside the `workspace/todo-app`
  folder. If it errors, Ada should confirm it's in the right folder and that lesson 4.1 finished.

## Challenge

While the server is running, ask Ada to open `workspace/todo-app/app/page.js` and change a bit of
the visible text (for example, a heading). Save the file, then refresh http://localhost:3000 in
your browser. Watch it update almost instantly — that live-reload is one of the nicest parts of
working locally. (Feel free to change the text back afterward.)

## Hints

- Ask Ada to run the dev server for you; you just need to open the browser to the local address.
- The private preview address is **http://localhost:3000** — type it into your browser exactly,
  `http://` and all.
- If the page won't load, check that the server is still running and look at what Ada printed —
  Next.js tells you the exact address (and port) it's serving on; use that one.
