# Trunk-Based Development Guide for FRC Robotics

## What is Trunk-Based Development?

Trunk-based development is a version control strategy where all developers work on a single branch (called "main" or "trunk") and integrate their changes frequently. Instead of maintaining long-lived feature branches, developers create short-lived branches for their work and merge them back to main quickly after code review.

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

1. **Start Your Day**
   ```bash
   git checkout main
   git pull origin main
   ```
   - `git checkout main` - Switches to the `main` branch (makes it your active branch)
   - `git pull origin main` - Downloads and merges the latest changes from the remote `main` branch

2. **Create a Feature Branch**
   ```bash
   git checkout -b feature/your-feature-name
   ```
   - `git checkout -b` - Creates a new branch and switches to it (the `-b` flag means "create branch")
   - Use descriptive names: `feature/drive-base`, `feature/arm-control`, `feature/autonomous-route-1`
   - Keep branches focused on one feature or fix
   
   **What `git checkout` does:**
   - Switches your working directory to a different branch
   - Updates your files to match that branch's state
   - Makes that branch your "active" branch (where new commits will go)
   - `git checkout -b` creates a new branch and switches to it in one command

3. **Make Your Changes**
   - Write code, test locally, commit frequently
   - Write clear commit messages:
     ```
     Add PID controller for arm position
     Fix drive base encoder calibration
     Update autonomous routine for scoring
     ```

4. **Push Your Branch**
   ```bash
   git push -u origin feature/your-feature-name
   ```
   - The `-u` flag sets up "upstream tracking" so future pushes can just use `git push`
   - After this first push, you can use `git push` for subsequent commits

5. **Create a Pull Request**
   - See detailed instructions in the "Creating a Pull Request" section below

6. **Address Review Feedback**
   - Make requested changes
   - Push updates to your branch (the PR updates automatically)
   - Respond to comments and questions

7. **Merge After Approval**
   - Once approved, merge the PR
   - Delete the feature branch after merging
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
   - You should see a yellow banner at the top saying "Your recently pushed branches" with your branch name
   - Click the **"Compare & pull request"** button

   OR

   - Click on the **"Pull requests"** tab at the top of the repository
   - Click the green **"New pull request"** button

2. **Select Your Branches**
   - **Base branch**: Should be `main` (or `master`)
   - **Compare branch**: Select your feature branch (e.g., `feature/arm-control`)
   - GitHub will show you a comparison of the changes

3. **Review Your Changes**
   - Scroll down to see the "Files changed" tab
   - Verify that all your changes are included
   - Make sure you haven't accidentally included unrelated files

4. **Fill Out the Pull Request Form**

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

5. **Request Reviewers**
   - On the right sidebar, click **"Reviewers"**
   - Select at least one team member (or team lead) to review your code
   - You can request multiple reviewers if needed
   - Consider requesting someone familiar with the subsystem you're modifying

6. **Add Labels** (optional but helpful)
   - Click **"Labels"** on the right sidebar
   - Add relevant labels like:
     - `feature` - For new features
     - `bug` - For bug fixes
     - `documentation` - For docs updates
     - `subsystem:drivetrain` - For subsystem-specific labels

7. **Create the Pull Request**
   - Click the green **"Create pull request"** button
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
   - Make changes to your code locally
   - Commit and push to the same branch:
     ```bash
     git add .
     git commit -m "Address review feedback: improve error handling"
     git push
     ```
   - After the first push with `-u`, you can just use `git push` for subsequent commits
   - The PR will automatically update with your new commits

4. **Get Approval**
   - Once a reviewer approves your PR, you'll see a green checkmark
   - If branch protection requires multiple approvals, wait for all required approvals

5. **Merge the Pull Request**
   - Once approved, click the green **"Merge pull request"** button
   - Choose merge method (if linear history is required, use "Rebase and merge" or "Squash and merge")
   - Confirm the merge
   - Delete the branch after merging (GitHub will offer this option)

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
   ```bash
   git branch
   ```
   - If you see `* main`, you're on the main branch
   - If you see `* feature/...`, you're already on a feature branch (no action needed!)

