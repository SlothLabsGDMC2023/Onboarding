# Setting Up the SlothLab Repository

> **Note:** You may skip this guide if you have already cloned the `generator` repository, copied *all* of its contents into the Amulet operations folder, and are familiar with Git. If you are unsure about any of those things, please follow the guide below.

This guide walks you through installing Git, setting up your local repository, and understanding our repository structure and how version control works.

---

## 1. Install Git

Before anything else, you need to have Git installed on your system.  
Git is our version control tool that lets us track changes, collaborate, and share code across the team.

### Windows
1. Download Git from [**git-scm.com/download/win**](https://git-scm.com/download/win).  
2. Install the latest version using the default settings.
3. Open **PowerShell** or **Git Bash** to confirm installation by running:
   `git --version`

### macOS
1. Open Terminal and check if Git is already installed: `git --version`
2. If not installed, run: `xcode-select --install`. 
This will install Git through Apple’s developer tools.

## 2. Access the SlothLab Repository

Once Git is ready, confirm that you have access to the 
[SlothLab repository](https://github.com/SlothLabsGDMC2023/generator).

If you don’t yet have permission, ask Michael to add you to the project.

---

## 3. Understanding Remote vs Local Repositories

The **remote repository** on GitHub acts as a shared cloud backup where everyone’s work is stored.

Your **local repository** is a clone of that same project on your computer, which you can modify freely before syncing your work back to the cloud.

This separation lets multiple contributors experiment locally without breaking the shared project.

---

## 4. Clone the Repository

### What is Cloning?

Cloning means downloading the full project history and files to your computer. You’ll now have your own editable copy.

Create or navigate to the directory where you’d like to store your projects (e.g., `Desktop/SlothLab`).

Open that folder in your terminal.

On GitHub, click the green “Code” button and copy the HTTPS link.

Run the command:
```bash
git clone https://github.com/SlothLabsGDMC2023/generator.git
```

Git will download the project into a new folder called `generator`.

Once finished, open the folder and you should see the project files!

If you would like to clone using SSH, contact Michael for help.

---

## 5. Open the Code in an Editor

If you don't already have one, you’ll need a code editor to explore and modify the project.

### Recommended Editor

- **Visual Studio Code** — the most popular option for Python and Git workflows.

Once installed, open the `generator` folder inside your editor. To open a folder, go to File and then Open Folder

Install the official **Python** extension by Microsoft from the Visual Studio Code Extension Marketplace

## 6. Essential Git Commands

Here are a few of the essential Git commands:

### Check Repository Status
```bash
git status
```
Shows which files you’ve modified and what’s staged for commit.

### Stage and Commit Changes
```bash
git add .
git commit -m "Describe what you changed"
```
This records your progress locally.

### Pull (Sync Downstream)
```bash
git pull
```
**Always pull before you start working** to make sure your local repository is up-to-date with the latest remote changes.
If you don’t, you risk merge conflicts or overwriting someone else’s work.

### Push (Sync Upstream)
```bash
git push
```
Uploads your committed changes to GitHub for others to access.

### Branching Basics

A **branch** is a separate line of development. We use branches to test or build new features without affecting the `main` (or “master” in our case) branch.

```bash
git branch                          # View existing branches
git checkout master                 # Switch to master branch
git checkout -b my-feature-branch   # Create and switch to a new branch
```
Make sure you’re on the correct branch before making any major edits:
```bash
git status
```
...will show you which branch you’re currently on.

You should work on your own feature branch and not on the `master` branch.

Before we submit to the competition, a TA will review your branch and merge it with the `master` branch.

---

## 7. Integrating with Amulet

After cloning, you’ll need to copy your local repository into the Amulet operations folder so that Amulet can detect and run our generation scripts.

### Windows

`\Users\<USERNAME>\AppData\Local\AmuletTeam\AmuletMapEditor\plugins\operations`

### macOS

`/Users/<USERNAME>/Library/Application Support/AmuletMapEditor/plugins/operations`

### Steps

1. **Copy** the entirety (every folder and file) of your SlothLab local `generator` repository into Amulet's `operations` folder. To be clear, this includes directories like `\generator`, `\planner`, or anything else! 
2. You’ll now be able to **test** scripts (like structure generators) directly inside Amulet.
3. When your additions to the code work perfectly, **copy them back** into your local repo to prepare them for commit and push to a feature branch of your creation. Upon sharing your contribution with the lab, we can get it pushed to the master branch. 

> Important: **Always remember to pull before pushing changes!**
>
> This ensures your local repository is synced with the remote one and prevents overwriting others’ work. Imagine you and another contributor edited the same file — pulling first allows Git to merge those changes safely before you upload yours.

---

**Next Steps:** Welcome to the team! Now that you've got the repo up and running, it's time to dive into the **[Amulet Crash Course](./AMULET-CRASH-COURSE.md)**!