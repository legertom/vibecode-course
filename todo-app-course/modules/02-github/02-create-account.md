---
id: "2.2"
module: 2
lesson: 2
title: "Create your free GitHub account"
estimated_minutes: 8
objectives:
  - "Create a free GitHub account and verify your email, then share your new username so Ada can confirm your public profile exists online."
prerequisites: ["2.1"]
success_criteria:
  - "A GitHub account exists at github.com/<username>, verifiable by fetching the public profile (HTTP 200 from curl -sI https://github.com/<username>, or a successful gh api users/<username>)."
badge: null
---

## Learn

Now that you know *why* GitHub is useful, let's get you an account. This is a quick sign-up
on a website — the kind you've done many times before.

A couple of things to know before you start, so nothing feels surprising:

- **It's free.** The account, the storage, the history — $0. You will **not** be asked for a
  credit card. If any screen ever mentions a paid plan, you can safely ignore it; the free
  option is all we need for this entire course.
- **Which email should you use?** Either works. You can use your **Clever work email** or a
  **personal email** — your choice. In fact, many developers attach a *personal* email to
  GitHub so their account travels with them between jobs, so a personal email is a perfectly
  good pick. Use whichever you'll remember and can check right now (you'll need to open a
  verification message).
- **Your username is public.** Pick something you're comfortable being seen — your name, a
  nickname, or a handle you like. It becomes part of your web address, like
  `github.com/your-username`.

That's it. Let's create it.

## Practice

You'll do this part in your web browser, and Ada will walk you through it step by step.

1. Open your browser and go to **github.com**.
2. Find the option to **sign up** for a new account (usually near the top-right of the page).
3. Enter an **email address** — your Clever work email *or* a personal email, whichever you
   prefer.
4. Create a **password** you'll remember (a longer passphrase is easier to recall and safer).
5. Choose a **username**. This is public and becomes part of your address, so pick something
   you like. If your first choice is taken, GitHub will suggest alternatives — pick one.
6. Finish the sign-up steps. GitHub will send a **verification code or link to your email**.
   Open that email and enter the code (or click the link) to confirm your address. This step
   matters — until you verify, GitHub keeps nagging you and some features stay locked.
7. Once you land on your logged-in GitHub home page, come back here and **tell Ada your new
   username** (just the username, not your password).

Then run `/check` so Ada can confirm your account is live on the web.

## Check

Ada verifies the account really exists online using the username the learner provides. Run
one of these (they don't need the learner's password — a public profile is enough):

```
curl -sI https://github.com/<username>
```

- **PASS** — the response's first line shows **HTTP/2 200** (or **HTTP/1.1 200 OK**). That means
  the public profile page loads, so the account exists. As a second option, Ada can run
  `gh api users/<username>` and confirm it returns profile JSON (with a `login` field matching
  the username) rather than a "Not Found" error. Celebrate — they now exist on GitHub!

Common mistakes to check kindly:

- **Username typo.** A `404` / "Not Found" usually means the username was mistyped or misheard.
  Ask the learner to open their GitHub page and read the exact username from the browser's
  address bar (`github.com/<this-part>`), then try again.
- **Email not verified yet.** The profile can still load before verifying, but remind the learner
  to click the link / enter the code GitHub emailed them, or GitHub will keep prompting and block
  some actions we'll need later. If they can't find the email, have them check spam and use
  GitHub's "resend" option.
- **Confused work vs. personal email.** If they can't verify, double-check they're opening the
  inbox for the exact address they typed during sign-up.
- **`curl` can't reach GitHub** (a work network blocks it, or there's no connection). Don't fail
  the learner for this — ask them to open `github.com/<username>` in their browser and paste the
  address bar or a screenshot showing their profile page loads. That's proof enough.

## Challenge

Optional: on your GitHub profile, add a short bio or a display name so it feels like *yours*.
Totally cosmetic and never required — but a nice little "this is me on the internet" moment.

## Hints

- Everything happens at **github.com** — look for the sign-up option near the top-right corner
  of the page.
- Use an email you can open right now (work or personal — both are fine), because you'll need
  to grab the verification code or link GitHub sends you.
- After you're logged in, your username is the last part of your web address: open
  `github.com/<username>` and read it straight from the browser's address bar — that's exactly
  what you paste to Ada.