2. **Check if you have commits on local main that aren't on remote main:**
   ```bash
   git fetch origin
   git log origin/main..main --oneline
   ```
   
   **What this command does:**
   - `git fetch origin` - Downloads the latest information about the remote repository (but doesn't change your local files)
   - `git log origin/main..main --oneline` - Shows commits that are in your local `main` branch but NOT in the remote `origin/main` branch
     - The `..` syntax means "show commits in the second branch that aren't in the first branch"
     - `--oneline` shows a compact one-line format for each commit
   
   **What to look for:**
   - If this shows commits (you'll see commit messages), you have local commits on main that aren't on the remote
   - If this shows nothing (empty output), your local main matches the remote (no commits on main)
   - **This is the most important check** - it determines which solution to use
   
   **Example output if you have commits:**
   ```
   abc1234 Add PID controller for arm
   def5678 Fix encoder calibration
   ```
   This means you made 2 commits on your local main that aren't on the remote yet.

3. **Check if you have uncommitted changes:**
   ```bash
   git status
   ```
   - If you see "Changes not staged for commit" or "Untracked files", you have uncommitted changes
   - **Note**: You can have uncommitted changes even if you've already committed other changes to main
   - Uncommitted changes are files you've modified but haven't committed yet

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

1. **Create a new branch from your current position** (this moves your uncommitted changes to the new branch):
   ```bash
   git checkout -b feature/your-feature-name
   ```
   - Your uncommitted changes will come with you to the new branch

2. **Commit your changes on the new branch:**
   ```bash
   git add .
   git commit -m "Your commit message"
   ```

3. **Push the new branch:**
   ```bash
   git push -u origin feature/your-feature-name
   ```
   - The `-u` flag sets up upstream tracking so future pushes can use `git push`

4. **Switch back to main and verify it's clean:**
   ```bash
   git checkout main
   git status
   ```
   - Main should now be clean (no uncommitted changes)

5. **Create a Pull Request** from your feature branch as normal

---

### Solution B: Commits on Main Branch

Use this if you have already committed changes to your local main branch.

1. **Create a new branch from main** (this includes your commits and any uncommitted changes):
   ```bash
   git checkout -b feature/your-feature-name
   ```
   - Your commits are now on this new branch
   - Any uncommitted changes also come with you

3. **If you have uncommitted changes, commit them now:**
   ```bash
   git add .
   git commit -m "Your commit message"
   ```

4. **Verify all changes are committed:**
   ```bash
   git status
   ```
   - You should see: `nothing to commit, working tree clean`
   - If you see any uncommitted changes, repeat step 3 to commit them
   - This ensures all your work is safely committed before proceeding

5. **Switch back to main:**
   ```bash
   git checkout main
   ```

6. **Reset main to match the remote** (this removes your commits from local main):
   ```bash
   git reset --hard origin/main
   ```
   - ⚠️ **Warning**: This removes your commits from local main, but they're safe on your feature branch
   - This also removes any uncommitted changes from main (they're on your feature branch)

7. **Push your feature branch:**
   ```bash
   git checkout feature/your-feature-name
   git push -u origin feature/your-feature-name
   ```
   - The `-u` flag sets up "upstream tracking" so you can use `git push` in the future
   - After the first push, you can just use `git push` (no need to specify the remote and branch)

8. **Verify main is clean:**
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

9. **Create a Pull Request** from your feature branch as normal

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
- Pull the latest main branch: `git checkout main && git pull`
- Merge main into your branch: `git checkout feature/your-branch && git merge main`
- Resolve conflicts, test, and push

### "I need to update my PR"
- Just push more commits to your branch
- The PR updates automatically
- Re-request review if needed

### "I accidentally worked on main branch"
- Don't panic! Your changes aren't lost
- See "Scenario 4: Accidentally Worked on Main Branch" above for detailed steps
- Quick fix: `git checkout -b feature/your-branch` (moves uncommitted changes)
- If already committed: Create branch, then reset main with `git reset --hard origin/main`

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
```bash
# Start work
git checkout main
git pull origin main
git checkout -b feature/your-feature

# During work
git add .
git commit -m "Clear commit message"
git push -u origin feature/your-feature  # First push only (sets up tracking)
# After first push, just use: git push

# After PR is merged
git checkout main
git pull origin main
git branch -d feature/your-feature  # Delete local branch
```

### GitHub Workflow
1. Push branch → Create PR → Request review → Address feedback → Merge → Delete branch

### Branch Protection Checklist
- ✅ Require pull request before merging
- ✅ Require at least 1 approval
- ✅ Require conversation resolution
- ✅ Do not allow bypassing settings

