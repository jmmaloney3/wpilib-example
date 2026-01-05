# Trunk-Based Development Guide for FRC Robotics

## What is Trunk-Based Development?

Trunk-based development is a version control strategy where all developers work on a single branch (usually called "main") and integrate their changes frequently. Instead of maintaining long-lived feature branches, developers create short-lived branches for their work and merge them back to main quickly after code review.

## Core Principles

1. **Single Source of Truth**: The `main` branch is always deployable and represents the current state of the project
2. **Short-Lived Branches**: Feature branches exist only long enough to complete a small piece of work (hours or days, not weeks)
3. **Frequent Integration**: Changes are merged to main multiple times per day
4. **Code Reviews Required**: All changes must be reviewed and approved before merging to main
5. **Continuous Integration**: The main branch is always in a working state

## Benefits for FRC Teams

### 1. **Reduced Merge Conflicts**
- By integrating frequently, conflicts are smaller and easier to resolve
- Less time spent fixing merge issues means more time coding features

### 2. **Faster Feedback**
- Code reviews happen quickly on small changes
- Issues are caught early before they compound
- Team members see each other's work immediately

### 3. **Always Deployable**
- Main branch is always ready to deploy to the robot
- No need to wait for "feature complete" branches
- Easy to test the latest code on the robot

### 4. **Better Collaboration**
- Team members stay in sync with each other's changes
- Knowledge sharing happens naturally through code reviews
- Less risk of duplicate work

### 5. **Simpler Workflow**
- No complex branching strategies to remember
- Clear process: create branch → code → review → merge
- Easier for new team members to learn

## Workflow Procedures

### Daily Workflow

Follow these steps each time you start working on a new feature or fix.

1. **Start Your Day**
   - Switch to main branch and get the latest changes from your team
   - This ensures you're starting from the most current codebase
   
   <details>
   <summary>Using Command Line</summary>
   
   ```bash
   git checkout main
   git pull origin main
   ```
   </details>
   
   <details>
   <summary>Using GitHub Desktop</summary>
   
   - Open GitHub Desktop
   - Click the **"Current branch"** dropdown in the top toolbar
   - Select **"main"** from the list
   - Click **"Fetch origin"** to check for updates
   - If updates are available, click **"Pull origin"** to download and merge them
   - You'll see a notification if your local main is now behind the remote
   </details>

2. **Create a Feature Branch**
   - Create a new branch for your work (never code directly on main)
   - Use descriptive names that explain what you're working on
   - Keep each branch focused on one feature or fix
   
   <details>
   <summary>Using Command Line</summary>
   
   ```bash
   git checkout -b feature/your-feature-name
   ```
   
   **Naming examples:**
   - `feature/drive-base` - New drive base subsystem
   - `feature/arm-control` - Arm control improvements
   - `feature/autonomous-route-1` - Specific autonomous routine
   - `fix/encoder-drift` - Bug fix for encoder issue
   </details>
   
   <details>
   <summary>Using GitHub Desktop</summary>
   
   - Click the **"Current branch"** dropdown in the top toolbar
   - Click **"New branch"** at the bottom of the dropdown
   - Enter your branch name: `feature/your-feature-name`
   - Make sure **"main"** is selected as the branch to base it on
   - Click **"Create branch"**
   - You're now on your new branch (you'll see the branch name in the top toolbar)
   
   **Naming examples:**
   - `feature/drive-base` - New drive base subsystem
   - `feature/arm-control` - Arm control improvements
   - `fix/encoder-drift` - Bug fix for encoder issue
   </details>

3. **Make Your Changes**
   - Write your code, test it locally, and commit frequently
   - Write clear commit messages that explain what each commit does
   - Small, frequent commits are easier to review and debug
   
   <details>
   <summary>Using Command Line</summary>
   
   ```bash
   # After making changes to files
   git add path/to/changed/file.java  # Add specific files (safer)
   # OR: git add -u  # Only modified tracked files
   git commit -m "Add PID controller for arm position"
   ```
   
   **Good commit message examples:**
   - "Add PID controller for arm position"
   - "Fix drive base encoder calibration"
   - "Update autonomous routine for scoring"
   </details>
   
   <details>
   <summary>Using GitHub Desktop</summary>
   
   - Make your code changes in your editor
   - GitHub Desktop will show your changes in the left sidebar
   - Review the changes in the diff view (green = additions, red = deletions)
   - Check the boxes next to files you want to commit (or check "Select all")
   - Write a commit message:
     - **Summary** (required): Short description of what the commit does
     - **Description** (optional): Press Enter twice or click in the description field to add more details
   - Click **"Commit to [branch-name]"**
   - Repeat as you make more changes
   </details>

