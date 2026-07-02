---
id: "4.4"
module: 4
lesson: 4
title: "Import into Vercel — your first LIVE URL"
estimated_minutes: 9
objectives:
  - "Import your GitHub repo into Vercel and deploy it to get a live, public web address"
prerequisites: ["4.3"]
success_criteria:
  - "a live Vercel URL for the app responds with HTTP 200 (any 2xx)"
badge: "first-live-url"
---

## Learn

This is the moment your app goes public. Your code is on GitHub; now we hand it to **Vercel**,
which builds it and puts it on the internet at a real web address — something like
`todo-app-yourname.vercel.app`. Anyone with that link can open it, including you on your phone.

We do this once by hand: import the repo and click deploy. After today, Vercel watches your GitHub
repo and re-publishes automatically every time you push a change (you'll feel that magic in Module
6). But first, the very first deploy.

Money check: **$0.** Vercel's Hobby plan is free, and this app never uses a database or any paid
service — so there's genuinely nothing to bill. Even though your Vercel account uses your Clever
**work** email, you're still on the free Hobby plan; a work email doesn't change that.

## Practice

This one happens in your browser, in the Vercel dashboard. Ada guides you step by step:

1. Open Vercel (vercel.com) and make sure you're signed in with your **Clever work email** account
   from Module 3.
2. Find the option to **add a new project** (usually an "Add New…" button, then "Project").
3. You'll see a list of your GitHub repositories. Find **`todo-app`** (or whatever name you used in
   lesson 4.3) and choose the option to **import** it.
4. Vercel automatically recognizes this is a Next.js app and fills in the right settings. **Leave
   everything as-is** — you don't need to change any setting or add anything.
5. Click the button that **deploys** it (labeled something like "Deploy"), then wait. Vercel builds
   your app; this usually takes under a minute or two.
6. When it's done, Vercel shows you a **live URL** ending in `.vercel.app`. Copy that address and
   **paste it to Ada.**

Then Ada verifies it's truly live (see Check).

## Check

Ada confirms your app is really on the internet:

- Ada runs `curl -sI <your-live-url>` (using the exact `.vercel.app` link you pasted) and looks for
  an **HTTP 200** — or any 2xx "OK" response. That means the live page answered successfully.

**Pass:** the live URL returns a 2xx. That's it — **your app is live on the internet, for free.**
This is a genuinely big deal: you went from nothing to a public web address. Take the win. You've
earned the **first-live-url** badge. 🎉

**Common mistakes:**

- *The repo didn't show up in Vercel's list.* Vercel may not be connected to your GitHub account
  yet — revisit lesson 3.3 to connect them, then come back and import.
- *Still building / a "please wait" screen.* Give it another moment. Very first builds can take a
  minute or two. Refresh, then grab the URL once it finishes.
- *Pasted the wrong link.* Make sure you copy the **live app URL** that ends in `.vercel.app` — not
  the Vercel dashboard/settings page address. If curl doesn't return a 2xx, double-check you sent
  the deployment link, not the dashboard link.

## Challenge

Open your new `.vercel.app` link on your **phone**. It works — the same app, on a different device,
anywhere. If you're up for it, send the link to a friend or coworker. That little starter page is
now something you built and shipped to the world.

## Hints

- The steps live in the Vercel dashboard: look for a way to add a new **Project**, then **import**
  your `todo-app` repo from GitHub.
- Don't touch the settings — Vercel detects Next.js on its own. Just find and click the **Deploy**
  button, wait for it to finish, and copy the `.vercel.app` link it gives you.
- Paste that exact `.vercel.app` link to Ada so Ada can `curl -sI` it and confirm a 200. If your
  repo isn't in the list, the GitHub↔Vercel connection from lesson 3.3 likely needs redoing.
