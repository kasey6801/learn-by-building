# Claude Code: Project Process Guide
### A structured development process for AI-assisted software projects using VS Code and Claude Code

**Version:** 1.1
**Last Updated:** 2026-05-20  
**Audience:** This document has been designed to assist those new to software development. 
**Primary tools:** [Visual Studio Code](https://code.visualstudio.com) and [Claude Code](https://claude.com/docs)  
**Purpose:** A reusable, step-by-step process for setting up and running software projects, from installing VS Code to publishing a release on GitHub.

---

## Table of Contents

- [PART 1 - Overview and Foundational Information](#part-1--overview-and-foundational-information)
  - [Section 1 - Getting started with VS Code](#section-1--getting-started-with-vs-code)
    - [Install VS Code](#install-vs-code)
    - [The VS Code interface](#the-vs-code-interface)
    - [Install the Claude Code extension](#install-the-claude-code-extension)
    - [Install Node.js](#install-nodejs)
  - [Section 2 - Understanding the terminal and bash commands](#section-2--understanding-the-terminal-and-bash-commands)
    - [Navigation](#navigation)
    - [Files and folders](#files-and-folders)
    - [Searching and editing text](#searching-and-editing-text)
    - [Node.js and project packages](#nodejs-and-project-packages)
    - [Git commands](#git-commands)
    - [Environment and credentials](#environment-and-credentials)
    - [HTTP requests and APIs](#http-requests-and-apis)
    - [Python](#python)
    - [Checking installations](#checking-installations)
    - [A note on using these with Claude](#a-note-on-using-these-with-claude)
  - [Section 3 - Getting started with GitHub](#section-3--getting-started-with-github)
    - [What GitHub is](#what-github-is)
    - [Create a free GitHub account](#create-a-free-github-account)
    - [What you can do on GitHub in a browser](#what-you-can-do-on-github-in-a-browser)
    - [Get a Personal Access Token](#get-a-personal-access-token)
    - [Do you need to install Git?](#do-you-need-to-install-git)
    - [Pushing to GitHub via Claude](#pushing-to-github-via-claude)
    - [Viewing your project on GitHub](#viewing-your-project-on-github)
- [PART 2 - Starting a New Project](#part-2--starting-a-new-project)
  - [Automate setup with the /new-project skill](#automate-setup-with-the-new-project-skill)
  - [Section 4 - Two ways to work with Claude Code](#section-4--two-ways-to-work-with-claude-code)
    - [Option A: Claude Code Desktop App (no terminal required)](#option-a-claude-code-desktop-app-no-terminal-required)
    - [Option B: VS Code Terminal and Claude Code](#option-b-vs-code-terminal-and-claude-code)
  - [Section 5 - Why this process exists](#section-5--why-this-process-exists)
  - [Section 6 - Choosing a project and when to code](#section-6--choosing-a-project-and-when-to-code)
    - [The learning opportunity](#the-learning-opportunity)
    - [Choosing your first project](#choosing-your-first-project)
    - [When to code vs. when to find another solution](#when-to-code-vs-when-to-find-another-solution)
    - [The progression](#the-progression)
  - [Section 7 - The file system: what lives where](#section-7--the-file-system-what-lives-where)
    - [Standard `_archive/` documents](#standard-_archive-documents)
  - [Section 8 - Starting a new project](#section-8--starting-a-new-project)
  - [Section 9 - The change log: the most important habit](#section-9--the-change-log-the-most-important-habit)
    - [Entry format](#entry-format)
  - [Section 10 - The backlog: managing future work](#section-10--the-backlog-managing-future-work)
    - [Priority levels](#priority-levels)
    - [The implement-or-backlog question](#the-implement-or-backlog-question)
    - [Entry format](#entry-format-1)
  - [Section 11 - Security practices](#section-11--security-practices)
    - [The golden rule](#the-golden-rule)
    - [The `.env` file](#the-env-file)
    - [Automated security review](#automated-security-review)
  - [Section 12 - The README.md](#section-12--the-readmemd)
    - [What to include](#what-to-include)
    - [What to leave out](#what-to-leave-out)
  - [Section 13 - Build and release workflow](#section-13--build-and-release-workflow)
    - [Build commands](#build-commands)
    - [The RELEASE folder](#the-release-folder)
    - [Publishing a release](#publishing-a-release)
  - [Section 14 - Documentation update policy](#section-14--documentation-update-policy)
  - [Section 15 - Archive documents reference](#section-15--archive-documents-reference)
  - [Section 16 - `CLAUDE.md`: project instructions for the AI](#section-16--claudemd-project-instructions-for-the-ai)
    - [What to put in `CLAUDE.md`](#what-to-put-in-claudemd)
    - [What not to put in `CLAUDE.md`](#what-not-to-put-in-claudemd)
  - [Section 17 - QC rounds: catching problems early](#section-17--qc-rounds-catching-problems-early)
    - [Common checks](#common-checks)
  - [Section 18 - Instructions for Claude](#section-18--instructions-for-claude)

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

| Panel | Location | Purpose |
|-------|----------|---------|
| Explorer | Left sidebar | Shows your project files and folders |
| Editor | Centre | Where you read and edit files |
| Terminal | Bottom | Command line for running instructions |
| Status bar | Very bottom | Shows current file and project info |

**Opening the terminal panel in VS Code:**
The easiest way for new users is to use the menu bar at the top of the VS Code window: click **Terminal**, then click **New Terminal**. A terminal panel will appear at the bottom of the screen. You can also use the keyboard shortcut `` Ctrl+` `` (Windows/Linux) or `` Cmd+` `` (Mac) once you are comfortable with VS Code.

[VS Code user interface overview](https://code.visualstudio.com/docs/getstarted/userinterface)

### Install the Claude Code extension

1. Click the **Extensions** icon in the left sidebar (four squares) or press `Ctrl+Shift+X` / `Cmd+Shift+X`
2. Search for **Claude Code**
3. Click **Install**
4. Follow the sign-in prompts

[VS Code Extensions](https://code.visualstudio.com/docs/editor/extension-marketplace) | [Claude Code documentation](https://claude.com/docs)

Once installed, open Claude Code from the sidebar. Type instructions in plain English and Claude reads your files, runs commands, and makes changes on your behalf.

### Install Node.js

Node.js lets you run JavaScript outside a browser and install project packages.

1. Go to [nodejs.org](https://nodejs.org) and download the **LTS** version
2. Run the installer
3. Confirm: type `node --version` in the VS Code terminal

---

## Section 2 — Understanding the terminal and bash commands

> **Note on terminology:** Throughout this guide, "terminal" always refers to the **terminal panel built into VS Code**, opened via **Terminal > New Terminal** in the menu bar. This is distinct from any standalone terminal application your operating system may provide. This guide does not cover OS-level terminals -- all terminal instructions here are intended to be run inside VS Code.

VS Code includes a built-in terminal panel -- a text-based interface where you type commands and press Enter to give instructions directly to your computer.

When Claude Code says "run this command" or "type this in the terminal", it is referring to bash -- the language the VS Code terminal uses on macOS and Linux. On Windows, the VS Code terminal uses a similar language.

In most cases you will not type these commands directly. Instead, describe what you want in plain English -- Claude reads your instruction, determines the correct command, and executes it on your behalf. This section is a reference so you can understand what Claude is doing and why, not a list of commands you are expected to learn.

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

| Command | What it does | Example |
|---------|-------------|---------|
| `pwd` | Print the current folder you are in | `pwd` shows `/Users/name/MyProject` |
| `cd foldername` | Move into a folder | `cd src` moves into the src folder |
| `cd ..` | Move up one folder level | `cd ..` moves from src back to the project root |
| `ls` | List files and folders in the current location | `ls` shows what is in the folder |
| `ls -la` | List all files including hidden ones, with details | Shows `.env`, `.gitignore`, and file sizes |

### Files and folders

| Command | What it does | Example |
|---------|-------------|---------|
| `mkdir foldername` | Create a new folder | `mkdir _archive` |
| `touch filename` | Create an empty file | `touch notes.md` |
| `cp source destination` | Copy a file | `cp file.txt backup.txt` |
| `mv source destination` | Move or rename a file | `mv old.txt new.txt` |
| `rm filename` | Delete a file permanently | `rm temp.txt` |
| `zip -r name.zip folder/` | Create a ZIP file from a folder | `zip -r "Release v1.0.zip" RELEASE/` |

### Searching and editing text

These commands search inside files and make text replacements without opening a file editor. Claude uses them frequently when scanning or updating code.

| Command | What it does | Example |
|---------|-------------|---------|
| `grep "word" filename` | Search for a word or phrase inside a file and print every matching line | `grep "error" output.log` finds every line containing the word "error" |
| `grep -rn "word" folder/` | Search recursively through all files in a folder, showing file names and line numbers | `grep -rn "TODO" src/` finds all to-do notes across every source file |
| `grep -i "word" filename` | Same as grep but ignores upper/lower case | `grep -i "welcome" docs/` matches "Welcome", "WELCOME", and "welcome" |
| `grep -v "word" filename` | Print lines that do NOT contain the word | Useful for filtering out unwanted results from a long list |
| `sed 's/old/new/g' filename` | Replace every occurrence of "old" with "new" in a file and print the result | `sed 's/v1.0/v2.0/g' config.txt` updates every version reference |
| `sed -i '' 's/old/new/g' filename` | Replace every occurrence directly inside the file (saves the change) | The `-i ''` part means "edit in place" on macOS |

**When Claude uses grep:** To verify that a word or value appears (or does not appear) across many files at once -- for example, confirming no credentials remain in source code, or checking that all version numbers match.

**When Claude uses sed:** To make the same text replacement in a file without opening an editor -- for example, updating a version number or correcting a spelling across an entire file in one command.

### Node.js and project packages

These commands manage the software packages your project depends on.

| Command | What it does |
|---------|-------------|
| `npm install` | Downloads all packages the project needs (run once when setting up, or after adding new ones) |
| `npm run build` | Compiles the source code into the final output file |
| `npm run dev` | Runs the project in development mode -- rebuilds automatically when you save a file |
| `node --version` | Confirms Node.js is installed and shows the version number |

### Git commands

Git tracks every change to your project files. These commands are the core of that workflow.

| Command | What it does |
|---------|-------------|
| `git init` | Sets up git tracking in the current folder -- run once when starting a project |
| `git status` | Shows which files have changed since the last save point |
| `git add .` | Stages all changed files, preparing them to be saved |
| `git add filename` | Stages a specific file only |
| `git commit -m "message"` | Saves a snapshot of the staged files with a description |
| `git push` | Sends committed changes to GitHub |
| `git pull` | Downloads the latest changes from GitHub to your local machine |
| `git pull --rebase` | Downloads and reapplies local changes on top -- used when GitHub has newer commits |
| `git log` | Shows the history of all commits |
| `git diff` | Shows exactly what has changed line by line |

### Environment and credentials

| Command | What it does |
|---------|-------------|
| `source .env` | Loads credentials from the `.env` file into the current terminal session. Run this before any session that needs to use `$GITHUB_TOKEN` or other stored credentials. |
| `set -a` | Marks all variables for automatic export to child processes. Run before `source .env` so every credential is available to scripts Claude calls. |
| `set +a` | Turns off automatic export. Run after `source .env` to restore normal shell behaviour. |
| `set -e` | Exits the script immediately if any command fails. Used at the top of scripts to catch errors early. |
| `echo $VARIABLE_NAME` | Prints the value of a variable -- useful to confirm a credential loaded correctly (do not share the output) |

Claude's standard credential-loading pattern is `set -a && source .env && set +a`.

### HTTP requests and APIs

An **API** (Application Programming Interface) is a way for one piece of software to talk to another over the internet. When you ask Claude to create a GitHub repository or publish a release, it does not log into the GitHub website the way you would. Instead, it sends a structured message directly to GitHub's API -- a dedicated address that GitHub provides specifically for software to interact with it. GitHub reads the message, performs the action, and sends a response back. The whole exchange happens invisibly in the background.

Think of an API like a drive-through window: you make a specific request in the expected format, and the service fulfils it without you going inside.

**HTTP and HTTPS** are the protocols that govern how data is sent and received over the internet. HTTP (HyperText Transfer Protocol) is the set of rules your browser and other software follow when making requests and receiving responses -- every time you load a web page or call an API, HTTP is the language being spoken. HTTPS is the secure version: the "S" stands for Secure, meaning all data exchanged between your computer and the server is encrypted so it cannot be read if intercepted. Any URL beginning with `https://` is using this encrypted connection. In practice, always use `https://` URLs when making API calls -- they protect your credentials and data in transit.

These commands make network requests from the VS Code terminal. Claude uses them to call APIs (such as the GitHub API) and download files without a browser.

| Command | What it does | Example |
|---------|-------------|---------|
| `curl -s URL` | Fetch the content of a URL silently (no progress bar) | `curl -s https://api.github.com/repos/owner/repo` |
| `curl -s -o filename URL` | Fetch a URL and save the response to a file | `curl -s -o data.json https://api.example.com/data` |
| `curl -s -w "%{http_code}" URL` | Fetch a URL and append the HTTP status code to the output | Returns `200`, `201`, `404` etc. -- used to confirm an API call succeeded |
| `curl -L URL` | Follow redirects automatically | Used when a URL redirects to the real download location |
| `curl -I URL` | Fetch headers only, not the response body | Useful for checking whether a URL exists without downloading it |
| `curl -X METHOD URL` | Send a specific HTTP method (GET, POST, PUT, DELETE) | `curl -X PUT ...` sends a PUT request |
| `curl -H "Name: value" URL` | Add a custom header to the request | `curl -H "Authorization: token $GITHUB_TOKEN" ...` sends an auth token |
| `curl -d '{"key":"value"}' URL` | Send a JSON body with the request | Used with `-X POST` or `-X PUT` to send data to an API |

The full pattern Claude uses for an authenticated GitHub API call:

```bash
curl -s -o response.json -w "%{http_code}" -X PUT \
  -H "Authorization: token $GITHUB_TOKEN" \
  -H "Content-Type: application/json" \
  -d '{"key":"value"}' \
  https://api.github.com/repos/owner/repo/contents/path
```

**When Claude uses curl:** To make GitHub API calls (create files, upload releases, update content), to download files without opening a browser, and to verify whether a URL returns a valid response.

### Python

Python is a general-purpose programming language. Claude uses it to run utility scripts, process data inline, and manage project dependencies.

| Command | What it does | Example |
|---------|-------------|---------|
| `python3 script.py` | Run a Python script | `python3 build.py` |
| `python3 -c "code"` | Run a Python one-liner directly in the VS Code terminal without creating a file | `python3 -c "import json; print(json.load(open('data.json')))"` |
| `python3 -m pip install package` | Install a Python package | `python3 -m pip install Pillow` |
| `python3 -m pip install package -q` | Install quietly -- suppresses most output | Used when Claude installs dependencies mid-script without cluttering the log |
| `python3 -m venv .venv` | Create a virtual environment (an isolated Python install for this project) | Run once when starting a Python project |
| `.venv/bin/python3 script.py` | Run a script using the virtual environment's Python, not the system Python | `.venv/bin/python3 build.py` |
| `.venv/bin/pip install package` | Install a package into the virtual environment | `.venv/bin/pip install Pillow -q` |
| `python3 --version` | Confirm Python is installed and show the version | Returns `Python 3.12.x` |

**When Claude uses python3:** To run build or utility scripts, to process JSON or text data inline with `-c`, and to install packages into virtual environments before a build step.

### Checking installations

| Command | What it does |
|---------|-------------|
| `node --version` | Confirms Node.js is installed |
| `git --version` | Confirms Git is installed |
| `npm --version` | Confirms npm (the package manager for Node.js) is installed |
| `python3 --version` | Confirms Python 3 is installed |

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

| Task | Git required? |
|------|--------------|
| View files and releases on GitHub | No |
| Download a release ZIP | No |
| Create releases and upload ZIP files via Claude | No |
| Push source code and track file history | Yes |

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

# PART 2 -- Starting a New Project

## Automate setup with the /new-project skill

**What is a slash command?** In Claude Code, a slash command is a shortcut that triggers a pre-written set of instructions. You type a forward slash followed by the command name -- for example `/new-project` -- and Claude reads the instructions stored in that skill file and follows them automatically. Slash commands save you from having to describe the same multi-step process every time. You can browse and invoke available slash commands in Claude Code by clicking the **/** button in the input area. [Learn more about slash commands](https://code.claude.com/docs/en/commands)

The `/new-project` skill is a Claude Code slash command that automates the full project setup described in this part. Instead of following each step manually, you type one command and Claude walks you through the entire process interactively: creating the folder structure, writing `CLAUDE.md`, setting up the archive documents, creating `.env`, configuring the exclusions file, initialising git, and optionally creating a GitHub repository.

The skill also includes Mode B (add a backlog item) and Mode C (run a QC check) for use throughout the life of the project.

The sections that follow document every step in detail. They are useful for understanding what the skill does, for manual setup when the skill is not available, and as a reference when something needs to be done outside the normal flow.

The skill is published as open-source at [github.com/kasey6801/claude-skills](https://github.com/kasey6801/claude-skills). You can browse its source, copy it into your own skills repository, or adapt it for your own workflow.

### Install the skill

> **Prefer to ask in natural language?** Instead of entering commands in the VS Code terminal, use the Claude Code panel in VS Code. Type: *"Install the new-project skill from https://raw.githubusercontent.com/kasey6801/claude-skills/main/skills/new-project.md into my global Claude commands folder."* Claude will run the commands on your behalf.

To install manually, run one of the following commands in the VS Code terminal. You do not need a GitHub account to install the skill.

> **Opening the VS Code terminal:** Go to **Terminal > New Terminal** in the menu bar, or press `` Ctrl+` `` (Windows/Linux) or `` Cmd+` `` (Mac). The terminal opens at the bottom of the VS Code window. Paste the command and press Enter.

**Global install** (recommended -- available in every Claude Code project on your machine, installed once):

```bash
mkdir -p ~/.claude/commands
curl -o ~/.claude/commands/new-project.md \
  https://raw.githubusercontent.com/kasey6801/claude-skills/main/skills/new-project.md
```

**Project-level install** (available only in the current project):

```bash
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

| Code when | Do not code when |
|-----------|-----------------|
| The exact tool does not exist | A free tool already solves the problem |
| Existing tools require payment for something simple | The problem only needs solving once |
| You need specific behaviour | Maintenance will exceed the value |
| You want to learn | An existing solution is close enough |

A 10-line solution that works is always better than a 1000-line solution that almost works.

### The progression

| Stage | Project type | Process level |
|-------|-------------|---------------|
| First project | Small personal tool, local only | Minimal: change log and backlog |
| Second project | Slightly more complex | Add QC and README |
| Third project and beyond | Defined feature set, releases | Full process as in this guide |

---

## Section 7 — The file system: what lives where

> **This is the structure the `/new-project` skill sets up for you.** When you run `/new-project` and select Mode A, Claude creates this folder structure and all the archive documents listed below automatically. This section explains what each part is and why it exists, so you understand the project you are working in.

| Location | What it is | Pushed to GitHub? |
|----------|-----------|------------------|
| Active project files | Code, configuration, documentation | Yes |
| `_archive/` | Reference, history, previous versions | No |
| `.env` | Secret credentials | No |
| `RELEASE/` | Compiled, packaged product | No |

### Standard `_archive/` documents

| File | What it contains |
|------|-----------------|
| `CHANGE_LOG.md` | Every change, numbered, with reversal instructions |
| `BUILD_OVERVIEW.md` | Description of every active file |
| `[Project] Backlog.md` | Queued feature requests with priority |
| `QC.md` | Quality control audit rounds |
| `BRANDING.md` | Product name, colours, and assets |
| `EFFORT_INVESTMENT.md` | Time and effort summary |
| `CLAUDE_SECURITY_REVIEW.md` | Security audit findings |
| `[Project] Q&A.md` | Product questions and answers |

---

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
```bash
mkdir _archive RELEASE
```

**Step 2: Create `CLAUDE.md`**

*Claude Code:*
> *"Create a CLAUDE.md file for this project with standard rules and workflow instructions"*

*VS Code:* Right-click the project root in Explorer, choose **New File**, name it `CLAUDE.md`.

Never push this file to GitHub. [Claude Code reads CLAUDE.md automatically.](https://claude.com/docs)

**Step 3: Create the archive documents**

*Claude Code:*
> *"Create the standard empty archive documents in _archive: CHANGE_LOG.md, BUILD_OVERVIEW.md, [ProjectName] Backlog.md, QC.md, EFFORT_INVESTMENT.md, and CLAUDE_SECURITY_REVIEW.md"*

Six files are created at setup:
- `CHANGE_LOG.md` -- numbered log of every change
- `BUILD_OVERVIEW.md` -- description of every active file
- `[ProjectName] Backlog.md` -- prioritised feature queue
- `QC.md` -- quality control audit rounds
- `EFFORT_INVESTMENT.md` -- session time, changes, and equivalent human effort (start with placeholder values; update before each GitHub push)
- `CLAUDE_SECURITY_REVIEW.md` -- security audit findings (placeholder until the first `/security-review` is run)

**Step 4: Create `.env`**

Create a file named exactly `.env` at the project root:
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
```

**Step 6: Initialise version control** (only needed if tracking source code with Git)

*Claude Code:*
> *"Initialise git in this project and make the first commit"*

*VS Code terminal:*
```bash
git init
git add .
git commit -m "Initial commit"
```

**Step 7: Create the GitHub repository**

*Claude Code:*
> *"Create a GitHub repository called [ProjectName] and connect this project to it. Use $GITHUB_TOKEN from .env"*

Never paste the token directly into chat.

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

| Priority | Meaning |
|----------|---------|
| **P0** | Critical: blocking usage or data loss. Fix immediately. |
| **P1** | High: significant problem or missing core feature. |
| **P2** | Medium: improvement or non-blocking feature. |
| **P3** | Low: nice-to-have or future consideration. |

### The implement-or-backlog question
Before any change, Claude asks:
> *"Would you like to implement this now or add it to the backlog?"*

If adding: *"What priority? P0 (critical), P1 (high), P2 (medium), or P3 (low)?"*

### Entry format
```
### BL-[N] -- [Short title] (P[priority])
**Added:** YYYY-MM-DD
**Request:** [The original request]

**Implementation plan:**
[Files to change, what to change, how to verify]
```

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
```bash
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
- Technical architecture (use `BUILD_OVERVIEW.md`)

---

## Section 13 — Build and release workflow

### Build commands

Build commands vary by project type. The examples below are for JavaScript and Node.js projects. For Python, Swift, or other project types, the commands will differ -- ask Claude what the correct build command is for your project if you are unsure.

*Claude Code:*
> *"Install dependencies and build the project"*

*VS Code terminal (JavaScript/Node.js):*
```bash
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
```bash
zip -r "../[ProjectName] v1.0.0.zip" .
```

### Before pushing to GitHub

Before any `git push` or GitHub release, Claude prompts for two steps:

1. **Security review:** *"Would you like to run a security review before this push?"* If yes, Claude runs `/security-review`. All findings at or above 8/10 confidence are logged in `_archive/CLAUDE_SECURITY_REVIEW.md`. Findings below 8/10 are dismissed with reasoning.

2. **Effort logging:** *"Would you like to update EFFORT_INVESTMENT.md before pushing?"* If yes, Claude collects the approximate session time, the number of CHANGE_LOG entries made, and what was delivered. The Executive Summary totals and Effort Breakdown table are updated.

---

## Section 14 — Documentation update policy

| Change type | CHANGE_LOG | BUILD_OVERVIEW | BRANDING | QC |
|-------------|:---:|:---:|:---:|:---:|
| Any code change | Yes | | | |
| File added | Yes | Yes | | |
| File deleted | Yes | Yes | | |
| File renamed or moved | Yes | Yes | | |
| File purpose changed | Yes | Yes | | |
| Comment added or removed | Yes | | Yes | |
| Product name changed | Yes | | Yes | |
| Version number bumped | Yes | | Yes | |
| Asset added or replaced | Yes | | Yes | Yes |
| QC item found | Yes | | | Yes |
| QC item resolved | Yes | | | Yes |
| Archive-only change | Yes | | | |

**Timestamps:** Whenever any file is modified, update its `**Last updated:**` header to today's date.

---

## Section 15 — Archive documents reference

| Document | What it contains | When to update |
|----------|-----------------|----------------|
| `CHANGE_LOG.md` | Every change, numbered, with reversal steps | After every change |
| `BUILD_OVERVIEW.md` | Description and function of every active file | When files change |
| `[Project] Backlog.md` | Queued requests with priority and plan | When requests arrive or are implemented |
| `QC.md` | QC rounds, findings, and resolutions | After each QC check |
| `BRANDING.md` | Product name, colours, and assets | When auditing branding |
| `EFFORT_INVESTMENT.md` | Time invested and equivalent human effort | At milestones |
| `CLAUDE_SECURITY_REVIEW.md` | Security findings with confidence scores | After a security review |
| `[Project] Q&A.md` | Product questions and answers | During Q&A sessions |

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

---

## Section 18 — Instructions for Claude

This section is written for the AI assistant. Claude should follow these instructions in every session without being reminded.

**Before making any change:** Ask *"Would you like to implement this now or add it to the backlog?"* If adding: *"What priority? P0 through P3?"* Skip only if intent is unambiguous.

**After every execution:**
1. Update `CHANGE_LOG.md` with a numbered entry
2. Confirm: *"CHANGE_LOG.md updated -- last entry: [N]"*
3. Update `**Last updated:**` on every file touched
4. Prompt about documentation updates using Section 14

**Credentials:** Never ask the user to paste a token into chat. Reference `$VARIABLE_NAME` from `.env`. After pushing with a token-embedded git URL, immediately restore the clean HTTPS remote URL.

**Archiving before deleting:** Copy to `_archive/` first, then delete the original, then log in `CHANGE_LOG.md`. Never edit files inside `_archive/`.

**Files never pushed to GitHub:** `_archive/`, `RELEASE/`, `CLAUDE.md`, `.env`, `node_modules/`, `*.zip`, `.DS_Store`.

**QC checks:** Run when a significant phase completes, naming changes occur, dead code is suspected, or a security concern arises.

**Version numbers:** When a version number changes, update every file where it appears. Run `npm install` after updating `package.json`. Confirm all in sync before pushing.

**Documentation updates:** After every task, check Section 14. State which documents were updated and why. Never update silently.

---

*For further reading: [Claude Code documentation](https://claude.com/docs) | [VS Code documentation](https://code.visualstudio.com/docs) | [GitHub documentation](https://docs.github.com)*