4. **Push Your Branch**
   - Upload your branch to GitHub so others can see it
   - First push sets up tracking so future pushes are simpler
   
   <details>
   <summary>Using Command Line</summary>
   
   ```bash
   git push -u origin feature/your-feature-name
   ```
   
   - The `-u` flag sets up "upstream tracking"
   - After this first push, you can just use `git push` for subsequent commits
   </details>
   
   <details>
   <summary>Using GitHub Desktop</summary>
   
   - Click **"Publish branch"** button in the top toolbar
   - GitHub Desktop will ask if you want to create a pull request
   - You can click "Create Pull Request" now, or do it later on GitHub
   - After the first push, use **"Push origin"** for future commits
   </details>

5. **Create a Pull Request**
   - See detailed instructions in the "Creating a Pull Request" section below
   - This is where your code gets reviewed before merging to main

6. **Address Review Feedback**
   - Make any requested changes
   - Push updates to your branch (the PR updates automatically)
   - Respond to comments and questions professionally

7. **Merge After Approval**
   - Once your PR is approved, merge it to main
   - Delete the feature branch after merging (GitHub will offer this)
   - Pull the latest main branch to start your next feature

### Branch Naming Conventions

Use clear, descriptive names:
- `feature/` - New features or functionality
  - Example: `feature/vision-targeting`
- `fix/` - Bug fixes
  - Example: `fix/encoder-drift`
- `refactor/` - Code improvements without changing behavior
  - Example: `refactor/drive-subsystem`
- `docs/` - Documentation updates
  - Example: `docs/autonomous-guide`

### Commit Message Guidelines

Write clear, concise commit messages:
- First line: Short summary (50 characters or less)
- Optional body: More detailed explanation if needed
- Use imperative mood: "Add feature" not "Added feature"

Examples:
```
Add PID controller for arm subsystem

Implements position control with configurable P, I, and D gains.
Includes unit tests for PID calculations.
```

```
Fix drive base encoder calibration

Resolves issue where encoders reset incorrectly during autonomous.
```

## Creating a Pull Request

After you've pushed your branch to GitHub, you need to create a Pull Request (PR) to get your code reviewed and merged into main.

### Step-by-Step Instructions

#### Using GitHub's Web Interface

1. **Navigate to Your Repository**
   - Go to your GitHub repository in a web browser
   - Click on the **"Pull requests"** tab at the top of the repository
   - Click the green **"New pull request"** button
   
   **Note:** Sometimes GitHub shows a yellow banner at the top saying "Your recently pushed branches" with a "Compare & pull request" button. If you see this, you can click it for a shortcut, but the method above always works.

2. **Select Your Branches**
   - **Base branch**: Should be `main` (or `master`)
   - **Compare branch**: Select your feature branch (e.g., `feature/arm-control`)
   - GitHub will show you a comparison of the changes

3. **Review Your Changes**
   - GitHub will show you a comparison view with:
     - A list of commits at the top
     - File diffs below showing what changed (additions in green, deletions in red)
   - Scroll through the changes to verify:
     - All your intended changes are included
     - You haven't accidentally included unrelated files
   - **Note:** After the PR is created, you'll see a "Files changed" tab in the PR detail view, but during creation you'll see the comparison view described above

4. **Click "Create pull request"**
   - Click the green **"Create pull request"** button near the top of the page
   - This will take you to the pull request form where you can add a title and description

5. **Fill Out the Pull Request Form**

   **Title** (required):
   - Write a clear, descriptive title
   - Examples:
     - "Add PID controller for arm position control"
     - "Fix drive base encoder calibration issue"
     - "Implement vision targeting for autonomous"
   - Keep it concise but informative

   **Description** (highly recommended):
   - Explain **what** your changes do
   - Explain **why** you made these changes
   - Mention any testing you've done
   - Include screenshots or videos if relevant (especially for robot behavior)
   - Link to related issues using `#issue-number` (e.g., "Fixes #42")
   
   Example description:
   ```markdown
   ## What This PR Does
   Adds a PID controller to the arm subsystem to enable precise position control.
   
   ## Why
   The previous open-loop control was inconsistent. This allows the arm to 
   accurately reach target positions for scoring.
   
   ## Testing
   - Tested on practice robot with various target positions
   - Verified PID tuning values work correctly
   - No regressions in other subsystems
   
   ## Related Issues
   Addresses #15
   ```

6. **Request Reviewers**
   - On the right sidebar, click **"Reviewers"**
   - Select at least one team member (or team lead) to review your code
   - You can request multiple reviewers if needed
   - Consider requesting someone familiar with the subsystem you're modifying

7. **Add Labels** (optional but helpful)
   - Click **"Labels"** on the right sidebar
   - Add relevant labels like:
     - `feature` - For new features
     - `bug` - For bug fixes
     - `documentation` - For docs updates
     - `subsystem:drivetrain` - For subsystem-specific labels

