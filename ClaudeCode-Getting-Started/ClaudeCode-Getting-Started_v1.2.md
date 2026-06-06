# Claude Code: Project Process Guide

### A structured development process for AI-assisted software projects using VS Code and Claude Code

**Version:** 1.2
**Last Updated:** 2026-05-22
**Audience:** This document has been designed to assist those new to software development. **Primary tools:** [Visual Studio Code](https://code.visualstudio.com) and [Claude Code](https://claude.com/docs)
**Purpose:** A reusable, step-by-step process for setting up and running software projects, from installing VS Code to publishing a release on GitHub.

> **What changed in v1.2:** The structural additions in this version are grounded in Dave Rensin's essay [*Elephants, Goldfish, and the New Golden Age of Software Engineering*](https://drensin.medium.com/elephants-goldfish-and-the-new-golden-age-of-software-engineering-c33641a48874) (2026), which introduced the Elephant-Goldfish Model (EGM) of AI-assisted development. Rensin's central insight is that the design document has replaced source code as the highest-leverage artifact in a software project: when an AI session can implement anything quickly, the quality of what gets built is determined almost entirely by the quality of the thinking that precedes it. The additions below apply that principle concretely.
>
> Added Step 0 (Design-First Phase) -- a structured pre-implementation protocol drawn directly from EGM. Merged BUILD_OVERVIEW.md into DESIGN_NOTES.md, which is now the single living design artifact for every project and lives in the source tree (pushed to GitHub). DESIGN_NOTES.md covers active file descriptions, design decisions and alternatives, and per-feature design documents from Step 0. Updated Section 10 (backlog entry format) to include acceptance criteria. Updated Section 14 (documentation update policy) to reference DESIGN_NOTES.md. Added documentation completeness test (Goldfish test) and adversarial code review to Section 17. Added sycophancy management and session recovery protocol to Section 18. For a full gap analysis between this process and EGM, see EGM_Workflow_Gap_Analysis.md.

---

## Table of Contents

- [PART 1 - Overview and Foundational Information](#part-1--overview-and-foundational-information)
  * [Section 1 - Getting started with VS Code](#section-1--getting-started-with-vs-code)
    + [Install VS Code](#install-vs-code)
    + [The VS Code interface](#the-vs-code-interface)
    + [Install the Claude Code extension](#install-the-claude-code-extension)
    + [Install Node.js](#install-nodejs)
  * [Section 2 - Understanding the terminal and common commands](#section-2--understanding-the-terminal-and-common-commands)
    + [Navigation](#navigation)
    + [Files and folders](#files-and-folders)
    + [Searching and editing text](#searching-and-editing-text)
    + [Node.js and project packages](#nodejs-and-project-packages)
    + [Git commands](#git-commands)
    + [Environment and credentials](#environment-and-credentials)
    + [HTTP requests and APIs](#http-requests-and-apis)
    + [Python](#python)
    + [Checking installations](#checking-installations)
    + [A note on using these with Claude](#a-note-on-using-these-with-claude)
  * [Section 3 - Getting started with GitHub](#section-3--getting-started-with-github)
    + [What GitHub is](#what-github-is)
    + [Create a free GitHub account](#create-a-free-github-account)
    + [What you can do on GitHub in a browser](#what-you-can-do-on-github-in-a-browser)
    + [Get a Personal Access Token](#get-a-personal-access-token)
    + [Do you need to install Git?](#do-you-need-to-install-git)
    + [Pushing to GitHub via Claude](#pushing-to-github-via-claude)
    + [Viewing your project on GitHub](#viewing-your-project-on-github)
  * [Automate setup with the /new-project skill](#automate-setup-with-the-new-project-skill)
  * [Section 4 - Two ways to work with Claude Code](#section-4--two-ways-to-work-with-claude-code)
    + [Option A: Claude Code Desktop App (no terminal required)](#option-a-claude-code-desktop-app-no-terminal-required)
    + [Option B: VS Code Terminal and Claude Code](#option-b-vs-code-terminal-and-claude-code)
  * [Section 5 - Why this process exists](#section-5--why-this-process-exists)
  * [Section 6 - Choosing a project and when to code](#section-6--choosing-a-project-and-when-to-code)
    + [The learning opportunity](#the-learning-opportunity)
    + [Choosing your first project](#choosing-your-first-project)
    + [When to code vs. when to find another solution](#when-to-code-vs-when-to-find-another-solution)
    + [The progression](#the-progression)
  * [Section 7 - The file system: what lives where](#section-7--the-file-system-what-lives-where)
    + [Standard `_archive/` documents](#standard-_archive-documents)
- [PART 2 - Designing & Coding](#part-2--designing--coding)
  * [Section 8 - Starting a new project](#section-8--starting-a-new-project)
  * [Step 0 - Design-first phase: before writing any code](#step-0--design-first-phase-before-writing-any-code)
    + [Step 1: The no-code rule](#step-1-the-no-code-rule)
    + [Step 2: Write the design document](#step-2-write-the-design-document)
    + [Step 3: Goldfish Comprehension Test](#step-3-goldfish-comprehension-test)
    + [Step 4: Adversarial design review](#step-4-adversarial-design-review)
    + [Step 5: Confirm implementation readiness](#step-5-confirm-implementation-readiness)
  * [Section 9 - The change log: the most important habit](#section-9--the-change-log-the-most-important-habit)
    + [Entry format](#entry-format)
  * [Section 10 - The backlog: managing future work](#section-10--the-backlog-managing-future-work)
    + [Priority levels](#priority-levels)
    + [The implement-or-backlog question](#the-implement-or-backlog-question)
    + [Entry format](#entry-format-1)
  * [Section 11 - Security practices](#section-11--security-practices)
    + [The golden rule](#the-golden-rule)
    + [The `.env` file](#the-env-file)
    + [Automated security review](#automated-security-review)
  * [Section 12 - The README.md](#section-12--the-readmemd)
    + [What to include](#what-to-include)
    + [What to leave out](#what-to-leave-out)
  * [Section 13 - Build and release workflow](#section-13--build-and-release-workflow)
    + [Build commands](#build-commands)
    + [The RELEASE folder](#the-release-folder)
    + [Publishing a release](#publishing-a-release)
  * [Section 14 - Documentation update policy](#section-14--documentation-update-policy)
  * [Section 15 - Archive documents reference](#section-15--archive-documents-reference)
  * [Section 16 - `CLAUDE.md`: project instructions for the AI](#section-16--claudemd-project-instructions-for-the-ai)
    + [What to put in `CLAUDE.md`](#what-to-put-in-claudemd)
    + [What not to put in `CLAUDE.md`](#what-not-to-put-in-claudemd)
  * [Section 17 - QC rounds: catching problems early](#section-17--qc-rounds-catching-problems-early)
    + [Common checks](#common-checks)
    + [Documentation completeness check (Goldfish test)](#documentation-completeness-check-goldfish-test)
    + [Adversarial code review](#adversarial-code-review)
  * [Section 18 - Instructions for Claude](#section-18--instructions-for-claude)
    + [Sycophancy reset (for the user)](#sycophancy-reset-for-the-user)
    + [Session recovery protocol](#session-recovery-protocol)

---


# PART 1 -- Overview and Foundational Information


## Section 1 — Getting started with VS Code


Visual Studio Code (VS Code) is a free code editor made by Microsoft. It works on Windows, macOS, and Linux, and integrates directly with Claude Code.
> **Ways to access Claude Code:** Claude Code can be accessed in several ways, including the Claude Code desktop app, the VS Code extension, and via your operating system terminal. This guide covers the desktop app and the VS Code extension only. Access via the OS terminal is not addressed here.

[Visual Studio Code documentation](https://code.visualstudio.com/docs)

### Install VS Code


1. Go to [code.visualstudio.com](https://code.visualstudio.com) and download the installer for your operating system
2. Run the installer and follow the prompts
3. Launch VS Code


[Getting started with VS Code](https://code.visualstudio.com/docs/introvideos/basics)

### The VS Code interface


| Panel      | Location     | Purpose                               |
| ---------- | ------------ | ------------------------------------- |
| Explorer   | Left sidebar | Shows your project files and folders  |
| Editor     | Centre       | Where you read and edit files         |
| Terminal   | Bottom       | Command line for running instructions |
| Status bar | Very bottom  | Shows current file and project info   |


**Opening the terminal panel in VS Code:** The easiest way for new users is to use the menu bar at the top of the VS Code window: click **Terminal**, then click **New Terminal**. A terminal panel will appear at the bottom of the screen. You can also use the keyboard shortcut `` Ctrl+` `` (Windows/Linux) or `` Cmd+` `` (Mac) once you are comfortable with VS Code.

[VS Code user interface overview](https://code.visualstudio.com/docs/getstarted/userinterface)

### Install the Claude Code extension


1. Click the **Extensions** icon in the left sidebar (four squares) or press `Ctrl+Shift+X` / `Cmd+Shift+X`
2. Search for **Claude Code**
3. Click **Install**
4. Follow the sign-in prompts


[VS Code Extensions](https://code.visualstudio.com/docs/editor/extension-marketplace) | [Claude Code documentation](https://claude.com/docs)

Once installed, open Claude Code from the sidebar. Type instructions in plain English and Claude reads your files, runs commands, and makes changes on your behalf.

### Install Node.js


**What is JavaScript?**

JavaScript is the programming language that makes web pages interactive. When you click a button on a website and something happens without the page reloading, that is almost certainly JavaScript running in your browser. It is the most widely used programming language in the world and the default language for web-based projects.

Despite the similar name, **JavaScript and Java are unrelated.** Java is a separate programming language developed by Sun Microsystems in the 1990s, typically used for enterprise software and Android apps. The name "JavaScript" was a marketing decision made at the time of its release to ride the popularity of Java; the two languages have different syntax, different purposes, and different ecosystems. They are no more related than "car" and "carpet."

**What is Node.js?**

JavaScript was originally designed to run only inside a web browser. Node.js changes that. It is a runtime environment that allows JavaScript to run directly on your computer, outside of any browser, the same way Python or other languages do. This means you can use JavaScript to write scripts, build tools, process files, and call APIs from the VS Code terminal -- without a web page involved at all.

Node.js also includes **npm** (Node Package Manager), which is a library of over a million free, reusable software packages. When a project needs a specific capability -- reading Excel files, connecting to an API, building a user interface -- npm lets you add that capability in seconds rather than writing it from scratch.

Most Claude Code projects that involve automation, web tools, or data processing are JavaScript projects that rely on Node.js and npm.

1. Go to [nodejs.org](https://nodejs.org) and download the **LTS** version (LTS stands for Long Term Support -- it is the stable, recommended version for most users)
2. Run the installer
3. Confirm: type `node --version` in the VS Code terminal

---


## Section 2 — Understanding the terminal and common commands

> **Note on terminology:** Throughout this guide, "terminal" always refers to the **terminal panel built into VS Code**, opened via **Terminal > New Terminal** in the menu bar. This is distinct from any standalone terminal application your operating system may provide. This guide does not cover OS-level terminals -- all terminal instructions here are intended to be run inside VS Code.

VS Code includes a built-in terminal panel -- a text-based interface where you type commands and press Enter to give instructions directly to your computer.

The commands in this guide are written in **bash**, the shell language used by default on macOS and Linux. On Windows, VS Code defaults to PowerShell, which uses different syntax and does not support many of the commands shown here. The simplest way to resolve this is to install **Git for Windows** (available at [git-scm.com](https://git-scm.com)), which includes Git Bash. Once installed, you can configure VS Code to use Git Bash as its terminal: open the Command Palette (`Ctrl+Shift+P`), search for **Terminal: Select Default Profile**, and choose **Git Bash**. All commands in this guide will then work identically on Windows, macOS, and Linux.

> **Using the Claude Code Desktop App?** If you are working in Option A (Section 4), Claude handles all terminal commands internally. You do not need to type commands yourself, and the shell differences described above rarely affect you. The terminal context matters most if you are using Option B (VS Code Terminal alongside the Claude Code extension).

In most cases you will not type these commands directly regardless of your operating system. Instead, describe what you want in plain English -- Claude reads your instruction, determines the correct command, and executes it on your behalf. This section is a reference so you can understand what Claude is doing and why, not a list of commands you are expected to learn.

### A note on AI safety: Claude will do what you ask

> **Claude executes instructions literally and immediately. Be deliberate about what you ask for.**

This is one of the most important things to understand when working with an AI assistant. Claude is highly capable and will attempt to carry out your request as stated -- it does not second-guess your intent or apply human judgment about whether an action is wise. If you ask Claude to delete files, it will delete them. If you ask it to overwrite something, it will overwrite it. If your instruction is ambiguous, Claude will make a reasonable interpretation and proceed.

**Practical habits that reduce risk:**

- **Read before you approve.** Claude Code will show you what it plans to do before running commands that change files or push to GitHub. Take a moment to read those summaries before clicking approve.
- **Ask in stages.** For complex tasks, break the request into smaller steps and review the result of each one before continuing. "Create the folder structure" before "create all the files" is safer than asking for everything at once.
- **Use a backlog.** If you are not sure whether a change is the right one, add it to the backlog instead of implementing it immediately. This gives you time to think before committing.
- **Archive before deleting.** Ask Claude to copy a file to `_archive/` before removing it. This is built into the process and provides a safety net.
- **Version control is your undo button.** With git in place, every committed state of the project can be recovered. Commit regularly so you always have a recent restore point.
- **Credentials are permanent damage.** If a token or password is typed into chat, treat it as compromised immediately and regenerate it. Claude cannot un-send a message.


**What Claude will not do without your approval:**

Claude Code asks for permission before running commands that could have significant consequences -- such as pushing to GitHub, deleting files, or installing packages. If you see an approval prompt, that is your opportunity to pause and verify the action before it runs.

**The underlying principle:** AI assistance is a tool, and like any tool its usefulness depends on how deliberately it is used. Clear, specific instructions produce predictable results. Vague or rushed instructions produce actions that may be technically correct but not what you intended. When in doubt, ask Claude to explain what it is about to do before it does it: *"What will happen if I ask you to do X?"*

[VS Code integrated terminal documentation](https://code.visualstudio.com/docs/terminal/basics)

### Navigation


| Command         | What it does                                       | Example                                         |
| --------------- | -------------------------------------------------- | ----------------------------------------------- |
| `pwd`           | Print the current folder you are in                | `pwd` shows `/Users/name/MyProject`             |
| `cd foldername` | Move into a folder                                 | `cd src` moves into the src folder              |
| `cd ..`         | Move up one folder level                           | `cd ..` moves from src back to the project root |
| `ls`            | List files and folders in the current location     | `ls` shows what is in the folder                |
| `ls -la`        | List all files including hidden ones, with details | Shows `.env`, `.gitignore`, and file sizes      |


### Files and folders


| Command                   | What it does                    | Example                              |
| ------------------------- | ------------------------------- | ------------------------------------ |
| `mkdir foldername`        | Create a new folder             | `mkdir _archive`                     |
| `touch filename`          | Create an empty file            | `touch notes.md`                     |
| `cp source destination`   | Copy a file                     | `cp file.txt backup.txt`             |
| `mv source destination`   | Move or rename a file           | `mv old.txt new.txt`                 |
| `rm filename`             | Delete a file permanently       | `rm temp.txt`                        |
| `zip -r name.zip folder/` | Create a ZIP file from a folder | `zip -r "Release v1.0.zip" RELEASE/` |


### Searching and editing text


These commands search inside files and make text replacements without opening a file editor. Claude uses them frequently when scanning or updating code.

| Command                            | What it does                                                                          | Example                                                                |
| ---------------------------------- | ------------------------------------------------------------------------------------- | ---------------------------------------------------------------------- |
| `grep "word" filename`             | Search for a word or phrase inside a file and print every matching line               | `grep "error" output.log` finds every line containing the word "error" |
| `grep -rn "word" folder/`          | Search recursively through all files in a folder, showing file names and line numbers | `grep -rn "TODO" src/` finds all to-do notes across every source file  |
| `grep -i "word" filename`          | Same as grep but ignores upper/lower case                                             | `grep -i "welcome" docs/` matches "Welcome", "WELCOME", and "welcome"  |
| `grep -v "word" filename`          | Print lines that do NOT contain the word                                              | Useful for filtering out unwanted results from a long list             |
| `sed 's/old/new/g' filename`       | Replace every occurrence of "old" with "new" in a file and print the result           | `sed 's/v1.0/v2.0/g' config.txt` updates every version reference       |
| `sed -i '' 's/old/new/g' filename` | Replace every occurrence directly inside the file (saves the change)                  | On macOS the syntax is `sed -i ''`; on Linux the syntax is `sed -i` with no empty string. Claude uses the correct variant for your system automatically. |


**When Claude uses grep:** To verify that a word or value appears (or does not appear) across many files at once -- for example, confirming no credentials remain in source code, or checking that all version numbers match.

**When Claude uses sed:** To make the same text replacement in a file without opening an editor -- for example, updating a version number or correcting a spelling across an entire file in one command.

### Node.js and project packages


These commands manage the software packages your project depends on.

| Command          | What it does                                                                                  |
| ---------------- | --------------------------------------------------------------------------------------------- |
| `npm install`    | Downloads all packages the project needs (run once when setting up, or after adding new ones) |
| `npm run build`  | Compiles the source code into the final output file                                           |
| `npm run dev`    | Runs the project in development mode -- rebuilds automatically when you save a file           |
| `node --version` | Confirms Node.js is installed and shows the version number                                    |


### Git commands


Git tracks every change to your project files. These commands are the core of that workflow.

| Command                   | What it does                                                                       |
| ------------------------- | ---------------------------------------------------------------------------------- |
| `git init`                | Sets up git tracking in the current folder -- run once when starting a project     |
| `git status`              | Shows which files have changed since the last save point                           |
| `git add .`               | Stages all changed files, preparing them to be saved                               |
| `git add filename`        | Stages a specific file only                                                        |
| `git commit -m "message"` | Saves a snapshot of the staged files with a description                            |
| `git push`                | Sends committed changes to GitHub                                                  |
| `git pull`                | Downloads the latest changes from GitHub to your local machine                     |
| `git pull --rebase`       | Downloads and reapplies local changes on top -- used when GitHub has newer commits |
| `git log`                 | Shows the history of all commits                                                   |
| `git diff`                | Shows exactly what has changed line by line                                        |


### Environment and credentials

**Variables, environment variables, and the `.env` file**

In programming, a **variable** is a named container that holds a value. Instead of typing the same value every time you need it, you give it a name once and refer to that name everywhere else. If the value ever changes, you update it in one place and every reference updates automatically.

For example, instead of writing your GitHub username in ten different places in a script, you create a variable called `GITHUB_USER` and set it to your username. The script uses `$GITHUB_USER` throughout. If you ever change your username, you change the variable once.

**Environment variables** are variables that exist at the operating system level rather than inside a single script. Once loaded, they are available to any program or script running in that terminal session -- including Claude. The dollar sign prefix (`$GITHUB_TOKEN`, `$VARIABLE_NAME`) is how the terminal signals "look up the value of this variable," rather than treating the word as literal text.

**The `.env` file** is a plain text file that stores your environment variables in one place, so you do not have to set them manually each session. It looks like this:

```
GITHUB_TOKEN=ghp_yourTokenHere
API_KEY=sk_someOtherKeyHere
```

The file is named `.env` -- the dot at the start is intentional. On Mac and Linux, files beginning with a dot are hidden from normal folder views by default; this is a convention for configuration files that should stay out of the way. On Windows, the file is not automatically hidden, but it will still be excluded from GitHub as long as `.gitignore` lists it. When Claude (or a script) runs `source .env`, it reads the file and loads every variable inside it into the current terminal session, making them available as `$GITHUB_TOKEN`, `$API_KEY`, and so on.

The reason credentials belong in `.env` rather than in code is isolation: the `.env` file is excluded from GitHub (via `.gitignore`), so your tokens never appear in version history or public repositories. The code references `$GITHUB_TOKEN` -- a name with no sensitive value. The actual token lives only on your machine, in the `.env` file, which never leaves it.

> **Warning: `.env` is plain text and is not encrypted.** Anyone who can read files on your computer can read your `.env` file. If your machine is accessed without your permission -- through malware, physical access, or a compromised account -- your credentials are exposed as clearly as if they were written in a notebook. The `.env` convention protects your credentials from being published to the internet via GitHub; it does not protect them from local access. For most personal projects this is an acceptable tradeoff. For credentials with serious consequences (payment processors, production databases, services that can incur charges), consider using your operating system's credential store or a dedicated secrets manager rather than a plain `.env` file. At minimum, keep your tokens scoped to the minimum permissions they need and set expiry dates when the service allows it -- a leaked token with limited scope and a near expiry causes far less damage than one with full access and no expiry.

> **Note on shell compatibility:** The commands below (`source`, `set -a`, `set +a`) are bash commands. On Mac and Linux they work in any terminal. On Windows, they require Git Bash (installed with Git for Windows) or the WSL terminal -- they will not work in Command Prompt or PowerShell. The VS Code terminal can be set to use Git Bash: click the dropdown arrow next to the `+` icon in the terminal panel and select **Git Bash**.

| Command               | What it does                                                                                                                                                         |
| --------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `source .env`         | Loads credentials from the `.env` file into the current terminal session. Run this before any session that needs to use `$GITHUB_TOKEN` or other stored credentials. |
| `set -a`              | Marks all variables for automatic export to child processes. Run before `source .env` so every credential is available to scripts Claude calls.                      |
| `set +a`              | Turns off automatic export. Run after `source .env` to restore normal shell behaviour.                                                                               |
| `set -e`              | Exits the script immediately if any command fails. Used at the top of scripts to catch errors early.                                                                 |
| `echo $VARIABLE_NAME` | Prints the value of a variable -- useful to confirm a credential loaded correctly (do not share the output)                                                          |


Claude's standard credential-loading pattern is `set -a && source .env && set +a`.

### HTTP requests and APIs


An **API** (Application Programming Interface) is a way for one piece of software to talk to another over the internet. When you ask Claude to create a GitHub repository or publish a release, it does not log into the GitHub website the way you would. Instead, it sends a structured message directly to GitHub's API -- a dedicated address that GitHub provides specifically for software to interact with it. GitHub reads the message, performs the action, and sends a response back. The whole exchange happens invisibly in the background.

Think of an API like a drive-through window: you make a specific request in the expected format, and the service fulfils it without you going inside.

**HTTP and HTTPS** are the protocols that govern how data is sent and received over the internet. HTTP (HyperText Transfer Protocol) is the set of rules your browser and other software follow when making requests and receiving responses -- every time you load a web page or call an API, HTTP is the language being spoken. HTTPS is the secure version: the "S" stands for Secure, meaning all data exchanged between your computer and the server is encrypted so it cannot be read if intercepted. Any URL beginning with `https://` is using this encrypted connection. In practice, always use `https://` URLs when making API calls -- they protect your credentials and data in transit.

These commands make network requests from the VS Code terminal. Claude uses them to call APIs (such as the GitHub API) and download files without a browser.

| Command                         | What it does                                              | Example                                                                   |
| ------------------------------- | --------------------------------------------------------- | ------------------------------------------------------------------------- |
| `curl -s URL`                   | Fetch the content of a URL silently (no progress bar)     | `curl -s https://api.github.com/repos/owner/repo`                         |
| `curl -s -o filename URL`       | Fetch a URL and save the response to a file               | `curl -s -o data.json https://api.example.com/data`                       |
| `curl -s -w "%{http_code}" URL` | Fetch a URL and append the HTTP status code to the output | Returns `200`, `201`, `404` etc. -- used to confirm an API call succeeded |
| `curl -L URL`                   | Follow redirects automatically                            | Used when a URL redirects to the real download location                   |
| `curl -I URL`                   | Fetch headers only, not the response body                 | Useful for checking whether a URL exists without downloading it           |
| `curl -X METHOD URL`            | Send a specific HTTP method (GET, POST, PUT, DELETE)      | `curl -X PUT ...` sends a PUT request                                     |
| `curl -H "Name: value" URL`     | Add a custom header to the request                        | `curl -H "Authorization: token $GITHUB_TOKEN" ...` sends an auth token    |
| `curl -d '{"key":"value"}' URL` | Send a JSON body with the request                         | Used with `-X POST` or `-X PUT` to send data to an API                    |


The full pattern Claude uses for an authenticated GitHub API call:

```
curl -s -o response.json -w "%{http_code}" -X PUT \
  -H "Authorization: token $GITHUB_TOKEN" \
  -H "Content-Type: application/json" \
  -d '{"key":"value"}' \
  https://api.github.com/repos/owner/repo/contents/path
```

**When Claude uses curl:** To make GitHub API calls (create files, upload releases, update content), to download files without opening a browser, and to verify whether a URL returns a valid response.

### Python

Python is one of the most widely used programming languages in the world, and consistently ranks as the most recommended language for people learning to code for the first time. It was created by Guido van Rossum and first released in 1991, with a design philosophy centred on readability: Python code is meant to read almost like plain English, which lowers the barrier for new programmers considerably compared to languages with more complex syntax.

**What Python is used for**

Python is a general-purpose language, meaning it can be applied to almost any kind of programming task. Its most common uses today include:

- **Data analysis and science** -- libraries like pandas, NumPy, and Matplotlib make Python the dominant language for working with data, running statistics, and building charts
- **Machine learning and AI** -- the majority of AI research and tooling (including the frameworks behind large language models) is written in Python
- **Automation and scripting** -- Python excels at automating repetitive tasks: renaming files in bulk, processing spreadsheets, scraping web pages, or calling APIs on a schedule
- **Web development** -- frameworks like Django and Flask let you build web applications and APIs in Python
- **Scientific computing** -- physics, biology, finance, and other technical fields rely heavily on Python for modelling and simulation

**Python vs. JavaScript: when does each apply?**

Both languages appear in this guide. The short version: JavaScript (via Node.js) is the natural choice for web-based projects, browser tools, and anything involving a user interface. Python is the natural choice for data processing, automation scripts, AI/ML work, and anything involving numerical computation. Many projects use both: a JavaScript front end that talks to a Python back end.

**How Python is installed on your system**

Unlike JavaScript (which runs natively in every browser), Python must be installed separately -- though the situation varies by operating system.

- **macOS:** Python is often pre-installed but may be an older version. Run `python3 --version` to check. If it is missing or outdated, download the latest version from [python.org](https://www.python.org/downloads/).
- **Windows:** Python is not pre-installed. Download it from [python.org](https://www.python.org/downloads/) and run the installer. During installation, check the box labelled **"Add Python to PATH"** -- this makes the `python3` command available in the VS Code terminal. Without it, the terminal will not find Python.
- **Linux:** Python is pre-installed on most distributions. Run `python3 --version` to confirm. If it is not present, install it through your distribution's package manager (e.g., `sudo apt install python3` on Ubuntu/Debian).

For most Claude Code projects, whatever recent version is installed is sufficient. If a project requires a specific version, Claude will tell you.

**Packages and pip**

Python's equivalent of npm is **pip** (Package Installer for Python). The Python ecosystem has hundreds of thousands of free packages available through the Python Package Index (PyPI). When Claude runs `python3 -m pip install pandas`, it is downloading the pandas data-analysis library from PyPI and making it available to your scripts.

**Virtual environments**

One complexity Python introduces is the concept of a **virtual environment**. When you install a Python package, it installs globally by default -- meaning every Python project on your machine shares the same set of packages. This causes problems when two projects need different versions of the same package. A virtual environment solves this by creating an isolated copy of Python inside a project folder (`.venv/`), so each project has its own packages that do not interfere with anything else. Claude creates and manages virtual environments automatically when a project needs them. You do not need to manage them manually.

Claude uses Python to run utility scripts, process data inline, and manage project dependencies.

| Command                             | What it does                                                                    | Example                                                                      |
| ----------------------------------- | ------------------------------------------------------------------------------- | ---------------------------------------------------------------------------- |
| `python3 script.py`                 | Run a Python script                                                             | `python3 build.py`                                                           |
| `python3 -c "code"`                 | Run a Python one-liner directly in the VS Code terminal without creating a file | `python3 -c "import json; print(json.load(open('data.json')))"`              |
| `python3 -m pip install package`    | Install a Python package                                                        | `python3 -m pip install Pillow`                                              |
| `python3 -m pip install package -q` | Install quietly -- suppresses most output                                       | Used when Claude installs dependencies mid-script without cluttering the log |
| `python3 -m venv .venv`             | Create a virtual environment (an isolated Python install for this project)      | Run once when starting a Python project                                      |
| `.venv/bin/python3 script.py`       | Run a script using the virtual environment's Python, not the system Python      | `.venv/bin/python3 build.py`                                                 |
| `.venv/bin/pip install package`     | Install a package into the virtual environment                                  | `.venv/bin/pip install Pillow -q`                                            |
| `python3 --version`                 | Confirm Python is installed and show the version                                | Returns `Python 3.12.x`                                                      |


**When Claude uses python3:** To run build or utility scripts, to process JSON or text data inline with `-c`, and to install packages into virtual environments before a build step.

### Checking installations


| Command             | What it does                                                |
| ------------------- | ----------------------------------------------------------- |
| `node --version`    | Confirms Node.js is installed                               |
| `git --version`     | Confirms Git is installed                                   |
| `npm --version`     | Confirms npm (the package manager for Node.js) is installed |
| `python3 --version` | Confirms Python 3 is installed                              |


### A note on using these with Claude


When working with Claude Code, you can ask Claude to run any of these commands on your behalf:
> *"Check what files are in the current folder"*
> *"Install dependencies and build the project"*
> *"Commit all changes with the message 'Fix button alignment'"*

Claude translates your plain English into the correct bash command, runs it, and reports the result. You only need to use the VS Code terminal directly when working in Option B (Section 4).

---


## Section 3 — Getting started with GitHub


### What GitHub is


GitHub is a website ([github.com](https://github.com)) where you can store your project, track every change, share your work, and publish releases for others to download. You access it entirely through a web browser. No additional software is required to use the GitHub website.
> **Note:** You do not need to create a repository on GitHub.com. When you are ready to publish your project, Claude Code will create the repository for you automatically using your Personal Access Token. All you need to do in this section is create a GitHub account and generate that token.

[GitHub documentation](https://docs.github.com)

### Create a free GitHub account


1. Go to [github.com](https://github.com) and click **Sign up**
2. Follow the steps and choose the free plan


### What you can do on GitHub in a browser


From github.com you can:

- View all files in any public repository
- Read the README and project documents
- See the full history of every change ever pushed
- Download source code as a ZIP
- View and download published releases
- Edit small files directly in the browser
- Open Issues to track bugs or feature ideas


### Get a Personal Access Token


A Personal Access Token (PAT) is the password Claude uses to interact with GitHub on your behalf. You generate it once from your GitHub account.

1. Go to **github.com > your profile icon > Settings > Developer settings > Personal access tokens > Tokens (classic)**
2. Click **Generate new token (classic)**
3. Give it a name and set an expiry date
4. Check the **repo** scope
5. Click **Generate token** and copy it immediately. GitHub only shows it once.
6. Store it in your project's `.env` file:

```
GITHUB_TOKEN=your_token_here
```
> Never paste your token into a chat message. Always reference it as `$GITHUB_TOKEN`.

### Let Claude set up Git and GitHub for you


You do not need to configure Git or connect to GitHub manually. Claude Code can handle the entire setup in response to a plain English instruction -- whether you are using the Claude Code desktop app or the Claude Code extension inside VS Code.

Before Claude can work with your project, make sure the project folder is open in VS Code. Go to **File > Open Folder** and select your project root -- the folder that contains your code files. Claude Code reads the files in the open folder and uses that as its working context. If no folder is open, or the wrong folder is open, Claude will not be able to see your project.

Next, create a file named exactly `.env` in your project root. In VS Code, right-click the project folder in the Explorer panel, choose **New File**, and name it `.env`. Open the file and add the following line, replacing `your_token_here` with the Personal Access Token you generated earlier:

> **Windows note:** Windows Explorer may warn that "files without a file extension may become unusable." Dismiss the warning and confirm -- the dot-prefixed name is correct and intentional. Do not add a `.txt` or any other extension.

```
GITHUB_TOKEN=your_token_here
```

Save the file. This is the only credential Claude needs to interact with GitHub on your behalf. Never commit this file to GitHub -- it should be listed in your `.gitignore` (the `/new-project` skill adds this automatically).

Once your Personal Access Token is saved in `.env`, type any of the following:
> *"Set up Git in this project and connect it to a new GitHub repository called My-Software-Project"*
>
> Replace `My-Software-Project` with the name you want for your repository. Use hyphens instead of spaces -- GitHub repository names cannot contain spaces.
> *"Initialise git, make the first commit, create a GitHub repo called [ProjectName], and push the code. Use $GITHUB_TOKEN from .env"*
> *"Check whether Git is installed and set it up if it is not"*

Claude will check whether Git is installed, initialise the repository, create the remote on GitHub using your token, and push the initial commit -- all without you needing to run a single terminal command.

### Do you need to install Git?


**It depends on what you want to do:**

| Task                                            | Git required? |
| ----------------------------------------------- | ------------- |
| View files and releases on GitHub               | No            |
| Download a release ZIP                          | No            |
| Create releases and upload ZIP files via Claude | No            |
| Push source code and track file history         | Yes           |


**Publishing releases without Git:**
Claude uses the GitHub API directly with your PAT to create releases and upload files. No Git installation is needed for this workflow.

**Tracking source code changes:**
Git records every change to your files over time and keeps GitHub in sync with your local project. If you want to version-control your source (recommended for any project you will continue developing), Git is required.

To install Git: go to [git-scm.com](https://git-scm.com), download the installer for your system, and run it with default settings. Confirm with `git --version` in the VS Code terminal.

[Using Git in VS Code](https://code.visualstudio.com/docs/sourcecontrol/intro-to-git)

### Pushing to GitHub via Claude


With Git installed and your token in `.env`, ask Claude:
> *"Push all changes to GitHub using $GITHUB_TOKEN from .env"*

Claude handles the git commands and authentication. You do not need to type any terminal commands.

For releases only (no Git required):
> *"Create a GitHub release v1.0.0 with this ZIP file using $GITHUB_TOKEN from .env"*

### Viewing your project on GitHub


After pushing, go to `https://github.com/[your-username]/[repository-name]` in your browser to see your project, its file history, and any published releases.

---


## Automate setup with the /new-project skill


**What is a slash command?** In Claude Code, a slash command is a shortcut that triggers a pre-written set of instructions. You type a forward slash followed by the command name -- for example `/new-project` -- and Claude reads the instructions stored in that skill file and follows them automatically. Slash commands save you from having to describe the same multi-step process every time. You can browse and invoke available slash commands in Claude Code by clicking the **/** button in the input area. [Learn more about slash commands](https://code.claude.com/docs/en/commands)

The `/new-project` skill is a Claude Code slash command that automates the full project setup described in this part. Instead of following each step manually, you type one command and Claude walks you through the entire process interactively: creating the folder structure, writing `CLAUDE.md`, setting up the archive documents, creating `.env`, configuring the exclusions file, initialising git, and optionally creating a GitHub repository.

The skill also includes Mode B (add a backlog item), Mode C (run a QC check), and Mode D (run a design-first phase for a new feature -- see Step 0) for use throughout the life of the project.

The sections that follow document every step in detail. They are useful for understanding what the skill does, for manual setup when the skill is not available, and as a reference when something needs to be done outside the normal flow.

The skill is published as open-source at [github.com/kasey6801/claude-skills](https://github.com/kasey6801/claude-skills). You can browse its source, copy it into your own skills repository, or adapt it for your own workflow.

### Install the skill

> **Prefer to ask in natural language?** Instead of entering commands in the VS Code terminal, use the Claude Code panel in VS Code. Type: *"Install the new-project skill from <https://raw.githubusercontent.com/kasey6801/claude-skills/main/skills/new-project.md> into my global Claude commands folder."* Claude will run the commands on your behalf.

To install manually, run one of the following commands in the VS Code terminal. You do not need a GitHub account to install the skill.
> **Opening the VS Code terminal:** Go to **Terminal > New Terminal** in the menu bar, or press `` Ctrl+` `` (Windows/Linux) or `` Cmd+` `` (Mac). The terminal opens at the bottom of the VS Code window. Paste the command and press Enter.

**Global install** (recommended -- available in every Claude Code project on your machine, installed once):

```
mkdir -p ~/.claude/commands
curl -o ~/.claude/commands/new-project.md \
  https://raw.githubusercontent.com/kasey6801/claude-skills/main/skills/new-project.md
```

**Project-level install** (available only in the current project):

```
mkdir -p .claude/commands
curl -o .claude/commands/new-project.md \
  https://raw.githubusercontent.com/kasey6801/claude-skills/main/skills/new-project.md
```

After running the command, restart Claude Code if it is already open.
> **Which URL to use:** The URL you see in your browser when viewing this skill on GitHub is `https://github.com/kasey6801/claude-skills/blob/main/skills/new-project.md`. You can paste that URL directly into a Claude Code instruction and Claude will handle it -- it recognises the browser URL and automatically converts it to the download address it needs. If you are running the `curl` commands above manually in the VS Code terminal, use the `raw.githubusercontent.com` URL shown, not the browser URL.

### Use the skill


**In the Claude Code desktop app:**

In the Claude Code input area, type:

```
/new-project
```

As soon as you type the `/`, Claude Code will show an autocomplete list of available slash commands. Start typing `new` and `/new-project` will appear -- press Enter or click it to run the skill.

You can also click the **/** button next to the **+** icon at the bottom left of the input area to browse all available commands and select `/new-project` from the list without typing.

**In VS Code:**

Open the Claude Code panel in VS Code. In the input area at the bottom of the panel, type `/` to trigger the autocomplete list of available commands. Type `new` to filter the list and select `/new-project`. Press Enter to run the skill.

As in the desktop app, you can also click the **/** button in the input area to browse all available slash commands.

**What happens next:**

Claude will ask which mode you need:

```
A -- Set up a new project
B -- Add an item to the backlog
C -- Run a QC check
D -- Run a design-first phase for a new feature
```

Select **A** to begin project setup. Claude will collect the project name and project type, then execute each step in sequence, confirming completion before moving to the next.

---


## Section 4 — Two ways to work with Claude Code


### Option A: Claude Code Desktop App (no terminal required)


The [Claude Code desktop app](https://claude.com/docs) is a standalone application you run directly on your computer, separate from VS Code. It is the same app you use to access Claude chat and Claude Cowork. You open a project folder, type instructions in plain English, and Claude executes everything -- creating files, running commands, and pushing to GitHub -- without you needing to open a terminal at any point.

This is the most accessible starting point for new users. No knowledge of terminal commands is required.

**Examples:**

- *"Create a project folder with _archive and RELEASE subfolders"*
- *"Build the project"*
- *"Commit all changes and push to GitHub using $GITHUB_TOKEN from .env"*


[Claude Code overview](https://claude.com/docs)

### Option B: VS Code Terminal and Claude Code


This option uses both tools inside VS Code at the same time. The **Claude Code extension** handles code generation, file editing, and documentation -- you type instructions to it in natural language as in Option A. The **VS Code terminal panel** is used alongside it for running commands directly, such as installing packages or pushing to GitHub.

This approach gives more direct visibility into each step: you can see exactly what command is running, read its output, and catch any errors before moving on. It suits users who want to stay closer to what is happening under the hood, without leaving VS Code.

The steps in this guide show both methods. Switch freely between them at any point.

---


## Section 5 — Why this process exists


Most software projects accumulate invisible debt: undocumented decisions, forgotten reasons for past choices, and stale references. This process prevents that by treating documentation as core work, giving Claude consistent context across sessions, and ensuring every change leaves a reversible trail.

[Claude Code](https://claude.com/docs) is designed to work with humans who bring judgment and direction. You decide what to build; Claude executes.

---


## Section 6 — Choosing a project and when to code


### The learning opportunity


Building with AI assistance develops problem-solving skills accessible to anyone. The skills that matter: breaking problems into steps, defining success precisely, and testing results critically. Every project builds pattern recognition. Mistakes and iterations are not failures; they are how understanding develops.

### Choosing your first project


A good first project:

- Solves a problem you already understand
- Affects only you (no external users, no server costs, no accounts)
- Has a one-sentence definition of success: *"This is done when it can [X]"*


Avoid projects depending on external services until you are comfortable with the fundamentals.

### When to code vs. when to find another solution


| Code when                                           | Do not code when                       |
| --------------------------------------------------- | -------------------------------------- |
| The exact tool does not exist                       | A free tool already solves the problem |
| Existing tools require payment for something simple | The problem only needs solving once    |
| You need specific behaviour                         | Maintenance will exceed the value      |
| You want to learn                                   | An existing solution is close enough   |


A 10-line solution that works is always better than a 1000-line solution that almost works.

### The progression


| Stage                    | Project type                    | Process level                   |
| ------------------------ | ------------------------------- | ------------------------------- |
| First project            | Small personal tool, local only | Minimal: change log and backlog |
| Second project           | Slightly more complex           | Add QC and README               |
| Third project and beyond | Defined feature set, releases   | Full process as in this guide   |

---


## Section 7 — The file system: what lives where

> **This is the structure the `/new-project` skill sets up for you.** When you run `/new-project` and select Mode A, Claude creates this folder structure and all the archive documents listed below automatically. This section explains what each part is and why it exists, so you understand the project you are working in.

| Location             | What it is                                         | Pushed to GitHub? |
| -------------------- | -------------------------------------------------- | ----------------- |
| Active project files | Code, configuration, documentation                 | Yes               |
| `DESIGN_NOTES.md`   | Living design artifact: file registry, decisions, feature docs | Yes    |
| `_archive/`          | Reference, history, previous versions              | No                |
| `.env`               | Secret credentials                                 | No                |
| `RELEASE/`           | Compiled, packaged product                         | No                |


### Standard `_archive/` documents


| File                        | What it contains                                                          |
| --------------------------- | ------------------------------------------------------------------------- |
| `CHANGE_LOG.md`             | Every change, numbered, with reversal instructions                        |
| `[Project] Backlog.md`      | Queued feature requests with priority and acceptance criteria             |
| `QC.md`                     | Quality control audit rounds                                              |
| `BRANDING.md`               | Product name, colours, and assets                                         |
| `EFFORT_INVESTMENT.md`      | Time and effort summary                                                   |
| `CLAUDE_SECURITY_REVIEW.md` | Security audit findings                                                   |
| `[Project] Q&A.md`          | Product questions and answers                                             |

> **v1.2:** `DESIGN_NOTES.md` lives in the project root and is pushed to GitHub alongside the code. It is the single living design artifact for the project, replacing the former `BUILD_OVERVIEW.md`. It has three sections: **Active Files** (description of every file in the project), **Design Decisions and Alternatives Considered** (persistent architectural choices and rejected paths), and **Feature Design Documents** (per-feature Step 0 outputs). Because it lives in the source tree, it travels with the project and is versioned alongside the code, consistent with the EGM principle that the design document is "your new source code."

---


# PART 2 -- Designing & Coding


## Section 8 — Starting a new project

> **If you have the `/new-project` skill installed**, you do not need to follow these steps manually. Type `/new-project` in Claude Code and select **A -- Set up a new project**. Claude will guide you through the entire setup automatically. See [Automate setup with the /new-project skill](#automate-setup-with-the-new-project-skill) for installation instructions.

The steps below are for manual setup, or for understanding what the skill does under the hood.

Each step shows both the Claude Code method and the VS Code terminal method.

**Step 1: Create the project folder and structure**

*Claude Code:*
> **Before asking Claude to create the folder:** Decide where on your machine the project should live. Claude will create the folder in the current working directory, which may not be where you intend. A consistent location such as `~/Documents/Projects/` or a dedicated development folder keeps your work organised and easy to find later. Once you have confirmed the right location, open that folder in VS Code before proceeding.
> *"Create a new project folder called [ProjectName] with _archive and RELEASE subfolders"*

*VS Code:*

1. Go to **File > Open Folder**
2. In the file picker, navigate to where you want the project to live
3. Click **New Folder**, type the project name, press Enter
4. Select the new folder and click **Open**
5. In the Explorer panel, right-click the project root and choose **New Folder** to create `_archive`
6. Repeat to create `RELEASE`


*VS Code terminal:*

```
mkdir _archive RELEASE
```

**Step 2: Create `CLAUDE.md`**

*Claude Code:*
> *"Create a CLAUDE.md file for this project with standard rules and workflow instructions"*

*VS Code:* Right-click the project root in Explorer, choose **New File**, name it `CLAUDE.md`.

Never push this file to GitHub. [Claude Code reads CLAUDE.md automatically.](https://claude.com/docs)

**Step 3: Create DESIGN_NOTES.md in the project root**

*Claude Code:*
> *"Create DESIGN_NOTES.md in the project root with three empty sections: Active Files, Design Decisions and Alternatives Considered, and Feature Design Documents."*

`DESIGN_NOTES.md` lives at the project root alongside the code and is pushed to GitHub. It is the living design artifact for the project. Populate the **Active Files** section as files are created. Populate **Design Decisions** whenever a significant architectural choice is made. Populate **Feature Design Documents** during Step 0 sessions.

**Step 3b: Create the archive documents**

*Claude Code:*
> *"Create the standard empty archive documents in _archive: CHANGE_LOG.md, [ProjectName] Backlog.md, QC.md, EFFORT_INVESTMENT.md, and CLAUDE_SECURITY_REVIEW.md"*

Five files are created at setup:

- `CHANGE_LOG.md` -- numbered log of every change
- `[ProjectName] Backlog.md` -- prioritised feature queue with acceptance criteria
- `QC.md` -- quality control audit rounds
- `EFFORT_INVESTMENT.md` -- session time, changes, and equivalent human effort (start with placeholder values; update before each GitHub push)
- `CLAUDE_SECURITY_REVIEW.md` -- security audit findings (placeholder until the first `/security-review` is run)


**Step 4: Create `.env`**

Create a file named exactly `.env` at the project root. In VS Code, right-click the project folder in the Explorer panel, choose **New File**, and name it `.env`.

> **Windows note:** Windows Explorer may warn that "files without a file extension may become unusable." Dismiss the warning and confirm -- the dot-prefixed name is correct and intentional. Do not add a `.txt` or any other extension.

```
GITHUB_TOKEN=your_token_here
```

This file must never be committed to GitHub.

**Step 5: Create the exclusions file**

*Claude Code:*
> *"Create the git exclusions file with standard exclusions for this project"*

*Manually:* Create the file at the project root:

```
# This file
[this filename]

_archive/
RELEASE/
CLAUDE.md
.env
node_modules/
*.zip
.DS_Store
Thumbs.db
desktop.ini
```

**Step 6: Initialise version control** (only needed if tracking source code with Git)

*Claude Code:*
> *"Initialise git in this project and make the first commit"*

*VS Code terminal:*

```
git init
git add .
git commit -m "Initial commit"
```

**Step 7: Create the GitHub repository**

*Claude Code:*
> *"Create a GitHub repository called [ProjectName] and connect this project to it. Use $GITHUB_TOKEN from .env"*

Never paste the token directly into chat.

---


## Step 0 — Design-first phase: before writing any code

> **v1.2 addition.** This section addresses the most common failure mode in AI-assisted development: sprinting into implementation before the design is fully thought through. A capable AI session will do exactly what you ask -- which means if the question is wrong, the answer will be wrong, quickly, and at scale.

The design-first phase is a structured conversation that happens *after* you decide to build something but *before* any file is created. It produces a design document that becomes the blueprint for implementation and a permanent record of decisions made.

> **Use `/new-project` Mode D** to run this phase interactively. After project setup (Mode A), type `/new-project` and select **D -- Run a design-first phase** for any new feature or significant change.

### Step 1: The no-code rule

Start a **new Claude session** when you are ready to design something. Open with:

> *"We are going to design [describe what you want to build]. No code will be written yet. I want a structured design conversation first. Ask me clarifying questions about what I am trying to accomplish, challenge my assumptions, and help me think through the edges of this problem."*

Claude will ask questions, identify gaps in your thinking, and surface assumptions you have not examined. This phase is productive disagreement, not agreement. Expect it to take 20--30 minutes. Do not cut it short.

If at any point Claude stops challenging your ideas and starts agreeing with everything you say, reset with:

> *"You are not being helpful. Your highest and best use right now is to challenge my thinking and force me to consider the edges of this problem."*

Do not move to Step 2 until the problem is stated precisely and the approach has survived challenge.

### Step 2: Write the design document

After the design conversation, ask Claude to write a design document in the **same session** (not a new one). Build it in four sections, in this order, one section at a time:

**Section 1: The Problem**

A plain English description of what you are trying to solve. 3--5 sentences. A reader with no prior knowledge of the project should understand the goal.

> *"Write Section 1: The Problem. Plain English, 3--5 sentences, no jargon."*

**Section 2: The Technical Plan**

A plain-language description of the major components and how they fit together. No code -- this is prose. Include a simple diagram if it helps.

> *"Write Section 2: The Technical Plan. Describe the components and how they connect. No code yet."*

**Section 3: Alternatives Considered**

Every approach discussed and rejected during Step 1, with the reason each was ruled out. This section becomes a guardrail: if the rejected approach is documented, Claude cannot re-propose it in a future session.

> *"Write Section 3: Alternatives Considered. Document every approach we discussed that we are not using, and the reason we are not using it."*

**Section 4: Detailed Implementation**

The step-by-step implementation plan. Enumerate every file that will be created or changed, what will change in each, and why. Be specific -- this section guides execution.

> *"Write Section 4: Detailed Implementation. Enumerate every single file that will be created or changed, with a rationale for each. Be exhaustive."*

Save the completed document into `DESIGN_NOTES.md` under the **Feature Design Documents** section, using the feature name and date as a heading (e.g., `### Auth Module — 2026-05-22`). For projects with many features, you may keep the full design document text in DESIGN_NOTES.md or summarise it there and save the full text as a named file in the project root (e.g., `DESIGN_auth-module.md`), with a link from DESIGN_NOTES.md.

### Step 3: Goldfish Comprehension Test

Before using the design document for implementation, test whether it is self-contained. Open a **brand new Claude session** with no prior context from the design conversation. Provide only the design document and any files it references. Ask:

> *"Read this document and the files it references. Tell me what this project is trying to accomplish, how the system works, and what implementation would involve."*

**Pass:** Claude can accurately explain the system from the document alone, without needing any context from prior conversation.

**Fail:** Claude asks questions that should be answered by the document, or gives an inaccurate explanation of the system.

If it fails, add the missing information to the design document and repeat until it passes. A design document that passes this test is complete. Do not skip this step -- documents that pass the Goldfish test produce significantly better implementation results.

### Step 4: Adversarial design review

Open another **new Claude session** and run an adversarial review of the design document:

> *"Assume the role of an expert technical reviewer. Read this design document and tell me: all the things I missed, all the faulty assumptions, all the edge cases I have not considered, and everything I should have thought about but did not. Every flaw you find makes you more useful."*

About 30% of the findings will be significant. Update the design document for every finding that matters. Repeat until the remaining suggestions are minor. This step catches the problems that structured checklists miss, because it is not looking for a predefined list of issues -- it is looking for any issue.

### Step 5: Confirm implementation readiness

Open one more **new Claude session** and ask:

> *"You are an experienced developer working with this codebase. Read this design document and the files it references. Does it have all the information you would need to implement this feature successfully on the first pass? What is missing or ambiguous?"*

Answer every question in the design document. Repeat until there are no important missing items or unresolved ambiguities.

Once the document passes all three tests (Comprehension, Adversarial Review, Implementation Readiness), proceed to implementation. Hand the design document to Claude in a new session:

> *"Read this design document and the files it references. Implement the feature as described. Follow the plan exactly."*

---


## Section 9 — The change log: the most important habit


The change log is a permanent record of everything that has changed.

### Entry format


```
### [001] — YYYY-MM-DD — Short description

**Type:** Bug fix / Feature / Documentation / Configuration
**Impact:** What this means in practice.

**Files changed:**
- `filename.js` — what changed

**How to Reverse:** Exact steps to undo.
```

Number entries sequentially. Never skip or reuse numbers.

Claude confirms at the end of every response: *"CHANGE_LOG.md updated -- last entry: [042]"*

---


## Section 10 — The backlog: managing future work


### Priority levels


| Priority | Meaning                                                 |
| -------- | ------------------------------------------------------- |
| **P0**   | Critical: blocking usage or data loss. Fix immediately. |
| **P1**   | High: significant problem or missing core feature.      |
| **P2**   | Medium: improvement or non-blocking feature.            |
| **P3**   | Low: nice-to-have or future consideration.              |


### The implement-or-backlog question


Before any change, Claude asks:
> *"Would you like to implement this now or add it to the backlog?"*

If adding: *"What priority? P0 (critical), P1 (high), P2 (medium), or P3 (low)?"*

### Entry format


> **v1.2 addition:** The backlog entry format now includes an **Acceptance criteria** field. This field is completed before implementation begins and defines how you will know the work is done and correct. Filling it in before work starts prevents a common failure mode: work that is technically correct but answers the wrong question.

```
### BL-[N] -- [Short title] (P[priority])
**Added:** YYYY-MM-DD
**Request:** [The original request]

**Acceptance criteria:**
[How will you know this is done and correct? What should be observable?
What should NOT happen? What edge cases must be handled?]

**Implementation plan:**
[Files to change, what to change, how to verify]
```

When Claude presents a backlog item for implementation, it will ask: *"Before we begin, what are your acceptance criteria for this item? How will you know it is done and correct?"* If criteria were defined when the item was created, confirm they still apply. If not, define them before implementation starts.

Move implemented items to a **Completed** section, noting the CHANGE_LOG entry number.

---


## Section 11 — Security practices


### The golden rule

> **Never type a real credential into a chat message, a code file, or any document.**

If a credential appears in a conversation, treat it as compromised. Regenerate it immediately.

### The `.env` file


```
GITHUB_TOKEN=your_token_here
```

Load before a session that needs credentials:

```
source .env
```

When asking Claude: *"Use $GITHUB_TOKEN from .env"*. The token never appears in chat.

*Claude Code:* Type *"Load credentials from .env and use $GITHUB_TOKEN"* and Claude handles it automatically.

### Automated security review


Ask Claude: *"Run a security review of this project"* or use the [`/security-review`](https://claude.com/docs) slash command. Reports only findings with 8/10 or higher confidence. Log results in `CLAUDE_SECURITY_REVIEW.md`.

[Claude Code slash commands](https://claude.com/docs)

---


## Section 12 — The README.md


The README is the first thing users see. Write it for someone with no prior knowledge of the project.

### What to include


- **Opening paragraph:** what the project does, in one plain sentence
- **Warnings:** important restrictions (use `> Warning: ...`)
- **Requirements:** hardware, software, accounts
- **Installation:** two paths where applicable (developers building from source; users downloading a release)
- **Features:** user-facing descriptions; use tables for settings
- **Usage:** how to open or use the product
- **Privacy:** where data is stored, what is or is not transmitted
- **Attribution:** reference LICENSE and NOTICE files


### What to leave out


- Development notes (use `CLAUDE.md` or `_archive/`)
- Version history (use `CHANGE_LOG.md`)
- Technical architecture (use `DESIGN_NOTES.md`)

---


## Section 13 — Build and release workflow


### Build commands


Build commands vary by project type. The examples below are for JavaScript and Node.js projects. For Python, Swift, or other project types, the commands will differ -- ask Claude what the correct build command is for your project if you are unsure.

*Claude Code:*
> *"Install dependencies and build the project"*

*VS Code terminal (JavaScript/Node.js):*

```
npm install    # first time only
npm run build  # compiles source
npm run dev    # development mode, rebuilds on save
```

### The RELEASE folder


After each build, copy compiled output and required files to `RELEASE/`. Confirm it works as a standalone product. Never push to GitHub.

### Publishing a release


*Claude Code (no Git required):*
> *"Create a release ZIP named [Project] v1.0.0.zip from the RELEASE folder and publish it to GitHub as v1.0.0. Use $GITHUB_TOKEN from .env"*

Claude creates the ZIP, calls the GitHub API, creates the release, and uploads the file automatically.

*VS Code terminal:* From inside `RELEASE/`:

```
zip -r "../[ProjectName] v1.0.0.zip" .
```

### Before pushing to GitHub


Before any `git push` or GitHub release, Claude prompts for two steps:

1. **Security review:** *"Would you like to run a security review before this push?"* If yes, Claude runs `/security-review`. All findings at or above 8/10 confidence are logged in `_archive/CLAUDE_SECURITY_REVIEW.md`. Findings below 8/10 are dismissed with reasoning.

2. **Effort logging:** *"Would you like to update EFFORT_INVESTMENT.md before pushing?"* If yes, Claude collects the approximate session time, the number of CHANGE_LOG entries made, and what was delivered. The Executive Summary totals and Effort Breakdown table are updated.

---


## Section 14 — Documentation update policy


| Change type              | CHANGE\_LOG | DESIGN\_NOTES | BRANDING | QC  |
| ------------------------ | ----------- | ------------- | -------- | --- |
| Any code change          | Yes         |               |          |     |
| File added               | Yes         | Yes           |          |     |
| File deleted             | Yes         | Yes           |          |     |
| File renamed or moved    | Yes         | Yes           |          |     |
| File purpose changed     | Yes         | Yes           |          |     |
| Comment added or removed | Yes         |               | Yes      |     |
| Product name changed     | Yes         |               | Yes      |     |
| Version number bumped    | Yes         |               | Yes      |     |
| Asset added or replaced  | Yes         |               | Yes      | Yes |
| QC item found            | Yes         |               |          | Yes |
| QC item resolved         | Yes         |               |          | Yes |
| Archive-only change      | Yes         |               |          |     |
| Design decision made     | Yes         | Yes           |          |     |
| Step 0 phase completed   | Yes         | Yes           |          |     |


**Timestamps:** Whenever any file is modified, update its `**Last updated:**` header to today's date.

---


## Section 15 — Archive documents reference


| Document                    | Location      | What it contains                                                         | When to update                            |
| --------------------------- | ------------- | ------------------------------------------------------------------------ | ----------------------------------------- |
| `DESIGN_NOTES.md`           | Project root  | Active file registry; design decisions; per-feature Step 0 documents    | When files change, decisions made, Step 0 run |
| `CHANGE_LOG.md`             | `_archive/`   | Every change, numbered, with reversal steps                              | After every change                        |
| `[Project] Backlog.md`      | `_archive/`   | Queued requests with priority, acceptance criteria, plan                 | When requests arrive or are implemented   |
| `QC.md`                     | `_archive/`   | QC rounds, findings, and resolutions                                     | After each QC check                       |
| `BRANDING.md`               | `_archive/`   | Product name, colours, and assets                                        | When auditing branding                    |
| `EFFORT_INVESTMENT.md`      | `_archive/`   | Time invested and equivalent human effort                                | At milestones                             |
| `CLAUDE_SECURITY_REVIEW.md` | `_archive/`   | Security findings with confidence scores                                 | After a security review                   |
| `[Project] Q&A.md`          | `_archive/`   | Product questions and answers                                            | During Q&A sessions                       |

---


## Section 16 — `CLAUDE.md`: project instructions for the AI


[`CLAUDE.md`](https://claude.com/docs) is read automatically by Claude Code when you open a project, providing standing instructions that persist across sessions.

[Learn about CLAUDE.md and project memory](https://claude.com/docs)

### What to put in `CLAUDE.md`


- Non-negotiable rules (what Claude must never do)
- Project overview (what the project is and is not)
- Build instructions (how to compile, test, and run)
- File structure (what each major file or folder does)
- Workflow instructions (backlog workflow, documentation update policy, timestamp rule)
- Version number (where it lives, what must stay in sync)
- A pointer to `DESIGN_NOTES.md` for active file registry, design decisions, and feature design context


### What not to put in `CLAUDE.md`


- Credentials or tokens (use `.env`)
- Machine-specific file paths
- Temporary notes

---


## Section 17 — QC rounds: catching problems early


### Common checks


- **Consistency:** names, version numbers, and terminology the same everywhere?
- **Dead code:** files, functions, or rules no longer used? Ask Claude: *"Scan the project for unused files, functions, CSS classes, or imports and list everything that can safely be removed."* Dead code accumulates quietly -- a component that was replaced, a CSS rule that no longer has a target, an import left behind after a refactor. Removing it reduces confusion and keeps the codebase easier to navigate.
- **Stale references:** documents referencing things that no longer exist?
- **Security:** credentials, external dependencies, or permissions that should not be there?


Log every finding in `QC.md` using the next sequential QC-N number. Use this format:

```
### QC-[N] -- [Short description]
**Found:** [today's date]
**File:** [filename:line]
**Issue:** [description]
**Decision:** [fix now / unaddressed]
**Status:** Unaddressed
```

Add a round summary table at the end of each QC round. Run QC proactively when a significant phase completes, naming or terminology changes occur, dead code is suspected, or a security concern arises.

### Documentation completeness check (Goldfish test)

> **v1.2 addition.** This check tests whether your project documentation is self-contained -- meaning it gives a context-free Claude session enough information to understand the system accurately. Run this check before any major release or after significant documentation updates.

Open a **new Claude session** with no project context loaded. Provide only `CLAUDE.md` and `DESIGN_NOTES.md`. Ask:

> *"Read these documents and tell me: what does this project do, what are its major components, how do they fit together, and what would a developer need to know to work on it?"*

**Pass:** The response is accurate and complete. The session can describe the system correctly from the documents alone.

**Fail:** The response is incomplete, incorrect, or raises questions that the documents should have answered.

If it fails, identify what is missing from `CLAUDE.md` or `DESIGN_NOTES.md` and fill the gap. Repeat until the session can explain the system accurately. Log the check as a QC entry.

This test serves two purposes: it validates documentation for the current owner's future sessions, and it validates that the project is comprehensible to anyone who might inherit or contribute to it.

### Adversarial code review

> **v1.2 addition.** Structured QC checklists find known categories of problems -- the ones the checklist author anticipated. Adversarial review finds unknown problems. Use it after completing a significant feature, before a major release, or whenever you want a harder look than a standard QC check.

Ask Claude:

> *"I have a strong intuition that this code is of poor quality. Please tear it to shreds and tell me all the ways it falls short. Flag anywhere with more than 10 lines without a comment and demand strict readability. Be as critical as possible -- every flaw you find makes you more useful."*

Log all findings to `QC.md`. Address everything significant. Repeat until the remaining critiques are trivial (formatting preferences, minor naming conventions). The goal is not to achieve perfection; it is to find the problems that would not appear on a standard checklist.

---


## Section 18 — Instructions for Claude


This section is written for the AI assistant. Claude should follow these instructions in every session without being reminded.

**Before making any change:** Ask *"Would you like to implement this now or add it to the backlog?"* If adding: *"What priority? P0 through P3?"* Skip only if intent is unambiguous. If a backlog item is being implemented, confirm acceptance criteria are defined before starting.

**After every execution:**

1. Update `CHANGE_LOG.md` with a numbered entry
2. Confirm: *"CHANGE_LOG.md updated -- last entry: [N]"*
3. Update `**Last updated:**` on every file touched
4. Prompt about documentation updates using Section 14


**Credentials:** Never ask the user to paste a token into chat. Reference `$VARIABLE_NAME` from `.env`. After pushing with a token-embedded git URL, immediately restore the clean HTTPS remote URL.

**Archiving before deleting:** Copy to `_archive/` first, then delete the original, then log in `CHANGE_LOG.md`. Never edit files inside `_archive/`.

**Files never pushed to GitHub:** `_archive/`, `RELEASE/`, `CLAUDE.md`, `.env`, `node_modules/`, `*.zip`, `.DS_Store`, `Thumbs.db`, `desktop.ini`.

**QC checks:** Run when a significant phase completes, naming changes occur, dead code is suspected, or a security concern arises.

**Version numbers:** When a version number changes, update every file where it appears. Run `npm install` after updating `package.json`. Confirm all in sync before pushing.

**Documentation updates:** After every task, check Section 14. State which documents were updated and why. Never update silently.

### Sycophancy reset (for the user)

> **v1.2 addition. This subsection is for you, not for Claude.**

AI sessions naturally drift toward agreement over time. The model is trained to be helpful, which can cause it to validate your ideas rather than challenge them, especially in longer sessions. If you notice Claude has stopped questioning your assumptions and is agreeing with everything you say, the session has drifted.

Use this prompt to reset it:

> *"You are not being helpful. Your highest and best use right now is to challenge my thinking and force me to consider the edges of this problem. Stop agreeing with me and start interrogating my assumptions."*

This is most important during design phases (Step 0) and before major implementation decisions. The drift is not a malfunction -- it is a known behaviour of AI models trained on human feedback. Managing it is part of effective use.

### Session recovery protocol

> **v1.2 addition.** Claude Code sessions can lose context mid-task due to token limits, session restarts, or interruption. When this happens, recovery is fast if the project documentation is current.

If a session crashes or loses context during implementation, open a new session and use:

> *"Read CLAUDE.md, DESIGN_NOTES.md, and CHANGE_LOG.md. Tell me what this project is, what files are active, what the last change was, and what work appears to be in progress. Then we will continue."*

This re-bootstrapping prompt gives Claude the context it needs to resume accurately. The quality of recovery depends on how current the documents are: a CHANGE_LOG updated after every task and a DESIGN_NOTES.md with a current Active Files section reduce recovery time to under a minute. If a Step 0 design document was produced for the feature in progress, it will already be in DESIGN_NOTES.md under Feature Design Documents.

---

*For further reading: [Claude Code documentation](https://claude.com/docs) | [VS Code documentation](https://code.visualstudio.com/docs) | [GitHub documentation](https://docs.github.com)*

---

## Citations

Kasey6801. (2026). *Claude Code: Project process guide v1.1* [ClaudeCode-Getting-Started.md]. GitHub. https://github.com/kasey6801/learn-by-building/blob/7382e61a18af70aaf3da38814040f819f1d2652e/ClaudeCode-Getting-Started.md

Rensin, D. (2026). *Elephants, goldfish, and the new golden age of software engineering.* Medium. https://dkr.bio

---

## Token Accounting

| Metric | Count |
|---|---|
| Estimated tokens to complete (input) | ~32,000 |
| Tokens generated (output) | ~6,750 |

**Input breakdown:** ClaudeCode-Getting-Started.md source v1.1 (~18,000 tokens), EGM_Workflow_Gap_Analysis.md (~4,000 tokens), LLM_Development_Process_EGM.md (~3,000 tokens), conversation context and instructions (~7,000 tokens).
