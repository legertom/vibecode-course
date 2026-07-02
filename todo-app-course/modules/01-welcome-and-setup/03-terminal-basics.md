---
id: "1.3"
module: 1
lesson: 3
title: "Terminal & folders 101"
estimated_minutes: 7
objectives:
  - "Understand what the terminal is and the three basics (where am I, what's here, how to move), and correctly identify what's in your workspace folder."
prerequisites: ["1.2"]
success_criteria:
  - "After Ada lists the workspace folder, the learner correctly names its contents (for example, identifies my-goal.md as a file that's there)."
badge: "setup-complete"
---

## Learn

Let's demystify the scariest-looking part of building apps: the **terminal**. It's just a place where you type short commands instead of clicking buttons — a text way to tell the computer what to do. That's all. And here's the reassuring bit: **in this course, I usually run the commands for you.** You mostly watch, understand, and decide. You truly cannot break anything just by looking around.

There are only three basics worth knowing, and they map to plain questions:
- **Where am I?** — the command `pwd` ("print working directory") shows the folder you're currently standing in.
- **What's here?** — the command `ls` ("list") shows the files and folders in that spot.
- **How do I move?** — the command `cd` ("change directory") steps you into a different folder, like double-clicking to open one.

That's the whole map. Folders on a computer nest inside each other like labeled boxes inside boxes, and these three commands let you see where you are, look inside a box, and step into another. We'll lean on them gently throughout the course — but you'll rarely type them yourself.

## Practice

Let's take a peaceful look inside your **workspace** — the folder that holds everything you build here.

1. Ask me to list what's in the `workspace/` folder (I'll run `ls` there and read the results to you).
2. Look at what I show you and tell me, in your own words, what file (or files) you see.

You should spot **`my-goal.md`** — the goal file we made together in Lesson 1.1. You may also see a small file called **`.gitkeep`**; that's just a placeholder that keeps the folder around, and it's completely fine to ignore. When you've told me what's there, say `/check`.

## Check

To pass, you correctly name what's in the workspace folder after I list it — most importantly, that **`my-goal.md`** is there.

- I verify by running `ls` (I'll use `ls -a workspace/` so hidden files like `.gitkeep` show too) and comparing your answer to the real contents.
- **Pass:** you name `my-goal.md` (and it's okay if you also mention `.gitkeep`). You've read a real folder listing — nicely done.
- **Common mistake 1:** forgetting Lesson 1.1's file was saved and expecting the folder to be empty. If `my-goal.md` truly isn't there, we pop back to 1.1 and create it together, then return here.
- **Common mistake 2:** being unsure whether `.gitkeep` "counts." It does count as a file, but it's just a placeholder — I'll reassure you it's harmless and not something you'll ever edit.

When this passes, that's **Module 1 complete** and you earn your first badge: **setup-complete**. Your tools work, you've met the terminal, and you've made your first files. That's a real milestone — take the win!

## Challenge

Optional: ask me to run `pwd` so you can see the full path (the "address") of where we're working, then ask me to `ls` the whole course folder (one level up from `workspace/`). See if you can spot the `modules/` folder — that's where every lesson, including this one, lives.

## Hints

- You don't type anything — just ask me to show you what's inside the `workspace` folder, then read back what you see.
- I'll print a short list of names. Your job is simply to tell me one file you notice — the one you created last lesson is a great pick.
- The file to name is **`my-goal.md`** (from Lesson 1.1). If you also see `.gitkeep`, that's just a harmless placeholder — mentioning it is fine, but naming `my-goal.md` is what I'm looking for.