8. **Create the Pull Request**
   - Click the green **"Create pull request"** button at the bottom of the form
   - Your PR is now created and reviewers will be notified

### After Creating the Pull Request

1. **Wait for Review**
   - Reviewers will be notified automatically
   - They'll review your code and may leave comments or request changes

2. **Respond to Comments**
   - Address any questions or concerns
   - Make requested changes if needed
   - Be professional and open to feedback

3. **Update Your PR** (if changes are needed)
   - Make changes to your code locally and push them to the same branch
   - The PR will automatically update with your new commits
   
   <details>
   <summary>Using Command Line</summary>
   
   ```bash
   # Add specific files you changed (safer)
   git add path/to/file1.java path/to/file2.java
   # OR if you only modified tracked files (not adding new files):
   git add -u
   # Then commit and push
   git commit -m "Address review feedback: improve error handling"
   git push
   ```
   
   - **Note:** Avoid `git add .` unless you're certain there are no untracked files that shouldn't be committed
   - After the first push with `-u`, you can just use `git push` for subsequent commits
   </details>
   
   <details>
   <summary>Using GitHub Desktop</summary>
   
   - Make your code changes in your editor
   - GitHub Desktop will show your changes in the left sidebar
   - Review the changes, check the files you want to commit
   - Write a commit message:
     - **Summary** (required): Short description (e.g., "Address review feedback: improve error handling")
     - **Description** (optional): Add more details if needed
   - Click **"Commit to [branch-name]"**
   - Click **"Push origin"** to upload your changes
   - Your PR will automatically update with the new commit
   </details>

4. **Get Approval**
   - Once a reviewer approves your PR, you'll see a green checkmark
   - If branch protection requires multiple approvals, wait for all required approvals

5. **Merge the Pull Request**
   - Once approved, you'll see merge options near the bottom of the PR page
   - Click the dropdown button (it may show "Squash and merge" or another merge method)
   - Choose your merge method (note: not all options may be available - see below):
     - **"Squash and merge"** - Combines all commits into one (recommended for clean history)
       - Usually always available
     - **"Rebase and merge"** - Replays commits on top of main (also keeps linear history)
       - Available when the branch can be rebased cleanly (no conflicts)
     - **"Create a merge commit"** - Creates a merge commit (preserves full branch history)
       - **Common reason it's not available:** If your branch protection rule has **"Require linear history"** enabled (Settings → Branches → Branch protection rules), this will disable merge commits even if "Allow merge commits" is enabled in general settings
       - **What "Require linear history" means:** This setting enforces a clean, linear commit history on the protected branch (like `main`). Merge commits create a "branching" history, so they're automatically disabled when this rule is active
       - **For repository admins:** 
         - General setting: **Settings → General → Pull Requests** (checkboxes for merge methods)
         - Branch protection: **Settings → Branches → Branch protection rules** → Select your branch → Look for "Require linear history" checkbox
         - Branch protection rules override general settings
       - **For regular contributors:** You'll only see the merge options that are actually available based on both settings
       - **If "Create a merge commit" doesn't appear:** Your repository is configured to require linear history (common for teams wanting clean commit history)
   
   **How the end result differs:**
   
   Imagine your feature branch has 3 commits:
   - `Commit A: "Add arm subsystem"`
   - `Commit B: "Fix arm PID tuning"`
   - `Commit C: "Update arm documentation"`
   
   And main currently has:
   - `Commit 1: "Initial robot code"`
   - `Commit 2: "Add drive base"`
   
   **After "Squash and merge":**
   ```
   main: Commit 1 → Commit 2 → [Single commit: "Add arm subsystem, fix PID, update docs"]
   ```
   - All 3 commits become ONE commit on main
   - Clean, simple history
   - Individual commit messages are lost (but PR description is preserved)
   
   **After "Rebase and merge":**
   ```
   main: Commit 1 → Commit 2 → Commit A → Commit B → Commit C
   ```
   - All 3 commits appear individually on main
   - Linear history (no merge commit)
   - Each commit keeps its original message
   
   **After "Create a merge commit":**
   ```
   main: Commit 1 → Commit 2 → [Merge commit] ← (points to Commit A, B, C)
   ```
   - Creates a merge commit that combines the branches
   - Preserves the branch structure
   - Shows that commits A, B, C came from a feature branch
   
   **Important:** The feature branch can be safely deleted after ANY merge method. When you merge:
   - Git copies all commits from the feature branch into main's history
   - The commits become part of main - they don't depend on the feature branch existing
   - The merge commit (if used) just records that a merge happened, but the actual commits are now in main
   - Deleting the feature branch doesn't affect main at all - all your work is safely in main
   
   - Click the merge button to confirm
   - Delete the branch after merging (GitHub will offer this option - recommended to keep the repository clean)

