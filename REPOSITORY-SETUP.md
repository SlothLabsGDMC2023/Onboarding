# Setting Up the SlothLab Repository

> **Note:** Skip this guide if you have already cloned the `generator` repository and copied all its contents into the Amulet operations folder. 

This guide walks you through installing Git, setting up your local repository, and understanding our repository structure and how version control works.

---

## 1. Install Git

To get started, we need to install Git. We use it for version control to track changes, collaborate, and share code across the team.

### Windows
1. Open **PowerShell** and check if Git is already installed: `git --version`
2. If not installed, download Git from [**git-scm.com/download/win**](https://git-scm.com/download/win).  
3. Install the latest version using the default settings.
4. Open **PowerShell** to confirm the installation was successful: `git --version`

### macOS
1. Open **Terminal** and check if Git is already installed: `git --version`
2. If not installed, download Git with `xcode-select --install`
3. Open **Terminal** to confirm the installation was successful: `git --version`

## 2. Access the SlothLab Repository

Once Git is installed, confirm that you have access to the [SlothLab Repository](https://github.com/SlothLabsGDMC2023/generator).

If you don’t have permission, ask Michael to add you to the project.

---

## 3. Understanding Remote vs Local Repositories

The **remote repository** is a version of the project stored in the cloud where everyone's work is saved.

Your **local repository** is a version of the project stored on your computer, which you can freely modify before syncing your work with the cloud.

This separation lets contributors work independently without breaking the shared project.

---

## 4. Clone the Repository

### What is Cloning?

Cloning creates a local copy by downloading the full project history and files to your computer. 

Create or navigate to the directory where you’d like to store your projects (e.g., `Desktop/SlothLab`).

Open that folder in your terminal.

On [GitHub](https://github.com/SlothLabsGDMC2023/generator), click the green “Code” button and copy the HTTPS link.

Run the command: `git clone https://github.com/SlothLabsGDMC2023/generator.git`

Git will download the project into a new folder called `generator`.

Once finished, open the folder and you should see the project files!

If you would like to clone using SSH, contact Michael for help.

---

## 5. Open the Code in an Editor

If you don't already have an editor, download Visual Studio Code from [**https://code.visualstudio.com/download**](https://code.visualstudio.com/download).

Once you have an editor, open the `generator` folder with your editor.

Install the official Python extension by Microsoft from the Visual Studio Code Extension Marketplace.

---

## 6. Essential Git Commands

Here are a few of the essential Git commands:

### Check Repository Status
```bash
git status
```

Shows which files you have modified, what’s staged for commit, and which branch is active.

### Stage and Commit Changes
```bash
git add .
git commit -m "Describe what you changed"
```

Stages your changes and saves a snapshot of your progress in your local repository.

### Pull (Sync Downstream)
```bash
git pull
```

Fetches and merges the latest changes from the remote repository. Always pull before you begin working to ensure your local repository remains up-to-date with the latest remote changes.

### Push (Sync Upstream)
```bash
git push
```
Uploads your committed changes to GitHub for others to access.

### Branching Basics

A branch is a separate line of development. Using branches allows you to build and test new features without affecting the `master` branch.

```bash
git branch                          # View existing branches
git checkout master                 # Switch to the master branch
git checkout -b my-feature-branch   # Create and switch to a new branch
```
Make sure you’re on the correct branch before making any major edits.

```bash
git status
```
Shows which branch you’re currently on.

You should work on your own feature branch and not on the `master` branch.

Before we submit to the competition, a TA will review your branch and merge it with the `master` branch.

---

## 7. Integrating with Amulet

After cloning, you’ll need to copy your local repository into the Amulet operations folder so that Amulet can detect and run our generation scripts. Navigate to the operations folder using the path for your operating system below:

### Windows

`C:\Users\<USERNAME>\AppData\Local\AmuletTeam\AmuletMapEditor\plugins\operations`

### macOS

`/Users/<USERNAME>/Library/Application Support/AmuletMapEditor/plugins/operations`

1. Copy the contents of your local `generator` repository into Amulet's `operations` folder.
2. You’ll now be able to test your code by running your generation scripts directly inside Amulet on a test world.
3. Copy your updated files back into your local repository once your features work as intended.
4. Commit and push your changes to your feature branch on GitHub

> **Note:** Always remember to pull before pushing changes! This ensures your local repository is synced with the remote one and prevents overwriting others’ work. Imagine you and another contributor edited the same file — pulling first allows Git to merge those changes safely before you upload yours.

---

**Next Steps:** Welcome to the team! Now that you have the repository up and running, it's time to dive into the **[Amulet Crash Course](./AMULET-CRASH-COURSE.md)**!