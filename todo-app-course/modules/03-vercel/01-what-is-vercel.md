---
id: "3.1"
module: 3
lesson: 1
title: "What Vercel is (and why it's your app's home on the web)"
estimated_minutes: 6
objectives:
  - "Explain in your own words that Vercel is free hosting that publishes your app on the web and auto-updates it when you push to GitHub"
prerequisites: ["2.3"]
success_criteria:
  - "Learner correctly states, in their own words, that Vercel hosts/publishes their app on the web for free (and/or that it auto-deploys every time they push to GitHub)"
badge: null
---

## Learn

Nice work getting GitHub set up. Right now your code has a safe online home — but a home isn't the
same as a *storefront*. GitHub keeps your code; it doesn't turn it into a website people can visit.

That's Vercel's job.

**Vercel is a free hosting service.** ("Hosting" just means: a company runs a computer that's
always on, so your website is available to anyone, anytime — you don't have to keep your laptop
running.) You hand Vercel your code, and it turns it into a real, public website with its own web
address (like `your-app.vercel.app`) that you can share with anyone.

Here's the part that makes it feel like magic. Once you connect Vercel to your GitHub (that's the
next couple of lessons), it watches your code. Every time you save an update to GitHub — which
we'll call a "push" — Vercel automatically rebuilds and republishes your site. This is often called
"deploy on push." You change your code, push it, and a minute later the live site shows the change.
No buttons, no servers, no fuss.

**And it's $0.** Vercel's free plan is called "Hobby," and it's genuinely free — plenty for this
whole course. Even though you'll sign up with your Clever work email in the next lesson, it's still
the free Hobby plan. No card, no bill.

So the picture is: **you write code → GitHub stores it → Vercel publishes it live.** Three free
tools, working together.

## Practice

No terminal, no clicking this time — just a quick check that the idea landed, in *your* words.

Tell Ada, in a sentence or two: **what does Vercel do for you?**

Try to capture at least one of these:
- Vercel *hosts / publishes* your app on the web (puts it online at its own address), for free, or
- Vercel *automatically updates* your live site every time you push your code to GitHub.

There's no perfect wording. Just say it how you'd explain it to a friend.

## Check

Ada reads your answer and passes this lesson if you show you understand the core idea: **Vercel
puts your app on the internet (hosts/publishes it) for free, and/or it auto-deploys your app each
time you push to GitHub.**

- **Pass:** anything like "It's free hosting that puts my app online" or "It publishes my site and
  re-publishes it automatically whenever I push to GitHub." Any phrasing in your own words is great.
- **Gentle corrections Ada may offer:**
  - If you say Vercel *stores* your code — that's GitHub's job. Vercel *publishes* it to the web.
  - If you worry it costs money — it doesn't. The Hobby plan is free, even with a work email.
  - If you're unsure about "deploy on push," Ada will restate it: push to GitHub → Vercel updates
    your live site automatically.

## Challenge

In one line, describe the three-step relationship between your computer, GitHub, and Vercel.
(Hint to yourself: who *writes*, who *stores*, who *publishes*?)

## Hints

- Think about the difference between where your code is *kept* versus where your app is *seen* by
  the public. Which of those is Vercel?
- Vercel is the piece that makes your app appear on the internet at a real web address — and it
  refreshes that live version by itself whenever your code changes on GitHub.
- Try a sentence like: "Vercel is free hosting that publishes my app on the web, and it
  automatically updates the live site every time I push my code to GitHub."
