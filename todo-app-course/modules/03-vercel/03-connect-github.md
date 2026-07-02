---
id: "3.3"
module: 3
lesson: 3
title: "Connect Vercel to your GitHub account"
estimated_minutes: 8
objectives:
  - "Authorize Vercel to access your GitHub so it can find and publish your repositories, confirmed by your GitHub repos being listable in Vercel"
prerequisites: ["3.2"]
success_criteria:
  - "Vercel is authorized to access the learner's GitHub — confirmed by GitHub showing as a connected Git provider and their repositories appearing when they start a new project import in Vercel"
badge: "vercel-ready"
---

## Learn

You've got two free accounts now: GitHub (where your code lives) and Vercel (which publishes it).
The last setup step is to introduce them to each other.

For Vercel to publish your app, it needs **permission to read your GitHub repositories**. (A
*repository*, or "repo," is just the labeled folder that holds one project's code on GitHub.)
Without that permission, Vercel simply can't see your code, so it has nothing to publish.

You'll grant that permission by connecting — "authorizing" — GitHub inside Vercel. Behind the
scenes this installs a small helper called the **Vercel GitHub app** on your GitHub account, which
is what lets Vercel notice your pushes and publish updates automatically later. It's a standard,
safe, one-time step, and — like everything here — **$0**.

One thing to be careful about: make sure you authorize the **same GitHub account** you set up in
Module 2 (the one with the email you used there). And when GitHub asks *which* repositories Vercel
may see, it's simplest to allow **all repositories**. You don't have any project repos yet, but the
one you create next module needs to be visible to Vercel — allowing all now saves a headache later.

## Practice

This is a browser step; Ada will guide you and help if a screen looks different (go by what each
button is *for*, since wording shifts over time).

1. In Vercel, look for the option to **connect** or **add** a Git provider — often on your
   dashboard as a prompt to import a project, or under **Account/Team Settings → Git / Connections**.
   Choose **GitHub**.
2. Vercel sends you to GitHub to confirm. If you're not already signed in to GitHub, sign in with
   the **same GitHub account from Module 2**.
3. GitHub will ask you to **authorize** and **install the Vercel GitHub app**. Approve it.
4. When GitHub asks which repositories Vercel may access, choose **All repositories** (recommended).
   If you'd rather limit it, at minimum make sure the project you'll create next module is included
   — but "All repositories" is the easy, safe choice here.
5. GitHub sends you back to Vercel, now connected.

**How to confirm it worked:** in Vercel, start to **add a new project** (look for a "New Project" or
"Import Git Repository" option). You don't have to finish creating anything — you're just checking
that Vercel can now **list your GitHub repositories**. If you see your GitHub repos (or a friendly
"you have no repositories yet, create one" message tied to your GitHub account), the connection is
live.

When you've checked, tell Ada what you saw — for example, "GitHub shows as connected in Vercel" or
"When I clicked to import a project, my GitHub account and its repos showed up."

## Check

Ada can't click through your browser, so Ada confirms this from what you describe. There are two
easy ways to prove the connection **right now**, without waiting for Module 4:
- **In Vercel:** start to add a new project — if your GitHub account and its (empty) repo list
  appear, you're connected.
- **In GitHub (extra confidence):** go to **Settings → Applications → Installed GitHub Apps** and
  confirm **Vercel** is listed. If it's there, the authorization definitely went through.

Ada will still double-check it for real in Module 4, when Vercel imports your actual repo.

**Pass when:** GitHub appears as a **connected Git provider** in Vercel, *and* when you start a new
project import your **GitHub account/repositories are listable** (even if the list is currently
empty because you haven't made a repo yet). That combination proves the authorization worked.

**Most common mistakes Ada will help you fix:**
- **Authorized the wrong GitHub account.** If Vercel is connected to a different GitHub login than
  the one from Module 2, your future repo won't show up. Ada will help you disconnect and reconnect
  the correct account (in Vercel's Git/connections settings) so it matches Module 2.
- **Restricted repository access too tightly.** If you chose "only select repositories" and didn't
  include the project you'll create next module, Vercel won't see it. Fix: in GitHub's settings for
  the Vercel app, either switch to **All repositories** or add the specific repo. Ada can point you
  to where that setting lives (GitHub → Settings → Applications → the Vercel GitHub app).

To confirm what to paste, Ada may ask: "When you click to import/add a new project in Vercel, does
your GitHub account show up and can you see (an empty) list of your repositories?"

**When this passes, you've earned the `vercel-ready` badge — GitHub and Vercel are officially
connected. That's Module 3 done. Next module, you'll put a real app online.**

## Challenge

Take a quick look at GitHub → **Settings → Applications** (or "Installed GitHub Apps"). Find the
Vercel entry and read what access it lists. Seeing exactly what you granted — and knowing you could
change or revoke it here anytime — is a great habit for staying in control of your accounts.

## Hints

- In Vercel, look for anything about **connecting GitHub** or **importing a project** — that's what
  kicks off the authorization. It'll bounce you over to GitHub to approve.
- On GitHub, **authorize/install the Vercel app** using the *same* GitHub account you used in Module
  2, and when it asks which repos, choose **All repositories** so your future project is visible.
- To prove it worked without creating anything: in Vercel, click to **add a new project / import a
  repository**. If your GitHub account and its (empty) repo list appear, you're connected — tell
  Ada that's what you see.
