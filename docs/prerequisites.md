# Prerequisites

This page lists everything you need on your machine and in your accounts before installing MkDocs. If you are new to this guide, start at [What is MkDocs](what-is-mkdocs.md).

Before you install MkDocs, make sure the following software is installed and the following accounts are in place. If you are comfortable with everything on this list, you will be able to complete this guide without additional research.

---

## Software requirements

You need the following tools installed on your machine:

**Python**
MkDocs is built on Python. Install the latest stable version for your operating system:

- **Windows:** Download from [python.org](https://www.python.org/downloads/) and check the box that says **"Add Python to PATH"** during setup. Without this, your terminal will not recognise Python commands.
- **macOS:** Install via Homebrew by running `brew install python` in your terminal. If you do not have Homebrew, install it first from [brew.sh](https://brew.sh/).
- **Linux:** Use your system package manager. On Ubuntu or Debian, run `sudo apt install python3`.

**pip**
pip is Python's package manager. You will use it to install MkDocs and its theme. pip is included automatically with Python on Windows and macOS. On some Linux distributions, pip must be installed separately. If pip is not available after installing Python, run:

```bash
python -m ensurepip
```

**Git**
Git is required to version-control your documentation and deploy it to GitHub Pages. Install it from [git-scm.com](https://git-scm.com/).

To confirm all three are installed, open your terminal and run:

```bash
python --version
pip --version
git --version
```

Each command should return a version number. If any returns an error, revisit the installation for that tool before continuing.

---

## Accounts

**GitHub account**
MkDocs itself is a local tool and requires no account. However, to host your documentation online using GitHub Pages, which this guide covers, you need a free GitHub account. Create one at [github.com](https://github.com) if you do not already have one.

---

## Assumed knowledge

This guide assumes you are comfortable with the following:

- **Terminal basics:** navigating directories and running commands. If you have never used a terminal before, spend 15 minutes with a beginner tutorial before continuing.
- **Markdown:** writing content in plain text with Markdown syntax. MkDocs uses Markdown for all documentation content.
- **Git fundamentals:** initialising a repository, staging changes, committing, and pushing to a remote. If you are new to Git, the [Git and GitHub for Technical Writers](https://douglasebhoman.github.io/git-github-for-technical-writers-series) series covers everything you need.
- **GitHub basics:** creating a repository and navigating the GitHub interface.

You do not need any experience with web development, HTML, CSS, or Python programming to follow this guide.

---

## Before you begin checklist

Run each command and confirm it returns a version number before moving on:

- [ ] `python --version` returns a version number
- [ ] `pip --version` returns a version number
- [ ] `git --version` returns a version number
- [ ] GitHub account created at [github.com](https://github.com)
- [ ] Comfortable navigating the terminal and running basic Git commands

Once every item on this list is checked, move to [Installation](installation.md).