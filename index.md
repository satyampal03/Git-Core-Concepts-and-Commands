# How to configure new folder with old github-repository 

```
1. First clone the previous repository

2. Go inside of the same repo that you want to configure with repository

3. Write the command <git init>

4. Copy the old repo URL <Where we clone the repo it code>local>https> copy the url>

5. Write this command into terminal on same path [git remote add origin <repository-url>]

6. git pull origin master <to be fetching and merging>

7. You can also add new new commit with the push.
```

# How to Create a New Repository

```
1. Go to You'r GitHub Account

2. Go in Repositories Section

3. Click on [New Repository] to create a new Repository 

4. Now give the repository name 

5. As you want to configure it you can do that such as - private/public

6. It will provide you a repo link <repo-url>

7. Now come in you'r VS-CODE -- configure you'r repo with you present directory 

8. Initilize you'r repo <git init>

9. Create some files inside you'r initilized directory

10. paste you'r git-hub-repository url in you'r directory

11. Now add to push files on git so -- <git add . OR git add [file/folder name]>

12. For commit Message --> <git commit -m 'Commit Message here'>

13. push you'r file/folder first time on you branch  --> <git push origin [branch name]>



# 📥 THE DEFINITIVE MANUAL: REMOVING GIT COMMITS (2025 EDITION)

This document provides a deep-dive into every mechanism available to remove commits from a Git repository, ranging from simple undos to complex history rewriting.

---

## 🛠 1. REMOVING THE MOST RECENT COMMIT (LOCAL)
Use these when the commit exists only on your computer.

### A. The Soft Reset (Undo but Keep Work)
**Scenario:** You committed, but realize you need to add more changes or fix the commit message.
*   **Command:** `git reset --soft HEAD~1`
*   **What happens:** The commit record is deleted. Your file changes are moved back to the **Staging Area** (Index).
*   **Result:** Files are "green" and ready for a new commit.

### B. The Mixed Reset (The Default Undo)
**Scenario:** You want to undo the commit and also unstage the files to work on them later.
*   **Command:** `git reset HEAD~1`
*   **What happens:** The commit is deleted. Your changes are moved back to the **Working Directory**.
*   **Result:** Files are "red" (unstaged). No code is lost, but nothing is ready to commit yet.

### C. The Hard Reset (The Deletion)
**Scenario:** The last commit was a total mistake and you want to delete the code changes forever.
*   **Command:** `git reset --hard HEAD~1`
*   **What happens:** The commit and all code changes within it are **destroyed**.
*   **Warning:** You cannot undo this easily. Ensure you don't need the code.

---

## 🛠 2. REMOVING A SPECIFIC OLD COMMIT (BY ID)
Use this when you want to remove a commit that is 3, 5, or 10 steps back in time without losing the work done afterward.

### A. Interactive Rebase (Surgical Extraction)
1.  **Find the ID:** Run `git log --oneline` to find the Hash (e.g., `a1b2c3d`).
2.  **Start Rebase:** You must target the commit *before* the one you want to kill.
    ```bash
    git rebase -i a1b2c3d^
    ```
3.  **The Editor:** A list of commits appears. Change the word `pick` to `drop` (or `d`) next to the target commit.
4.  **Save & Exit:** Git will "snip" that commit out and re-attach the rest of your history.

---

## 🛠 3. REMOVING COMMITS ALREADY PUSHED TO REMOTE
If your commit is on GitHub/GitLab, the rules change because other people might have your code.

### A. The Professional Way (Revert)
**Scenario:** You are working on a team and need to "undo" a pushed commit safely.
*   **Command:** `git revert <commit-id>`
*   **Mechanism:** Git creates a **new commit** that does the exact mathematical opposite of the target commit.
*   **Benefit:** It does not rewrite history, so your teammates' versions won't break.

### B. The Emergency Way (Force Push)
**Scenario:** You pushed sensitive data (like a password) and must erase it from the internet.
1.  **Local Fix:** Perform a Hard Reset (`git reset --hard HEAD~1`).
2.  **Force Push:** 
    ```bash
    git push origin <branch-name> --force
    ```
*   **Warning:** This overwrites the server's history. It will break the repo for anyone else on the team.

---

## 🛠 4. SPECIALIZED REMOVALS

### Remove a File but Keep the Commit
If you accidentally included `config.json` in your last commit:
```bash
git rm --cached config.json
git commit --amend --no-edit



# Fix it (Run these commands one by one)
> git branch            # Check your current branch (you will see main)

> git push -u origin main --force           # Push the correct branch