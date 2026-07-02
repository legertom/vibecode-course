# Glossary — plain-English words for everything you'll meet

New words can feel like a wall. They're not — each one is just a simple idea wearing a fancy coat.
Here's every term you'll bump into in this course, explained the way a friend would explain it.
No need to memorize any of it; come back whenever a word feels unfamiliar.

And the recurring good news: **everything here is free.** GitHub, the Vercel Hobby plan, and Next.js
are all $0, and your tasks save right in the browser — so nothing ever bills you.

---

**Ada**
Your tutor for this course — the friendly guide Claude speaks as while teaching you. Ada greets
you, explains each step, runs commands for you, checks your work, and remembers where you are. The
name is a nod to *Ada Lovelace*, often called the world's first programmer.

**Terminal**
A place where you type short text commands to tell the computer what to do, instead of clicking
buttons. In this course, Ada usually types in the terminal for you — you mostly watch and decide.

**Command**
One short instruction you give the computer in the terminal, like `ls` (list files) or `node -v`
(show a version). Think of it as a single spoken request.

**Node.js**
The "engine" that runs the tools we use to build your app. You won't use it directly — it just
works quietly in the background. It's free.

**npm**
Node's built-in helper for downloading the free building blocks (called *packages*) your app needs.
It comes bundled with Node.js. If Node is the motor, npm is the parts delivery.

**Git**
A free tool that quietly saves *versions* of your files as you work — like an unlimited undo history
for your whole project. It's also how your code travels up to GitHub.

**Commit**
A saved snapshot of your work, with a short caption. Like taking a photo of your project right now
and writing a note on the back ("Build the to-do app"). Old snapshots are never lost.

**Push**
Sending your saved snapshots (commits) up from your computer to GitHub, your code's online home.

**Repository (repo)**
A labeled project folder that lives on GitHub, holding all the code for one project. "Repo" is just
the short, friendly name for it.

**GitHub**
A free website where your code lives safely in the cloud. It backs up your work, remembers every
change so you can undo, and is the place your live app is published *from*. It's free for everything
we do — no credit card, ever.

**GitHub CLI (gh)**
A small helper tool (its command is `gh`) that connects your computer to GitHub. "CLI" just means a
tool you type commands to. It handles login through your browser, so there are no fiddly passwords to
copy by hand.

**Next.js**
A popular, free, open-source *framework* (a ready-made starter kit) for building websites and web
apps. It gives you a working app before you write a single line — that's the head start you get in
Module 4.

**App Router**
The modern way Next.js organizes an app's pages, using an `app` folder. It's why your main file lives
at `app/page.js`. You don't have to think about it — it's just how the app is laid out.

**Component**
A reusable building block of a web page — a labeled chunk of the interface, like a button or a whole
page. Your to-do app's home page is one component.

**"use client"**
A tiny line — literally the words `"use client"` with the quotes — that goes at the very top of
`page.js`. It tells Next.js "this page runs interactive code in the browser," which is what makes
typing and clicking work. Without it, the interactive parts break. Ada makes sure it's there.

**React**
The technology (built into Next.js) that lets a web page *react* to what you type and click — updating
what's on screen instantly. It's what makes your to-do list feel alive.

**State**
The information a page is currently remembering — for your app, that's the list of tasks. When the
state changes (you add a task), React updates the screen to match. React's tool for this is called
`useState`.

**localStorage**
A small, free storage space built right into your web browser — like a little notepad the browser
keeps for your app. It's how your tasks survive a page refresh, with **no database and no server**,
so nothing ever bills you. One honest trade-off: it saves *per browser, per device*, so your phone and
laptop each keep their own separate list.

**Deploy**
Publishing your app so it's live on the internet for anyone to visit. In this course, deploying is
automatic: you push your code to GitHub, and Vercel deploys it for you.

**Vercel**
A free service that takes your code from GitHub and puts it live on the web at a real address. Once
connected, it re-publishes automatically every time you push a change — no servers to manage.

**Hobby plan**
Vercel's free plan — the one this whole course uses. It's genuinely free, even when you sign up with
your Clever work email. No card, no bill.

**localhost**
A special address that means "this very computer." When you preview your app locally, it lives at
`http://localhost:3000` — an address only *you* can reach. Nobody else on the internet can see it.

**Dev server**
A small program ("dev" is short for development) that runs your app on your own computer so you can
preview it privately at `http://localhost:3000`. It's your safe rehearsal space before publishing.
Started with `npm run dev`.

**URL / domain**
A web address. Your live app gets one from Vercel, like `todo-app-yourname.vercel.app` — you can open
it on your phone and share it with anyone. The "domain" is the main part of that address.

**Framework**
A ready-made starter kit that handles the boring, repetitive parts of building an app so you can focus
on the fun parts. Next.js is the framework we use — it's free and open source.

**Dependency**
A free building block (a *package*) that your app relies on. They're listed in a file called
`package.json`. For example, your app depends on `next`. npm downloads them for you.

**Frontend**
The part of an app you actually see and interact with in your browser — the buttons, text boxes, and
lists. Your whole to-do app is frontend, which is part of why it stays so simple and free.

**Installer / `.pkg`**
On a Mac, a `.pkg` file is a click-through installer. You double-click it and follow the steps, and it
asks for your **Mac password** (the one you log in with) because it's adding software. This is the
gentlest way to install tools like Node.js. All the ones in this course are free.

**Command Line Tools (Apple)**
A free set of developer tools from Apple that includes **Git**. You get them by running
`xcode-select --install` in the Terminal and clicking **Install**. You don't use them directly — they
just need to be present.

**Homebrew**
An optional "package manager" for Macs — one tool that installs and updates other tools (Node, Git,
`gh`) with short commands like `brew install node`. Handy but not required; the official installers
work fine on their own. Its command is `brew`.

**PATH**
The list of places your computer looks for tools you type. If you just installed something but the
Terminal says *"command not found,"* it usually means a window opened *before* the install and hasn't
refreshed its PATH yet — quitting and reopening Claude Code fixes it.

---

If a word ever trips you up mid-lesson, just ask Ada — "what does *deploy* mean again?" is a perfectly
good question, always. You're learning a new language, one gentle word at a time.
