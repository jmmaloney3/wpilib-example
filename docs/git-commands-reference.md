# Git Commands & Actions Reference

This reference provides detailed explanations of Git commands and actions used in trunk-based development. Use this when you need to understand what a command does or how to perform an action in GitHub Desktop.

For step-by-step workflows, see the [Trunk-Based Development Guide](trunk-based-dev-guide.md).

## Table of Contents

- [Switch to a Branch (checkout)](#switch-to-a-branch-checkout)
- [Pull Latest Changes](#pull-latest-changes)
- [Create a New Branch](#create-a-new-branch)
- [Commit Changes](#commit-changes)
- [Push Branch to Remote](#push-branch-to-remote)
- [Check Branch Status](#check-branch-status)
- [View Commit History](#view-commit-history)
- [Reset Branch to Match Remote](#reset-branch-to-match-remote)
- [Delete a Local Branch](#delete-a-local-branch)
- [Merge Branches](#merge-branches)
- [Resolve Merge Conflicts](#resolve-merge-conflicts)
- [Understanding Git Terminology](#understanding-git-terminology)

---

## Switch to a Branch (checkout)

**What it does:** Changes your working directory to a different branch, updating all files to match that branch's state.

**Why you use it:** You need to switch between branches to work on different features or to update your local main branch.

**When to use it:** 
- At the start of each day to switch to main
- When creating a new feature branch
- When switching between different feature branches

### Using Command Line

```bash
git checkout branch-name
```

**Examples:**
```bash
git checkout main              # Switch to main branch
git checkout feature/arm-pid   # Switch to a feature branch
```

**What happens:**
- Git updates all files in your working directory to match the selected branch
- Your current branch changes (you'll see it in `git branch` output)
- Any uncommitted changes might prevent the switch (Git will warn you)

**Common flags:**
- `-b` - Creates a new branch and switches to it: `git checkout -b feature/new-branch`

**Common issues:**
- "Your local changes would be overwritten" - You have uncommitted changes. Commit or stash them first.

### Using GitHub Desktop

1. Open GitHub Desktop
2. Click the **"Current branch"** dropdown in the top toolbar (shows your current branch name)
3. Select the branch you want from the list
   - You'll see all local branches
   - Remote branches appear under "Remote branches" section
4. GitHub Desktop will switch to that branch
   - Files update automatically
   - You'll see the branch name change in the top toolbar

**Visual indicators:**
- Current branch name appears in the top toolbar
- Branch list shows a checkmark next to the active branch
- If you have uncommitted changes, GitHub Desktop will warn you before switching

---

## Pull Latest Changes

**What it does:** Downloads the latest commits from the remote repository and merges them into your current local branch.

**Why you use it:** To get updates that other team members have pushed to the remote repository.

**When to use it:**
- At the start of each day before creating a new branch
- Before merging your feature branch to ensure you have the latest main
- When you see your branch is "behind" the remote

### Using Command Line

```bash
git pull origin branch-name
```

**Examples:**
```bash
git pull origin main           # Get latest changes for main branch
git pull origin feature/arm-pid # Get latest changes for a feature branch
```

**What happens:**
1. `git fetch` - Downloads information about remote branches (doesn't change your files)
2. `git merge` - Merges the remote changes into your local branch
3. Your local branch is now up to date with the remote

**Common variations:**
- `git pull` - Pulls from the tracked remote branch (if upstream is set)
- `git pull --rebase` - Pulls and rebases instead of merging (creates cleaner history)

**Potential issues:**
- Merge conflicts if you have local changes that conflict with remote changes
- Git will pause and ask you to resolve conflicts before completing

### Using GitHub Desktop

1. Open GitHub Desktop
2. Make sure you're on the branch you want to update (e.g., `main`)
3. Click **"Fetch origin"** to check for updates
   - This downloads information but doesn't change your files yet
4. If updates are available, click **"Pull origin"**
   - GitHub Desktop will merge the remote changes into your local branch
5. You'll see a notification showing what was updated

**Visual indicators:**
- Branch shows "X commits behind" if remote has updates you don't have
- "Pull origin" button appears when updates are available
- After pulling, you'll see the new commits in the history

**If there are conflicts:**
- GitHub Desktop will show a conflict resolution dialog
- You can resolve conflicts using the built-in merge tool
- Or choose to open in your editor to resolve manually

---

## Create a New Branch

**What it does:** Creates a new branch starting from your current branch's state, allowing you to work on features without affecting main.

**Why you use it:** To isolate your work from the main branch, enabling safe experimentation and code review.

**When to use it:**
- Before starting any new feature or fix
- When you want to try something without affecting main
- For every piece of work (never code directly on main)

### Using Command Line

```bash
git checkout -b branch-name
```

**Examples:**
```bash
git checkout -b feature/arm-pid        # Create feature branch
git checkout -b fix/encoder-calibration # Create bug fix branch
git checkout -b docs/update-readme     # Create documentation branch
```

**What happens:**
1. Creates a new branch pointing to your current commit
2. Switches to the new branch immediately
3. Your working directory stays the same (no file changes)
4. Future commits go to this new branch

**Branch naming best practices:**
- Use prefixes: `feature/`, `fix/`, `refactor/`, `docs/`
- Use descriptive names: `feature/arm-pid` not `feature/branch1`
- Use hyphens, not spaces: `feature/arm-control` not `feature/arm control`
- Keep it concise but clear

### Using GitHub Desktop

1. Open GitHub Desktop
2. Make sure you're on the branch you want to branch from (usually `main`)
3. Click the **"Current branch"** dropdown in the top toolbar
4. Click **"New branch"** at the bottom of the dropdown
5. Enter your branch name in the dialog
   - Follow naming conventions (e.g., `feature/arm-pid`)
6. Make sure the correct base branch is selected (usually `main`)
7. Click **"Create branch"**
8. **If you have uncommitted changes**, a "Switch Branch" dialog will appear:
   - Select **"Bring my changes to [new-branch-name]"** to move your changes to the new branch
   - Select "Leave my changes on main" **only if** you intentionally want to keep them on main (**unusual** in trunk-based development)
   - This dialog only appears if you have uncommitted changes
9. You're now on the new branch (branch name appears in top toolbar)

**Visual indicators:**
- Branch name appears in the top toolbar
- History shows the branch point
- You can see which branch you branched from
- If you had uncommitted changes, they're now on the new branch

---

## Commit Changes

**What it does:** Saves a snapshot of your current changes with a message describing what you did.

**Why you use it:** To save your work in Git's history, allowing you to track changes, revert if needed, and share your work.

**When to use it:**
- After completing a logical unit of work
- Before switching branches
- Frequently as you work (small commits are better than large ones)

### Using Command Line

**Step 1: Stage files (tell Git what to include)**
```bash
git add file1.java file2.java  # Add specific files
git add -u                     # Add all modified tracked files
git add .                      # Add all files (use with caution)
```

**Step 2: Commit**
```bash
git commit -m "Your commit message"
```

**What happens:**
1. `git add` - Stages files (marks them to be included in the commit)
2. `git commit` - Creates a commit with the staged files and your message
3. Commit is saved to your local branch's history
4. Files are now part of Git's version control

**Good commit messages:**
- Start with a verb: "Add", "Fix", "Update", "Remove"
- Be specific: "Add PID controller" not "Changes"
- Keep first line under 50 characters
- Add body for complex changes (press Enter twice after first line)

**Examples:**
```
Add PID controller for arm position control

Implements position control with configurable P, I, and D gains.
Includes unit tests for PID calculations.
```

**Common flags:**
- `-m "message"` - Adds a commit message inline
- `-a` - Automatically stages all modified files (skips `git add`)

### Using GitHub Desktop

1. Make your code changes in your editor
2. GitHub Desktop shows changed files in the left sidebar
3. Review changes in the diff view:
   - Green highlights = additions
   - Red highlights = deletions
   - Click a file to see detailed changes
4. Check boxes next to files you want to commit
   - Or check "Select all" to include everything
   - **Tip:** Only commit related changes together
5. Write a commit message in the bottom text box:
   - **Summary** (required): Short description of what the commit does (first line)
   - **Description** (optional): Press Enter twice or click in the description field below to add more detailed information
   - The summary is required; the description is optional but helpful for complex changes
6. Click **"Commit to [branch-name]"**
7. Commit is saved to your local branch

**Visual indicators:**
- Changed files show in left sidebar with status icons
- Diff view shows exactly what changed
- Commit button is disabled until you select files and write a message
- After committing, files move from "Changes" to "History"

---

## Push Branch to Remote

**What it does:** Uploads your local branch and commits to the remote repository (GitHub), making them available to your team.

**Why you use it:** To share your work, create pull requests, and back up your commits to the remote repository.

**When to use it:**
- After creating a new branch (first push)
- After making commits you want to share
- Before creating a pull request

### Using Command Line

**First push (sets up tracking):**
```bash
git push -u origin feature/arm-pid
```
- `-u` flag sets up "upstream tracking"
- After this, Git remembers where to push
- Future pushes can just use `git push`

**Subsequent pushes:**
```bash
git push
```
- Pushes to the tracked remote branch automatically
- No need to specify remote or branch name

**What happens:**
1. Git uploads your commits to the remote repository
2. Creates/updates the branch on GitHub
3. Other team members can now see your branch
4. You can create a pull request

**Common issues:**
- "Branch is behind" - Pull latest changes first, then push
- "Permission denied" - Check you have push access to the repository
- "Remote branch deleted" - Run `git fetch --prune` to update remote tracking

### Using GitHub Desktop

**First push:**
1. After making commits, look in the main content area (you'll see "No local changes" message)
2. Click the **"Publish branch"** button
3. GitHub Desktop will ask if you want to create a pull request
   - You can create PR now or do it later on GitHub
4. Branch is now on GitHub

**Subsequent pushes:**
1. After making new commits, look in the main content area
2. Click the **"Push origin"** button
3. Commits are uploaded to GitHub
4. Your pull request (if you have one) updates automatically

**Visual indicators:**
- "Publish branch" appears for new branches
- "Push origin" appears when you have local commits not on remote
- Branch shows "X commits ahead" if you have unpushed commits
- After pushing, status updates to show branch is in sync

---

## Check Branch Status

**What it does:** Shows you the current state of your working directory and branch.

**Why you use it:** To see what branch you're on, what files have changed, and if you're ahead or behind the remote.

**When to use it:**
- Before starting work to check your current state
- After switching branches to verify the switch worked
- When troubleshooting issues

### Using Command Line

```bash
git status
```

**What it shows:**
- Current branch name
- Whether you're ahead or behind the remote
- Uncommitted changes (modified, staged, untracked files)
- Files ready to be committed

**Example output:**
```
On branch feature/arm-pid
Your branch is ahead of 'origin/feature/arm-pid' by 2 commits.
Changes not staged for commit:
  modified:   src/main/java/frc/robot/subsystems/Arm.java
Untracked files:
  src/main/java/frc/robot/commands/ArmCommand.java
```

### Using GitHub Desktop

- Look at the top toolbar to see your current branch
- Check the left sidebar:
  - "Changes" section shows uncommitted changes
  - "History" section shows commits
- Look for indicators:
  - "X commits ahead" - You have local commits not on remote
  - "X commits behind" - Remote has commits you don't have
  - "No local changes" - Working directory is clean

---

## View Commit History

**What it does:** Shows a list of commits on your current branch or another branch.

**Why you use it:** To see what changes have been made, when they were made, and by whom.

**When to use it:**
- To review recent changes
- To find when a specific change was made
- To compare branches

### Using Command Line

```bash
git log
git log --oneline          # Compact one-line format
git log -5                 # Show last 5 commits
git log --oneline -5       # Compact format, last 5 commits
git log branch-name         # View another branch's history
```

**Common flags:**
- `--oneline` - One commit per line
- `-n` - Show last n commits (e.g., `-5`)
- `--graph` - Show branch structure visually
- `--all` - Show all branches

**Example:**
```bash
git log --oneline -5
```
Output:
```
abc1234 Add PID controller for arm
def5678 Fix encoder calibration
ghi9012 Update autonomous routine
jkl3456 Refactor drive base
mno7890 Initial commit
```

### Using GitHub Desktop

- The left sidebar shows commit history for your current branch
- Click a commit to see:
  - Commit message
  - Files changed
  - Diff view of changes
- Use the branch dropdown to view history of other branches
- History is shown in reverse chronological order (newest first)

---

## Reset Branch to Match Remote

**What it does:** Resets your local branch to exactly match the remote branch, discarding any local commits or changes.

**Why you use it:** To remove commits you accidentally made on main, or to start fresh from the remote state.

**When to use it:**
- When you've committed to main by mistake and want to remove those commits
- When you want to discard all local changes and match remote exactly
- ⚠️ **Warning**: This permanently discards local commits and changes

### Using Command Line

```bash
git reset --hard origin/main
```

**What happens:**
1. Moves your branch pointer to match the remote
2. Updates your working directory to match
3. **Permanently discards** any local commits not on remote
4. **Permanently discards** any uncommitted changes

**⚠️ Important:**
- Only use this if your work is safely on another branch
- This cannot be undone easily
- Make sure you've moved your commits to a feature branch first

**Common use case:**
- You committed to main by mistake
- You created a feature branch with those commits
- Now you want to reset main to match remote

### Using GitHub Desktop

1. Make sure you're on the branch you want to reset (e.g., `main`)
2. Click **"Branch"** in the menu bar
3. Select **"Discard all changes"** or look for reset options
4. GitHub Desktop will warn you about discarding changes
5. Confirm the reset

**⚠️ Important:**
- Only use this if your work is safely on another branch
- This permanently discards local changes
- Make sure you've moved your commits to a feature branch first

---

## Delete a Local Branch

**What it does:** Removes a local branch from your repository.

**Why you use it:** To clean up after a branch has been merged and deleted on GitHub.

**When to use it:**
- After a PR has been merged and the remote branch is deleted
- To remove old feature branches you no longer need
- To keep your local repository clean

### Using Command Line

```bash
git branch -d branch-name      # Safe delete (only if merged)
git branch -D branch-name      # Force delete (even if not merged)
```

**What happens:**
- Removes the branch pointer
- Does NOT delete the commits (they're still in Git's history)
- You can't switch to a deleted branch

**Common flags:**
- `-d` - Safe delete, only works if branch is fully merged
- `-D` - Force delete, works even if branch has unmerged commits

**Note:** After "Squash and merge" or "Rebase and merge", Git may think the branch isn't merged (because commits were rewritten). Use `-D` in this case - it's safe because your changes are in main.

### Using GitHub Desktop

1. Make sure you're NOT on the branch you want to delete (switch to another branch first)
2. Click the **"Current branch"** dropdown
3. Right-click on the branch you want to delete
4. Select **"Delete [branch-name]"**
5. Confirm the deletion

**Visual indicators:**
- Deleted branches disappear from the branch list
- You can't switch to a deleted branch
- The branch's commits are still in Git's history

---

## Merge Branches

**What it does:** Combines changes from one branch into another branch.

**Why you use it:** To integrate changes from main into your feature branch, or to combine work from different branches.

**When to use it:**
- When your feature branch is behind main and you need the latest changes
- To integrate work from another feature branch
- Usually done before creating a PR to ensure your branch is up to date

### Using Command Line

```bash
git checkout feature/your-branch    # Switch to your branch
git merge main                       # Merge main into your branch
```

**What happens:**
1. Git finds the common ancestor of both branches
2. Applies changes from main to your branch
3. Creates a merge commit if there are no conflicts
4. If conflicts exist, Git pauses and asks you to resolve them

**Common scenarios:**
- `git merge main` - Merge main into your current branch
- `git merge feature/other-branch` - Merge another feature branch

**After merging:**
- If no conflicts: Merge completes automatically
- If conflicts: You must resolve them, then commit

### Using GitHub Desktop

1. Switch to the branch you want to merge INTO (usually your feature branch)
2. Click **"Branch"** in the menu bar
3. Select **"Merge into current branch"**
4. Choose the branch to merge FROM (usually `main`)
5. GitHub Desktop will attempt the merge
6. If conflicts exist, resolve them using the conflict tool
7. Commit the merge

**Visual indicators:**
- Merge commit appears in history
- Conflicts are highlighted if they exist
- You'll see a notification about the merge result

---

## Resolve Merge Conflicts

**What it does:** Manually resolve conflicts that occur when Git can't automatically merge changes.

**Why you use it:** When the same lines were changed differently in two branches, Git needs you to decide which version to keep.

**When to use it:**
- After merging branches that have conflicting changes
- When pulling changes that conflict with your local changes
- Git will pause and ask you to resolve conflicts before continuing

### Using Command Line

**When a merge has conflicts:**
1. Git will show which files have conflicts
2. Open the conflicted files in your editor
3. Look for conflict markers:
   ```
   <<<<<<< HEAD
   Your changes
   =======
   Changes from the branch you're merging
   >>>>>>> branch-name
   ```
4. Edit the file to keep the code you want (or combine both)
5. Remove the conflict markers (`<<<<<<<`, `=======`, `>>>>>>>`)
6. Stage the resolved file: `git add filename`
7. Complete the merge: `git commit`

**Example resolution:**
```java
// Before (with conflict markers):
<<<<<<< HEAD
int speed = 50;
=======
int speed = 75;
>>>>>>> main

// After (resolved):
int speed = 75;  // Using the value from main
```

### Using GitHub Desktop

1. GitHub Desktop will show conflicted files in the left sidebar
2. Click on a conflicted file to see the conflict
3. Use the conflict resolution tool:
   - Click **"Use me"** to keep your version
   - Click **"Use theirs"** to keep the other version
   - Or manually edit to combine both
4. After resolving all conflicts, click **"Mark as resolved"**
5. Commit the merge resolution

**Visual indicators:**
- Conflicted files are marked with a warning icon
- Conflict markers are highlighted
- You can't complete the merge until all conflicts are resolved

---

## Understanding Git Terminology

### Local vs Remote

- **Local** - On your computer, in your repository
- **Remote** - On GitHub (the server), shared with your team
- **Origin** - The default name for your remote repository (usually GitHub)

### Branch Concepts

- **Branch** - A line of development (like a timeline of commits)
- **Main/Master** - The primary branch (usually called `main` in new repositories)
- **Feature branch** - A branch for working on a specific feature
- **Upstream tracking** - Link between local and remote branch (set with `-u` flag)

### Commit Concepts

- **Commit** - A snapshot of your code at a point in time
- **Stage** - Mark files to be included in the next commit (`git add`)
- **Commit message** - Description of what the commit does
- **Commit hash** - Unique identifier for each commit (e.g., `abc1234`)

### Common Operations

- **Push** - Upload local commits to remote
- **Pull** - Download remote commits to local
- **Merge** - Combine changes from different branches
- **Rebase** - Replay commits on top of another branch (creates linear history)
- **Squash** - Combine multiple commits into one

### Status Indicators

- **Ahead** - You have local commits not on remote
- **Behind** - Remote has commits you don't have
- **Diverged** - Both ahead and behind (need to merge)
- **Clean** - No uncommitted changes
- **Dirty** - Has uncommitted changes

---

## Getting Help

### Command Line Help

- `git help command-name` - Shows detailed help for a command
  - Example: `git help checkout`
- `git command-name --help` - Alternative way to get help
- `git help` - Lists all available commands

### GitHub Desktop Help

- Help menu → "GitHub Desktop Help"
- Help menu → "Show Logs" (for troubleshooting)
- Help menu → "About GitHub Desktop" (version info)

### Additional Resources

- [Trunk-Based Development Guide](trunk-based-dev-guide.md) - Step-by-step workflows
- [Git Official Documentation](https://git-scm.com/doc)
- [GitHub Desktop Documentation](https://docs.github.com/en/desktop)

---

## Quick Command Reference

### Most Common Commands

```bash
git checkout main              # Switch to main branch
git pull origin main           # Get latest changes
git checkout -b feature/name   # Create and switch to new branch
git add file.java              # Stage a file
git commit -m "Message"        # Commit changes
git push -u origin branch      # Push branch (first time)
git push                       # Push branch (subsequent)
git status                     # Check current state
git log --oneline -5           # View recent commits
```

### Branch Management

```bash
git branch                     # List local branches
git branch -a                  # List all branches (local and remote)
git branch -d branch-name      # Delete local branch (safe)
git branch -D branch-name      # Delete local branch (force)
git branch -vv                 # Show branches with tracking info
```

### Troubleshooting

```bash
git fetch --prune              # Update remote tracking, remove deleted branches
git log main..branch           # See commits in branch not in main
git diff main..branch          # See differences between branches
git reset --hard origin/main   # Reset branch to match remote (⚠️ destructive)
```

---

*Last updated: 2025*

