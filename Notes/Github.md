# Git & GitHub Essentials for SDETs

## 1. Local Repository Setup & Daily Workflow
1. **Initialize local repository**
   ```bash
   git init
   ```
   *Creates a hidden `.git` folder. The default branch pointer comes into effect after your first commit.*

2. **Configure user identity (one-time setup)**
   ```bash
   git config --global user.name "Your Name"
   git config --global user.email "your.email@example.com"
   ```

3. **Stage changes**
   ```bash
   git add <filename>   # Stage a specific file
   git add .            # Stage all untracked and modified files
   ```

4. **Commit staged changes**
   ```bash
   git commit -m "Initial commit"
   ```
   *Creates a commit object containing metadata (author, timestamp) and a snapshot of staged files. Each commit gets a unique SHA-1 hash (40-character checksum) for data integrity.*

5. **View history & HEAD pointer**
   ```bash
   git log
   ```
   * **`HEAD`**: A pointer that refers to the current commit/branch you are currently working on.
   * **`git checkout <commit-id>`**: Switches your working directory state to a specific historical commit.

## 2. File Lifecycle Management & Untracking
* **Working Directory (Untracked)**: Files not tracked by Git. If deleted via `rm <filename>`, they cannot be recovered by Git.
* **Stop tracking a file (keep locally)**:
  ```bash
  git rm --cached <filename>
  ```
* **Ignore unwanted files (`.gitignore`)**: Prevents test reports, logs, and dependencies from being tracked.
  1. Create `.gitignore`: `touch .gitignore`
  2. Add ignore patterns (e.g., `newman/`, `target/`, `*.log`, `.env`)

## 3. Connecting & Pushing to GitHub

1. **Verify existing remotes**
   ```bash
   git remote -v
   ```

2. **Link local repository to remote**
   ```bash
   git remote add origin <repository-url>
   ```

3. **Rename current branch to `main`**
   ```bash
   git branch -M main
   ```
   *`-M` forces the current local branch to be renamed to `main`.*

4. **Push local code to GitHub**
   ```bash
   git push -u origin main
   ```
   *`-u` (`--set-upstream`) links your local `main` branch to `origin/main`. Future updates only require running `git push` or `git pull`.*
