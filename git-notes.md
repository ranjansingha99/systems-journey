***

## 1. Git vs. GitHub: The Core Concept

It's crucial to understand the difference between **Git** and **GitHub**.

* **Git** is the tool you install on your computer. It's a free and open source distributed version control system that tracks changes to your project files locally. Think of it as a "save game" system for your code, allowing you to create snapshots (commits) and travel back in time.

* **GitHub** is the service or website you visit. It's a cloud-based platform that hosts your Git repositories. It's the online home for your projects, making it easy to store backups and collaborate with other people.

In short: **Git** is the tool, **GitHub** is the place you store the projects you use the tool on.

---

## 2. One-Time Setup

Before you start using Git, you should configure your user information. This information will be associated with every commit you make.

* `git config --global user.name "[firstname lastname]"`: Sets a name that is identifiable for credit when you review version history.
* `git config --global user.email "[valid-email]"`: Sets an email address that will be associated with each history marker.
* `git config --global color.ui auto`: Sets automatic command line coloring for Git, which makes reviewing easier.

---

## 3. The Core Git Workflow: Saving Your Work 💾

The process of saving changes in Git involves three stages. Understanding this is key to using Git effectively.

* **Working Directory**: This is your actual project folder on your computer where you edit your files. Any changes you make here are not yet saved by Git.
* **Staging Area (or Index)**: This is a "drafting" or "preparation" area. You add the specific changes you want to save from your Working Directory to the Staging Area. This allows you to group related changes together into a single, clean snapshot.
* **Repository (.git folder)**: This is the permanent "photo album" of your project. When you commit, Git takes everything in the Staging Area and saves it as a permanent snapshot (a commit) in the repository.

### Essential Commands for the Workflow:

* `git init`: Initializes an existing directory as a Git repository. (Run only once per project).
* `git clone [url]`: Retrieves an entire repository from a hosted location via a URL.
* `git status`: Your most important command. It shows modified files in your working directory and files staged for your next commit.
* `git add [file]` or `git add .`: Adds a file as it looks now to your next commit (this is called "staging").
* `git reset [file]`: Unstages a file while keeping the changes in your working directory.
* `git diff`: Shows the differences between what has changed in your working directory but is not staged.
* `git diff-staged`: Shows the differences between what is staged and what was last committed.
* `git commit -m "Your descriptive message"`: Commits your staged content as a new snapshot in the repository's history.
* `git remote add origin <URL>.git`: Add the remote repository to your working directory, giving it a nickname, origin.
* `git remote -v`: Verify the remote URL.

---

## 4. Branching & Merging: Working in Parallel 🌳

Branches are parallel timelines of your project that let you work on new features or bug fixes in isolation without affecting the main, stable version of your code.

The main, official branch is usually called **`main`**. You create a feature branch to do your work, and when you're done, you merge that feature branch back into **`main`**.

### Branching Workflow & Commands:

* `git branch`: Lists all of your branches. A `*` will appear next to the currently active branch.
* `git branch [branch-name]`: Creates a new branch at the current commit.
* `git checkout [branch-name]`: Switches to another branch and checks it out into your working directory.
* **Do your work**: Make your changes and create commits on this new branch. The `main` branch remains untouched.
* `git checkout main`: When done, switch back to the `main` branch.
* `git merge [branch-name]`: Merges the specified branch's history into your current one.
* `git log`: Shows all commits in the current branch's history.
* `git branch -m main`: Rename the 'master' branch to 'main', provided that it's already `git checkout [master]`. `-m` flag stands for "move," which is how Git renames a branch.
* `git push -u origin main`: Push the new 'main' branch to the remote repository. `-u` flag sets main as the default upstream branch, so in the future, you can just use `git push` in stead of `git push origin main` /or `git pull` in stead of `git pull origin main`.
* `git push origin --delete master`: Delete the old 'master' branch from the remote repository.

---

## 5. Collaboration: Working with Remotes (GitHub) ☁️

To collaborate, you need to sync your local repository with a remote repository (usually on GitHub).

A **remote** is a version of your repository hosted on the internet. **`origin`** is the default nickname(alias) for your main remote URL.

### Remote Commands:

* `git fetch [alias]`: Fetches down all the branches from a Git remote.
* `git merge [alias]/[branch]`: Merges a remote branch into your current branch to bring it up to date.
* `git push <nick_name> <branch_name>`: Transmits local branch commits to the remote repository branch. Ex: `git push origin main`
* `git pull = git fetch + git merge`
* `git pull`: Fetches and merges any commits from the tracking remote branch.
* `git pull <nick_name> <branch_name>`: pull the latest changes from origin’s <branch_name> branch into my current branch. Ex: `git pull origin main`

---

## 6. Inspecting the History 🔍

These commands help you examine logs, differences between commits, and object information.

* `git log`: Shows the commit history for the currently active branch.
* `git log branchB..branchA`: Shows the commits that are on branchA but not on branchB.
* `git log-follow [file]`: Shows the commits that changed a specific file, even if the file was renamed.
* `git diff branchB...branchA`: Shows the difference of what is in branchA that is not in branchB.
* `git show [SHA]`: Shows any object in Git (like a commit) in a human-readable format.

---

## 7. Tracking File Changes 📂

Git can also track when files are moved or removed.

* `git rm [file]`: Deletes a file from your project and stages that removal for the next commit.
* `git mv [existing-path] [new-path]`: Changes an existing file path and stages the move.
* `git log--stat -M`: Shows all commit logs with an indication of any paths that were moved or renamed.

---

## 8. Ignoring Files 🙈

You can tell Git to ignore certain files or patterns so they aren't accidentally staged or committed.

* This is done by creating a file named `.gitignore`.
* You can list direct file or folder names (`Logs/`) or use wildcards (`*.notes`) to ignore patterns of files.
* `git config --global core.excludesfile [file]`: Sets up a system-wide ignore pattern for all of your local repositories.

---

## 9. Advanced (but useful) Commands

These commands are powerful and can alter your project history. Use them with care, especially on your local branches.

### Rewriting History (⚠️ Use Caution)

* `git rebase [branch]`: Applies any commits of the current branch ahead of the specified one. This rewrites your commits to create a cleaner, linear history. Use this to update your feature branch with the latest changes from `main` before merging.
* `git reset --hard [commit]`: A "demolition" command. It clears the staging area and rewrites your working tree from a specified commit. Use this to completely discard recent, local mistakes that you have not pushed.

### Saving Unfinished Work

* `git stash`: Saves your modified and staged changes temporarily.
* `git stash list`: Lists the stack-order of your stashed file changes.
* `git stash pop`: Re-applies the changes from the top of the stash stack to your working directory.
* `git stash drop`: Discards the changes from the top of the stash stack.

---

## 10. Quick Note for Windows Users

The command `touch [filename]` is used to create empty files on Linux and macOS. It does not exist in Windows by default.

* In **PowerShell**, use: `New-Item [filename]`
* In the older **Command Prompt (CMD)**, use: `type nul > [filename]`
