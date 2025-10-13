# Setting Up the SlothLab Repository

> **Note:** You may skip this guide if you have already cloned the repository, copied it into the Amulet operations folder, and are familiar with Git basics.

Welcome to the SlothLab project!  
This guide will walk you through installing Git, setting up your local environment, and understanding how our repository structure and version control workflow operate.

---

## 1. Install Git

Before anything else, you need Git installed on your system.  
Git is the version control tool that lets us track changes, collaborate, and share code seamlessly across the SlothLab team.

### Windows
1. Go to [**git-scm.com/download/win**](https://git-scm.com/download/win).  
2. Download and install the latest version.
3. During installation, keep the default settings unless you know what you’re doing.
4. Open **Git Bash** to confirm installation by running:
   `git --version`

### macOS
1. Open Terminal and check if Git is already installed: `git --version`
2. If not installed, run: `xcode-select --install`. 
This will install Git through Apple’s developer tools.

## 2. Access the SlothLab Repository

Once Git is ready, confirm that you have access to the 
[SlothLab repository](https://github.com/SlothLabsGDMC2023/generator).

If you don’t yet have permission, ask Dr. Markus Eger to add you to the project.

---

## 3. Understanding Remote vs Local Repositories

The **remote repository** on GitHub acts as a shared cloud backup where everyone’s work is stored.

Your **local repository** is a clone of that same project on your computer, which you can modify freely before syncing your work back to the cloud.

This separation lets multiple contributors experiment locally without breaking the shared project.

---

## 4. Clone the Repository

### What is Cloning?

Cloning means downloading the full project history and files to your computer. You’ll now have your own editable copy.

Create or navigate to the directory where you’d like to store your projects (e.g., `Documents/SlothLab`).

Open that folder in your terminal.

On GitHub, click the green “Code” button and copy the HTTPS link.

Run the command:
```bash
git clone https://github.com/SlothLabsGDMC2023/generator.git
```

Git will download the project into a new folder called `generator`.

Once finished, open the folder and you should see the project files—welcome to SlothLab!

---

## 5. Open the Code in an Editor

If you don't already have one, you’ll need a code editor to explore and modify the project.

### Recommended Editor

- **Visual Studio Code** — the most popular option for Python and Git workflows.

Once installed, open the `generator` folder inside your editor.

## 6. Essential Git Commands

Here are a few of the essentials:

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
**Always pull before you start working** to make sure your local copy is up-to-date with the latest remote changes.
If you don’t, you risk **merge conflicts** or overwriting someone else’s work.

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

You will want to make sure you're on the `master` branch for now.

---

## 7. Integrating with Amulet

After cloning, you’ll need to copy your local repository into the Amulet operations folder so that Amulet can detect and run our generation scripts.

### Path Example (Windows)

`AppData\Local\AmuletTeam\AmuletMapEditor\plugins\operations`

### Steps

1. **Copy** your SlothLab local repository into the `operations` folder.
2. You’ll now be able to **test** scripts (like structure generators) directly inside Amulet.
3. When your structure generator works perfectly, **copy it back** into your main local repo to prepare it for commit and push.

> Important: **Always remember to pull before pushing changes!**
>
> This ensures your local branch is synced with the remote one and prevents overwriting others’ work. Imagine you and another contributor edited the same file — pulling first allows Git to merge those changes safely before you upload yours.

---

**Next Steps:** Welcome to the team! Now that you've got the repo up and running, it's time to dive into the **[Amulet Crash Course](./AMULET-CRASH-COURSE.md)**!