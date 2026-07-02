# Installing your tools on a Mac 🛠️

This is your one-stop guide for getting the free tools this course needs onto a **recent Mac**:
**Node.js** (with **npm**), **Git**, and the **GitHub CLI** (`gh`). Ada will point you here when
it's time. Everything below is **$0** — free downloads, no credit card, ever.

**One thing to know up front (it's why Ada asks *you* to do these steps):** installing software on
a Mac needs either a **double-click on an installer** or **your Mac's password**. Ada can't click
buttons or type your password for you — so *you* run the install, and then **Ada checks it worked**
by running things like `node -v`. Think of it like the account sign-ups: you do the clicking, Ada
confirms the result.

> 💡 **The golden rule after ANY install:** if a tool you just installed still says
> *"command not found,"* **fully quit and reopen Claude Code** (and/or your Terminal). Freshly
> installed tools are only visible to windows opened *after* the install. This fixes it 9 times
> out of 10.

---

## Two ways to do this: Auto or DIY

Ada can offer you two working styles (you pick once, and can switch anytime):

- **🤝 Auto — "do it with me":** Ada runs each command for you, asks your OK each time, and only
  hands off the bits it *can't* do (your Mac password, an install pop-up, a browser). For Auto, the
  smoothest route is **Homebrew** (Section 4): you paste one command and your password *once*, and
  after that Ada can `brew install` everything for you.
- **🧑‍💻 DIY — "I'll drive":** Ada explains each step and you run it. For DIY, the **official
  installers** (Sections 1–3) are the gentlest — mostly double-clicking.

**What Ada can never do for you, in either style:** type your **Mac password**, click a **native
install pop-up**, or use a **web browser**. So the initial Homebrew install, any `.pkg` install, the
`xcode-select` dialog, and `gh auth login` are always *your* hands on the keyboard — Ada guides and
then checks the result.

---

## 0. Opening the Terminal (you'll need it a couple of times)

Press **⌘ (Command) + Space** to open Spotlight, type **Terminal**, and press **Return**. A small
window opens where you can type commands. That's the Terminal. You can leave it open — Ada does
most of the typing, but a few install steps you'll paste in here yourself.

---

## 1. Node.js + npm (the engine that builds your app)

Node.js is the motor; npm (which comes bundled with it) fetches the free building blocks. We want
version **18.18 or newer** — the current **LTS** ("Long-Term Support," the stable one) is perfect.

**Recommended way — the official installer (no extra tools, just clicking):**
1. Go to **nodejs.org**.
2. Click the big download button labeled **LTS**. It gives you a macOS installer file ending in
   `.pkg`.
3. Open that `.pkg` file (double-click it in your Downloads) and click **Continue / Agree /
   Install** through the steps.
4. When it asks for your **Mac password**, type it (the same one you use to log in). This is normal
   and safe — macOS asks for it whenever software is installed.
5. When it says it's done, tell Ada — Ada will run `node -v` and `npm -v` to confirm.

**Alternative:** if you set up Homebrew (Section 4), you can instead run `brew install node`.

---

## 2. Git (saves versions of your work; sends code to GitHub)

Macs don't always ship with Git, but macOS has a built-in way to add it in one step.

**Recommended way — Apple's Command Line Tools:**
1. In the Terminal, type this and press Return:
   ```
   xcode-select --install
   ```
2. A little window pops up asking to install the **Command Line Developer Tools**. Click
   **Install**, then **Agree**. (This is a free, official Apple package; it includes Git.)
3. Wait for it to finish (a few minutes), then tell Ada — Ada will run `git --version` to confirm.

> Tip: sometimes just typing `git --version` the first time *itself* triggers that install pop-up.
> If it does, click **Install** and let it run.

**Alternative:** download the installer from **git-scm.com**, or (with Homebrew) run
`brew install git`.

---

## 3. GitHub CLI — `gh` (logs your computer in to GitHub)

You'll use this in Module 2 to connect your computer to GitHub.

**Recommended way — the official installer (no Homebrew needed):**
1. Go to **cli.github.com** and find the download for macOS — it's a `.pkg` installer (on the
   releases page, look for the file ending in `macOS.pkg`).
2. Open the `.pkg`, click through the installer, and enter your **Mac password** when asked.
3. When it's done, tell Ada — Ada will run `gh --version` to confirm.

**Alternative (with Homebrew):** `brew install gh`.

> Note: *logging in* with `gh auth login` is a separate, interactive step you run yourself in the
> Terminal (it asks you a couple of questions and opens your browser). Lesson 2.3 walks you through
> it, and Ada checks the result with `gh auth status`.

---

## 4. (Optional) Homebrew — "one tool to install everything"

**Homebrew** is a popular *package manager* for Macs — a single tool that installs and updates
other tools (like Node, Git, and `gh`) with one-line commands. It's completely optional: the
official installers above work great on their own. But if you'd like one tidy way to manage
everything — or you already know you want it — here's the safe path.

**Install it (paste this into *your* Terminal — Ada can't, because it asks for your password):**
```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```
- It may first offer to install Apple's **Command Line Tools** — say yes; that also gives you Git.
- It will ask you to **press Return** and then type your **Mac password**. That's expected.
- It takes a few minutes. Let it finish.

**Then, on Apple Silicon Macs (M1/M2/M3/M4), add Homebrew to your path** — the installer prints
"Next steps" telling you to run two lines that look like this (Ada can run these for you, or paste
them yourself):
```
echo 'eval "$(/opt/homebrew/bin/brew shellenv)"' >> ~/.zprofile
eval "$(/opt/homebrew/bin/brew shellenv)"
```
This just tells your Mac where Homebrew lives. (On older Intel Macs it's already in the right place,
so you can skip this.)

**Confirm and use it:**
```
brew --version
brew install node gh
```
That installs Node.js and the GitHub CLI in one go. For Git, you can use `brew install git` or the
Command Line Tools from Section 2.

---

## 5. The final check (Ada runs these)

Once things are installed, Ada confirms your toolbox by running:
```
node -v        # want v18.18.0 or higher
npm -v         # any version
git --version  # any version
gh --version   # any version
```
If any still says *"command not found"* right after installing, remember the **golden rule**:
fully quit and reopen Claude Code so it sees the new tools, then Ada re-checks.

You don't have to memorize any of this — Ada will guide you step by step and do all the checking.
Errors along the way are normal; we just tidy them up together. 💚
