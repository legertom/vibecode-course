---
id: "6.2"
module: 6
lesson: 2
title: "Verify your live app — on your computer and your phone"
estimated_minutes: 7
objectives:
  - "Confirm the live app really works out in the world: it loads, you can add a task, and the task survives a refresh — on both your computer and your phone."
prerequisites: ["6.1"]
success_criteria:
  - "The live URL responds HTTP 200 and its HTML contains the real to-do app."
  - "The learner confirms, in their own words, that on BOTH their computer and their phone they added a task and it was still there after refreshing that same device."
badge: null
---

## Learn

Your app is live. A `curl` check tells us the server is answering — but the real test is
using it the way anyone on the internet would: open the web address, add a task, refresh the
page, and see your task still sitting there.

Here's one honest, important thing about how your app saves tasks. It uses **localStorage** —
a little storage box built into each web browser, on each device. That's exactly what keeps
your app free (no database, nothing that bills). But it also means:

- Tasks you add **on your phone** live in your phone's browser.
- Tasks you add **on your laptop** live in your laptop's browser.
- They **don't sync between devices**. Your phone won't show the laptop's tasks, and that's
  completely normal and expected for a free app like this.

So each device keeps its own list. On any single device, though, your tasks should stick
around even after you close and reopen the page. Let's confirm that.

## Practice

Grab your live web address (the same one from the last lesson) and do this **twice** — once
on your computer, once on your phone:

1. Open the live URL in a browser.
2. Add a task (type something and add it).
3. **Refresh the page** (on a phone, pull down to reload; on a computer, reload the tab).
4. Confirm your task is **still there** after the refresh.

On your phone, the easiest way to open the address is to type it into your phone's browser, or
have Ada help you copy it somewhere you can tap it. Once you've checked both devices, tell Ada
what happened — for example: *"On my laptop I added 'buy milk', refreshed, still there. Same
on my phone with 'call mom'."*

## Check

Say `/check` when you've tried both devices.

**Pass looks like:**
- Ada fetches your live URL and confirms **HTTP 200** and that the real to-do app HTML is
  being served.
- You confirm in your own words that on **both** your computer and your phone, a task you
  added was still there after refreshing that device.

**Common mistakes Ada will gently clear up:**
- *"My phone doesn't show the tasks from my laptop!"* — that's expected, not a bug. Each
  device keeps its own list (that's the free, no-database design). Each device just needs to
  keep *its own* tasks after a refresh.
- *"After refresh my task vanished."* — you might be looking at an old, cached version of the
  page. Ada will have you do a hard refresh (fully reload) and try once more. If it still
  disappears, the saving code needs a look and Ada will help.
- *"The page won't load on my phone."* — double-check the address is typed exactly, including
  the part after the dots. Ada can re-confirm the URL responds.

## Challenge

Open your live URL on your computer, add a couple of tasks, then close the browser tab
completely and reopen the address. Still there? That's localStorage doing its job — your tasks
survive not just a refresh but closing the page entirely. Neat, and free.

## Hints

- The real test is using the app like a visitor would: open the address, add a task, reload,
  and see if it stuck. Do that on your computer and on your phone.
- If your phone doesn't show your laptop's tasks, that's expected — each device keeps its own
  list because the app saves in that browser (localStorage). Just confirm each device keeps
  *its own* task after a refresh.
- If a task disappears after reload, you're probably seeing a cached page. Do a full/hard
  refresh and try again, then tell Ada exactly what you added and what happened.