### Pull Request Best Practices

✅ **Do:**
- Write clear titles and descriptions
- Keep PRs small and focused (one feature or fix per PR)
- Test your code before requesting review
- Request reviews from appropriate team members
- Respond to feedback promptly
- Link related issues or discussions

❌ **Don't:**
- Create PRs with broken code
- Include unrelated changes in the same PR
- Merge your own PR without review (even if you're an admin)
- Ignore review feedback
- Create PRs that are too large to review effectively

### Pull Request Template (Optional)

You can create a `.github/pull_request_template.md` file in your repository to provide a template for PR descriptions:

```markdown
## What This PR Does
<!-- Describe what your changes accomplish -->

## Why
<!-- Explain why these changes are needed -->

## Testing
<!-- Describe how you tested these changes -->
- [ ] Tested on robot
- [ ] Tested in simulator
- [ ] No regressions in other subsystems

## Screenshots/Videos (if applicable)
<!-- Add screenshots or links to videos showing the changes in action -->

## Related Issues
<!-- Link to related issues using #issue-number -->
Fixes #
```

## Configuring GitHub for Required Code Reviews

### Step 1: Navigate to Repository Settings

1. Go to your GitHub repository
2. Click on **Settings** (top right of the repository page)
3. In the left sidebar, click on **Branches**

### Step 2: Add Branch Protection Rule

1. On the Branches page, you'll see two options:
   - **Add branch ruleset** - Newer, more flexible option (for advanced use cases)
   - **Add classic branch protection rule** - Simpler, recommended for most teams
   
   **Click "Add classic branch protection rule"** (this is the option we'll use)

2. **Branch name pattern**: Enter `main` (or `master` if that's your default branch)

3. **Protect matching branches**: Check the following options:

   - ✅ **Require a pull request before merging**
     - Under this, check:
       - ✅ **Require approvals** (set to at least 1)
       - ✅ **Dismiss stale pull request approvals when new commits are pushed**
     - Optional but recommended:
       - ✅ **Require review from Code Owners** (if you have a CODEOWNERS file)
       - ✅ **Require status checks to pass before merging** (if you have CI/CD)

   - ✅ **Require status checks to pass before merging** (if you have automated tests)
     - Select which status checks must pass

   - ✅ **Require conversation resolution before merging**
     - Ensures all PR comments are addressed

   - ✅ **Require signed commits** (optional, for extra security)

   - ✅ **Require linear history** (optional, recommended for cleaner history)
     - **What it does**: Forces all merges to be "fast-forward" merges, which means the commit history looks like a straight line instead of having merge commits that create branches in the history
     - **With linear history**: Your git log shows commits in chronological order: A → B → C → D → E
     - **Without linear history**: Your git log shows merge commits: A → B → C → D → E, with merge commits like "Merge branch 'feature/arm' into main" creating a more complex tree structure
     - **Why use it**: 
       - Easier to read and understand the project history
       - Simpler to see what changed and when
       - Easier to revert specific commits
       - Better for learning and debugging
     - **Trade-off**: When enabled, GitHub will automatically rebase your PR before merging (or require you to rebase manually), which can be slightly more complex but results in cleaner history
     - **Recommendation**: ✅ **Enable this** - The cleaner history is worth it, especially for teams learning Git

   - ✅ **Do not allow bypassing the above settings** ⚠️ **CRITICAL - MUST ENABLE**
     - **What it does**: Prevents repository admins and owners from bypassing the branch protection rules
     - **Why it's critical**: Without this, admins can still push directly to main or merge PRs without reviews, which defeats the purpose of code reviews
     - **What happens if unchecked**: Admins will see "Bypassed rule violations" messages and can push directly to main
     - **Recommendation**: ✅ **ALWAYS enable this** - Even mentors and team leads should follow the same code review process

   - ❌ **Lock Branch** - **DO NOT ENABLE THIS**
     - **What it does**: Completely prevents ALL pushes to the branch, including merges from pull requests
     - **Why you don't want this**: This would block pull request merges, which defeats the entire purpose of trunk-based development
     - **What you want instead**: The "Require a pull request before merging" option (checked above) already prevents direct pushes while still allowing merges through approved pull requests
     - **When to use Lock Branch**: Only for archived branches or branches you want to completely freeze (not for active development branches)

4. **Restrict who can push to matching branches**: 
   - Leave unchecked to allow anyone to create branches
   - Check this if you want to restrict who can push directly to main

5. Click **Create** or **Save changes**

### Step 3: Verify the Protection Rule

1. Try to push directly to main (it should be blocked)
   - You should see an error message like this:
   ```
   remote: error: GH006: Protected branch update failed for refs/heads/main.
   remote: 
   remote: - Changes must be made through a pull request.
   To github.com:username/repository.git
    ! [remote rejected] main -> main (protected branch hook declined)
   error: failed to push some refs to 'github.com:username/repository.git'
   ```
   - This confirms that branch protection is working correctly!

2. Create a test branch and PR to verify reviews are required
3. Confirm that you cannot merge without an approval

> **Note**: GitHub offers two types of branch protection:
> - **Classic branch protection rule** - Simpler interface, perfect for most teams. This is what we recommend for FRC teams.
> - **Branch ruleset** - More advanced, allows complex rules and conditions. Useful for larger organizations with multiple repositories.

### Additional Configuration Options

#### Require Multiple Approvals

If you want multiple team members to review code:
- Set "Required number of approvals" to 2 or more
- Useful for critical subsystems like autonomous or safety features

#### Code Owners File

Create a `.github/CODEOWNERS` file to automatically request reviews from specific team members:

```
# Robot subsystems
/src/main/java/frc/robot/subsystems/drivetrain/ @team-lead @drive-team
/src/main/java/frc/robot/subsystems/arm/ @team-lead @arm-team
/src/main/java/frc/robot/commands/autonomous/ @team-lead @autonomous-team

# All code requires at least one review
* @team-lead
```

#### Status Checks

If you set up continuous integration (CI):
- Configure GitHub Actions or other CI tools
- Require tests to pass before merging
- This ensures code quality and prevents broken builds

## Best Practices for FRC Teams

### 1. **Keep Changes Small**
- Aim for PRs that can be reviewed in 15-30 minutes
- Break large features into smaller, reviewable pieces
- Example: Instead of "Complete autonomous", do:
  - "Add path following"
  - "Add scoring sequence"
  - "Add vision alignment"

### 2. **Review Promptly**
- Check for PR review requests multiple times per day
- Provide constructive feedback
- Approve quickly if the code looks good
- Ask questions if something is unclear

### 3. **Test Before Review**
- Test your code on the robot or simulator before requesting review
- Include test results in your PR description
- Document any known issues or limitations

### 4. **Communicate Clearly**
- Write clear PR descriptions explaining what and why
- Use comments in code to explain complex logic
- Respond to review feedback professionally

### 5. **Keep Main Branch Healthy**
- Never merge broken code to main
- Fix issues immediately if main breaks
- Run tests locally before pushing

### 6. **Regular Integration**
- Merge to main at least once per day
- Don't let branches sit for days or weeks
- If a branch is getting large, split it into smaller PRs

## Common Scenarios

### Scenario 1: Multiple People Working on the Same Feature

**Problem**: Two team members need to work on the same subsystem

**Solution**: 
- Split the work into smaller, independent pieces
- Create separate branches: `feature/arm-pid` and `feature/arm-safety`
- Review and merge independently
- Coordinate in person or via GitHub issues

### Scenario 2: Urgent Bug Fix During Competition

**Problem**: Need to fix a critical bug quickly

**Solution**:
- Still create a branch: `fix/critical-encoder-issue`
- Create PR and request immediate review
- Team lead can review and merge quickly
- Document the fix in the PR description

### Scenario 3: Large Refactoring

**Problem**: Need to refactor a large subsystem

**Solution**:
- Break into smaller PRs:
  1. `refactor/drive-base-extract-constants`
  2. `refactor/drive-base-simplify-methods`
  3. `refactor/drive-base-add-tests`
- Merge incrementally to keep main stable

### Scenario 4: Accidentally Worked on Main Branch

**Problem**: You started coding on the `main` branch instead of creating a feature branch, and now you have uncommitted or committed changes that you want to push.

**Step 1: Diagnose Your Situation**

First, let's check what state you're in:

1. **Check what branch you're on:**
   - Determine if you're on main or a feature branch
   
   <details>
   <summary>Using Command Line</summary>
   
   ```bash
   git branch
   ```
   - If you see `* main`, you're on the main branch
   - If you see `* feature/...`, you're already on a feature branch (no action needed!)
   </details>
   
   <details>
   <summary>Using GitHub Desktop</summary>
   
   - Look at the top toolbar in GitHub Desktop
   - The current branch name is shown in the **"Current branch"** dropdown
   - If it says "main", you're on the main branch
   - If it shows a feature branch name, you're already on a feature branch (no action needed!)
   </details>

2. **Check if you have commits on local main that aren't on remote main:**
   - Determine if you've committed changes to local main that aren't on GitHub yet
   - This is the most important check - it determines which solution to use
   
   <details>
   <summary>Using Command Line</summary>
   
   ```bash
   git fetch origin
   git log origin/main..main --oneline
   ```
   
   **What to look for:**
   - If this shows commits (you'll see commit messages), you have local commits on main that aren't on the remote
   - If this shows nothing (empty output), your local main matches the remote (no commits on main)
   
   **Example output if you have commits:**
   ```
   abc1234 Add PID controller for arm
   def5678 Fix encoder calibration
   ```
   This means you made 2 commits on your local main that aren't on the remote yet.
   </details>
   
   <details>
   <summary>Using GitHub Desktop</summary>
   
   - Make sure you're on the main branch (check the branch dropdown)
   - Look at the top toolbar or commit history in the left sidebar
   - **If you see "X commits ahead"** or a **"Push origin"** button, you have local commits on main
   - **If you don't see those indicators**, you likely don't have local commits on main
   - **To double-check:** Compare the most recent commit message in GitHub Desktop with the most recent commit on GitHub (go to your repository on GitHub.com, the main branch page shows the latest commit at the top)
   </details>

3. **Check if you have uncommitted changes:**
   - Determine if you have files you've modified but haven't committed yet
   
   <details>
   <summary>Using Command Line</summary>
   
   ```bash
   git status
   ```
   - If you see "Changes not staged for commit" or "Untracked files", you have uncommitted changes
   - **Note**: You can have uncommitted changes even if you've already committed other changes to main
   </details>
   
   <details>
   <summary>Using GitHub Desktop</summary>
   
   - Look at the left sidebar in GitHub Desktop
   - If you see files listed under "Changes" (with checkboxes), you have uncommitted changes
   - If the sidebar shows "No local changes", you don't have any uncommitted changes
   </details>

**Step 2: Choose the Correct Solution**

Based on your findings from Step 1:

**If you have neither commits nor uncommitted changes:**
→ You're all set! No action needed.

**If you have NO commits on main, but you DO have uncommitted changes:**
→ Go to **Solution A: Uncommitted Changes Only**
- This is the simpler case: just uncommitted changes, no commits yet

**If you have commits on local main (regardless of whether you also have uncommitted changes):**
→ Go to **Solution B: Commits on Main Branch**
- Solution B handles both: commits on main AND any uncommitted changes

---

### Solution A: Uncommitted Changes Only

Use this if you have uncommitted changes but haven't committed anything to main yet.

1. **Create a new branch from your current position**
   - This moves your uncommitted changes to the new branch
   - Your uncommitted changes will come with you automatically
   
   <details>
   <summary>Using Command Line</summary>
   
   ```bash
   git checkout -b feature/your-feature-name
   ```
   </details>
   
   <details>
   <summary>Using GitHub Desktop</summary>
   
   - Click the **"Current branch"** dropdown
   - Click **"New branch"**
   - Enter your branch name: `feature/your-feature-name`
   - Make sure **"main"** is selected as the base branch
   - Click **"Create branch"**
   - If a "Switch Branch" dialog appears, select **"Bring my changes to [new-branch-name]"**
     - This moves your uncommitted changes to the new branch (which is what we want)
     - Do NOT select "Leave my changes on main" - that would keep them on main
   - Your uncommitted changes will now be on the new branch
   </details>

2. **Commit your changes on the new branch:**
   - Save your work by committing it to the new branch
   
   <details>
   <summary>Using Command Line</summary>
   
   ```bash
   # Add specific files you changed (recommended)
   git add path/to/file1.java path/to/file2.java
   # OR if you only modified tracked files:
   git add -u
   # Then commit
   git commit -m "Your commit message"
   ```
   - **Note:** Use `git add .` only if you're certain all files in the directory should be committed
   </details>
   
   <details>
   <summary>Using GitHub Desktop</summary>
   
   - Your uncommitted changes should already be visible in the left sidebar
   - Review the changes, check the files you want to commit
   - Write a commit message:
     - **Summary** (required): Short description of what the commit does
     - **Description** (optional): Press Enter twice or click in the description field to add more details
   - Click **"Commit to [branch-name]"**
   </details>

3. **Push the new branch:**
   - Upload your branch to GitHub
   
   <details>
   <summary>Using Command Line</summary>
   
   ```bash
   git push -u origin feature/your-feature-name
   ```
   - The `-u` flag sets up upstream tracking so future pushes can use `git push`
   </details>
   
   <details>
   <summary>Using GitHub Desktop</summary>
   
   - Click **"Publish branch"** in the top toolbar
   - GitHub Desktop will ask if you want to create a pull request
   - You can create the PR now or do it later on GitHub
   </details>

4. **Switch back to main and verify it's clean:**
   - Confirm that main no longer has your changes
   
   <details>
   <summary>Using Command Line</summary>
   
   ```bash
   git checkout main
   git status
   ```
   - Main should now be clean (no uncommitted changes)
   </details>
   
   <details>
   <summary>Using GitHub Desktop</summary>
   
   - Click the **"Current branch"** dropdown
   - Select **"main"**
   - Check the left sidebar - it should show "No local changes"
   - Your changes are now safely on your feature branch
   </details>

5. **Create a Pull Request** from your feature branch as normal

---

### Solution B: Commits on Main Branch

Use this if you have already committed changes to your local main branch.

1. **Create a new branch from main**
   - This moves your commits and any uncommitted changes to the new branch
   - Your commits are now on this new branch
   
   <details>
   <summary>Using Command Line</summary>
   
   ```bash
   git checkout -b feature/your-feature-name
   ```
   </details>
   
   <details>
   <summary>Using GitHub Desktop</summary>
   
   - Click the **"Current branch"** dropdown
   - Click **"New branch"**
   - Enter your branch name: `feature/your-feature-name`
   - Make sure **"main"** is selected as the base branch
   - Click **"Create branch"**
   - Your commits and uncommitted changes are now on this new branch
   </details>

2. **If you have uncommitted changes, commit them now:**
   - Ensure all your work is committed before proceeding
   
   <details>
   <summary>Using Command Line</summary>
   
   ```bash
   # Add specific files you changed (recommended)
   git add path/to/file1.java path/to/file2.java
   # OR if you only modified tracked files:
   git add -u
   # Then commit
   git commit -m "Your commit message"
   ```
   - **Note:** Use `git add .` only if you're certain all files in the directory should be committed
   </details>
   
   <details>
   <summary>Using GitHub Desktop</summary>
   
   - If you see files in the "Changes" section, review and commit them
   - Check the files you want to commit
   - Write a commit message:
     - **Summary** (required): Short description of your changes
     - **Description** (optional): Add more details if needed
   - Click **"Commit to [branch-name]"**
   </details>

3. **Verify all changes are committed:**
   - Make sure everything is saved before resetting main
   
   <details>
   <summary>Using Command Line</summary>
   
   ```bash
   git status
   ```
   - You should see: `nothing to commit, working tree clean`
   - If you see any uncommitted changes, repeat step 2 to commit them
   </details>
   
   <details>
   <summary>Using GitHub Desktop</summary>
   
   - Check the left sidebar
   - It should show "No local changes"
   - If you see files listed, commit them first
   </details>

4. **Switch back to main:**
   - Return to main so we can reset it
   
   <details>
   <summary>Using Command Line</summary>
   
   ```bash
   git checkout main
   ```
   </details>
   
   <details>
   <summary>Using GitHub Desktop</summary>
   
   - Click the **"Current branch"** dropdown
   - Select **"main"**
   </details>

5. **Reset main to match the remote**
   - This removes your commits from local main (they're safe on your feature branch)
   - ⚠️ **Warning**: This removes your commits from local main, but they're safe on your feature branch
   
   <details>
   <summary>Using Command Line</summary>
   
   ```bash
   git reset --hard origin/main
   ```
   - This also removes any uncommitted changes from main (they're on your feature branch)
   </details>
   
   <details>
   <summary>Using GitHub Desktop</summary>
   
   - Click **"Branch"** in the menu bar
   - Select **"Update from [remote]/main"** or **"Discard all changes"**
   - This will reset your local main to match the remote
   - **Note**: Your commits are safe on your feature branch
   </details>

6. **Push your feature branch:**
   - Upload your branch to GitHub
   
   <details>
   <summary>Using Command Line</summary>
   
   ```bash
   git checkout feature/your-feature-name
   git push -u origin feature/your-feature-name
   ```
   - The `-u` flag sets up "upstream tracking" so you can use `git push` in the future
   - After the first push, you can just use `git push`
   </details>
   
   <details>
   <summary>Using GitHub Desktop</summary>
   
   - Switch back to your feature branch (click branch dropdown, select your feature branch)
   - Click **"Publish branch"** in the top toolbar
   - GitHub Desktop will ask if you want to create a pull request
   </details>

7. **Verify main is clean:**
   - Confirm that main is back to its original state
   
   <details>
   <summary>Using Command Line</summary>
   
   ```bash
   git checkout main
   git status
   ```
   
   **What to look for:**
   - `git status` should show: `Your branch is up to date with 'origin/main'` and `nothing to commit, working tree clean`
   - This means your local main branch matches the remote main branch, and all your work is safely on your feature branch
   
   **Optional - Check your feature branch has your work:**
   ```bash
   git checkout feature/your-feature-name
   git log --oneline -5
   ```
   - You should see your commits (the ones you wanted to move) listed here
   - This confirms your work is on the feature branch where it belongs
   </details>
   
   <details>
   <summary>Using GitHub Desktop</summary>
   
   - Make sure you're on the main branch
   - Check the left sidebar - it should show "No local changes"
   - Check the commit history - it should match what you see on GitHub
   - Switch to your feature branch to verify your commits are there
   </details>

8. **Create a Pull Request** from your feature branch as normal

**Prevention Tips:**
- Always check your branch before starting work: `git branch`
- Make it a habit to create a branch first: `git checkout main && git pull && git checkout -b feature/...`
- Some IDEs show the current branch name in the status bar - keep an eye on it!

## Troubleshooting

### "I can't push to main"
- This is expected! Create a branch instead
- Branch protection is working correctly
- **Example error message you'll see:**
  ```
  remote: error: GH006: Protected branch update failed for refs/heads/main.
  remote: 
  remote: - Changes must be made through a pull request.
  To github.com:username/repository.git
   ! [remote rejected] main -> main (protected branch hook declined)
  error: failed to push some refs to 'github.com:username/repository.git'
  ```
- **What to do**: Create a feature branch and push that instead (see "Daily Workflow" section above)

### "My PR is blocked"
- Check that you have the required number of approvals
- Ensure all status checks are passing
- Make sure all conversations are resolved

### "Merge conflicts"
- Your branch has conflicts with the latest main branch
- You need to merge main into your branch and resolve the conflicts
   
   <details>
   <summary>Using Command Line</summary>
   
   ```bash
   git checkout main
   git pull origin main
   git checkout feature/your-branch
   git merge main
   # Resolve conflicts in your editor, then:
   git add .
   git commit -m "Resolve merge conflicts"
   git push
   ```
   </details>
   
   <details>
   <summary>Using GitHub Desktop</summary>
   
   - Switch to main branch and click **"Pull origin"** to get latest changes
   - Switch back to your feature branch
   - Click **"Branch"** → **"Merge into current branch"** → Select **"main"**
   - GitHub Desktop will show conflicts if any exist
   - Resolve conflicts using the conflict resolution tool
   - Commit the merge resolution
   - Push your branch
   </details>

### "I need to update my PR"
- Just push more commits to your branch
- The PR updates automatically
- Re-request review if needed

### "I accidentally worked on main branch"
- Don't panic! Your changes aren't lost
- See "Scenario 4: Accidentally Worked on Main Branch" above for detailed steps
   
   <details>
   <summary>Quick Fix - Using Command Line</summary>
   
   - If you have uncommitted changes: `git checkout -b feature/your-branch` (moves changes)
   - If already committed: Create branch, then reset main with `git reset --hard origin/main`
   </details>
   
   <details>
   <summary>Quick Fix - Using GitHub Desktop</summary>
   
   - If you have uncommitted changes: Create a new branch (changes come with you)
   - If already committed: Create a new branch from main, then reset main to match remote
   </details>

### "I can push to main even though I have branch protection rules"
- If you see "Bypassed rule violations" in the output, you're bypassing the rules because you're an admin/owner
- **Solution**: Go to your branch protection settings and check **"Do not allow bypassing the above settings"**
- This prevents even admins from pushing directly to main
- After enabling this, you'll need to use pull requests like everyone else
- **Important**: Even mentors and team leads should follow the code review process!

## Summary

Trunk-based development with code reviews helps FRC teams:
- ✅ Write better code through peer review
- ✅ Avoid merge conflicts by integrating frequently
- ✅ Keep the codebase always deployable
- ✅ Learn from each other through code reviews
- ✅ Maintain code quality and consistency

Remember: **Small, frequent merges are better than large, infrequent ones!**

---

## Quick Reference

### Daily Commands

**Start work:**
- Switch to main and get latest changes, then create a feature branch

**During work:**
- Make changes, commit frequently, push to your branch

**After PR is merged:**
- Switch to main, pull latest, delete local feature branch

<details>
<summary>Using Command Line</summary>

```bash
# Start work
git checkout main
git pull origin main
git checkout -b feature/your-feature

# During work
git add path/to/changed/file.java  # Add specific files (safer)
# OR: git add -u  # Only modified tracked files
git commit -m "Clear commit message"
git push -u origin feature/your-feature  # First push only (sets up tracking)
# After first push, just use: git push

# After PR is merged
git checkout main
git pull origin main
git branch -d feature/your-feature  # Delete local branch
```
</details>

<details>
<summary>Using GitHub Desktop</summary>

**Start work:**
- Switch to main branch → Pull origin → Create new branch

**During work:**
- Make changes → Review in GitHub Desktop → Commit → Push origin

**After PR is merged:**
- Switch to main → Pull origin → Delete local feature branch (right-click branch name → Delete)
</details>

### GitHub Workflow
1. Push branch → Create PR → Request review → Address feedback → Merge → Delete branch

### Branch Protection Checklist
- ✅ Require pull request before merging
- ✅ Require at least 1 approval
- ✅ Require conversation resolution
- ✅ Do not allow bypassing settings

