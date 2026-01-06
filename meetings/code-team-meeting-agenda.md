# Code Team Meeting Agenda - Beginning of Season

## Table of Contents

1. [Overview](#overview)
2. [Development Process](#2-development-process)
   - 2.1 [Requirements](#21-requirements)
   - 2.2 [Design](#22-design)
   - 2.3 [Planning, Work Tracking & Assignment](#23-planning-work-tracking--assignment)
   - 2.4 [Stand-Up Meetings](#24-stand-up-meetings)
3. [Team Organization & Management](#3-team-organization--management)
   - 3.1 [Team Structure](#31-team-structure)
   - 3.2 [Scheduling & Availability](#32-scheduling--availability)
4. [Mentor Participation](#4-mentor-participation)
   - 4.1 [Mentor Roles](#41-mentor-roles)
   - 4.2 [Code Reviews by Mentors](#42-code-reviews-by-mentors)
5. [Development Practices](#5-development-practices)
   - 5.1 [Development Methodology](#51-development-methodology)
     - 5.1.1 [Iterative Development](#511-iterative-development)
     - 5.1.2 [Collaborative Development](#512-collaborative-development)
   - 5.2 [Code Quality Standards](#52-code-quality-standards)
     - 5.2.1 [Coding Standards](#521-coding-standards)
     - 5.2.2 [Implementation Standards](#522-implementation-standards)
   - 5.3 [Version Control Workflow](#53-version-control-workflow)
     - 5.3.1 [Branching Strategy Decision](#531-branching-strategy-decision)
     - 5.3.2 [Pull Requests & Code Reviews](#532-pull-requests--code-reviews)
     - 5.3.3 [Branch Management](#533-branch-management)
     - 5.3.4 [Merge Conflicts](#534-merge-conflicts)
   - 5.4 [Quality Assurance](#54-quality-assurance)
     - 5.4.1 [Code Quality Gates](#541-code-quality-gates)
     - 5.4.2 [Continuous Integration/Continuous Deployment (CI/CD)](#542-continuous-integrationcontinuous-deployment-cicd)
   - 5.5 [Deployment Process](#55-deployment-process)
6. [Configuration Management](#6-configuration-management)
   - 6.1 [File Management](#61-file-management)
   - 6.2 [.gitignore Strategy](#62-gitignore-strategy)
7. [Testing Strategy](#7-testing-strategy)
   - 7.1 [Testing on Development Machines](#71-testing-on-development-machines)
   - 7.2 [Automated Testing](#72-automated-testing)
   - 7.3 [Testing on Robot (QA)](#73-testing-on-robot-qa)
8. [Special Topics](#8-special-topics)
   - 8.1 [Refactoring Drivebase Code](#81-refactoring-drivebase-code)
   - 8.2 [AI Usage in Code](#82-ai-usage-in-code)
   - 8.3 [WPILib Version Updates](#83-wpilib-version-updates)
   - 8.4 [Hot Fixes During Matches](#84-hot-fixes-during-matches)
9. [Research Insights: Top-Tier FRC Teams](#research-insights-top-tier-frc-teams)
10. [Best Practices from Top FRC Teams](#best-practices-from-top-frc-teams)
11. [Recommended Decisions to Make](#recommended-decisions-to-make)
12. [Next Steps After Meeting](#next-steps-after-meeting)
13. [References](#references)

---

## Overview
This agenda covers the organization, processes, and standards for the FRC code team. Topics are organized by theme to facilitate discussion and decision-making.

---

## 2. Development Process

### 2.1 Requirements
- **Requirements documentation:**
  - What do we want the robot to do?
  - Where are requirements documented? (Issues, tickets, docs?)

**Requirements Documentation Options:**
- **GitHub Issues**: Track requirements with acceptance criteria in issues
- **Markdown files**: Document requirements in `docs/requirements/` folder
- **GitHub Projects**: Organize requirements by milestone
- **Hybrid**: Use issues for tracking, markdown for formal documentation

**Decision Points:**
- Where are requirements documented?
- How detailed should requirements be?
- How do we ensure requirements are met (acceptance criteria)?

### 2.2 Design
- When is design required? (For new subsystems? Small changes?)
- How do we document designs?
- Design review process?
- Architecture decisions recorded?

**Evidence from Top FRC Teams:**

After reviewing public repositories of top FRC teams (Teams 2052, 254, 1678, 1114, 67, 2056, 1323, 3206), **no specific evidence was found of formal design documents, requirements documents, or design templates** in their public repositories. This could mean:
- They use private repositories or internal documentation systems
- They use informal design processes (whiteboard, discussions)
- Design documentation exists but isn't committed to version control
- They document designs in other locations (team wikis, Google Docs, etc.)

**Design Documentation Options:**
- **Markdown files in `docs/` folder**: Design documents as `.md` files
- **GitHub Issues**: Use issues for design discussions
- **GitHub Discussions**: For longer-form design conversations
- **Separate documentation site/wiki**: External documentation system
- **Hybrid**: Use issues for discussions, markdown for formal design docs

**Decision Points:**
- Do we want formal design documents, or is informal design sufficient?
- Should design documents be in the repository or external?
- What level of documentation is needed for different types of changes?
- When is design required? (For new subsystems? Small changes?)
- Design reviews before implementation?

### 2.3 Planning, Work Tracking & Assignment
- **Planning:**
  - Breaking down work into small increments/tickets/stories
  - Acceptance criteria for each increment
  - How to prioritize work?
  
- **Milestones & Dependencies:**
  - What are the key code team milestones?
  - Timeline for each milestone?
  - How do code milestones align with mechanical build?
  - When do we need hardware to test?
  - How do we manage dependencies on other teams (mechanical/electrical)?
  - Communication with mechanical/electrical teams
  
- **Work Tracking:**
  - How do we track work items? (GitHub Issues? Other tools?)
  - How do we link work items to code changes (PRs)?
  
- **Assignment:**
  - How are tasks assigned to team members?
  - How do we prioritize work?

**Industry Best Practices (Applicable to FRC Teams):**

While specific FRC team practices aren't publicly documented, industry best practices suggest:

1. **GitHub Issues for Work Tracking**
   - Many teams use GitHub Issues to track work items, features, and bugs
   - Issues can be linked to pull requests (e.g., "Fixes #42")
   - Supports templates for different issue types (bug, feature, task)
   - Can use labels, milestones, and projects for organization
   - Can assign issues to team members
   - Can use GitHub Projects for kanban boards and roadmaps

2. **Work Organization:**
   - Use labels to categorize (e.g., `subsystem:drivetrain`, `priority:high`, `type:feature`)
   - Use milestones to group work by goals/deadlines
   - Use projects for visual organization (kanban boards, roadmaps)
   - Break large work items into smaller issues

**Recommended Approach for FRC Teams:**

**Option 1: GitHub Issues-Based (Lightweight)**
- Create GitHub Issue templates for:
  - Feature requests (with requirements/acceptance criteria)
  - Bug reports
  - Design discussions
  - Tasks
- Use issues to track all work items
- Link PRs to issues for traceability
- Use labels to categorize (e.g., `subsystem:drivetrain`, `priority:high`)
- Assign issues to team members
- Use milestones for major goals (e.g., "Week 1: Drivetrain", "Week 2: Arm")

**Option 2: External Project Management Tools**
- Use tools like Trello, Asana, or Jira
- Link to GitHub for code integration
- More features but requires additional tool management

**Option 3: Hybrid Approach (Recommended)**
- Use GitHub Issues for code-related work tracking
- Use GitHub Projects for visual organization
- Link issues to PRs for traceability
- Use external tools only if needed for non-code work

**GitHub Issue Templates Example:**

Create `.github/ISSUE_TEMPLATE/` directory with:
- `feature_request.md` - For new features (includes requirements/acceptance criteria)
- `bug_report.md` - For bug reports
- `design_discussion.md` - For design discussions
- `task.md` - For general tasks

**Decision Points:**
- Will we use GitHub Issues for tracking work items?
- How do we assign work to team members?
- How do we prioritize work? (Labels? Milestones? Projects?)
- How do we break down large features into smaller work items?
- How do we link work items to code changes (PRs)?
- What are our key milestones and timelines?
- How do we coordinate with mechanical/electrical teams?
- How do we plan work around hardware availability?

### 2.4 Stand-Up Meetings
- Do we have daily stand-ups?
- Format: What did you do? What will you do? Blockers?
- How long? When?

---

## 3. Team Organization & Management

### 3.1 Team Structure
- **Subgroups:**
  - Drivetrain team
  - Manipulator/arm team
  - Autonomous team
  - Vision team
  - Other subsystems?

### 3.2 Scheduling & Availability
- Who is available on which days?
- How to track availability?
- "The Big Spreadsheet" - what is it? How do we use it?

---

## 4. Mentor Participation

### 4.1 Mentor Roles
- **How do mentors participate?**
  - "Show how" - demonstrate techniques
  - Pair programming with students
  - Code reviews
  - Architecture guidance
  
- **Guidance approach:**
  - How to provide guidance when team might be going wrong direction?
  - How to handle "bad decisions"?
  - When to step in vs. let students learn from mistakes?
  
- **Mentor involvement over time:**
  - Significant guidance early in season
  - Taper off as season progresses
  - Students take more ownership

### 4.2 Code Reviews by Mentors
- Do mentors review all code?
- Do mentors approve PRs?
- How to balance learning vs. code quality?

---

## 5. Development Practices

### 5.1 Development Methodology

#### 5.1.1 Iterative Development
- **Small, frequent changes:**
  - Easier to debug
  - Only implement what's needed for immediate goal
  - Test, then iterate based on results
  
- **MVP (Minimum Viable Product)**
  - Start simple, add complexity as needed
  
- **YAGNI (You Aren't Gonna Need It)**
  - Avoid over-engineering
  - Build for current needs, not hypothetical future needs

#### 5.1.2 Collaborative Development
- **Pair programming:**
  - When to pair program?
  - How are pairs assigned?
  - Benefits: knowledge sharing, code quality, learning
  
- **Group coding:**
  - When does the whole team code together?
  - How to coordinate?
  - When is group coding most effective?

### 5.2 Code Quality Standards

#### 5.2.1 Coding Standards
- **Code formatting:**
  - Spotless configuration
  - Auto-format on commit or in CI?
  
- **Naming conventions:**
  - Classes, methods, variables
  - Constants
  - Packages
  
- **Code architecture:**
  - Subsystem structure
  - Command-based architecture (WPILib)
  - Separation of concerns

#### 5.2.2 Implementation Standards
- Code standards (covered in section 5.2.1)
- Code architecture (covered in section 5.2.1)
- When to refactor vs. when to ship?

### 5.3 Version Control Workflow

#### 5.3.1 Branching Strategy Decision
**Key Question: Feature branches with PRs vs. direct commits to main?**

- **Option A: Feature branches with Pull Requests (Recommended)** [^1][^2][^3]
  - All changes go through feature branches
  - PR required for all merges to main
  - Enables code review before integration
  - Aligns with trunk-based development best practices
  - Short-lived branches (hours to days, not weeks)

- **Option B: Direct commits to main**
  - Faster for small changes
  - Requires high trust and discipline
  - Less protection against breaking changes
  - May conflict with branch protection rules

**Discussion Points:**
- Team size and experience level
- How to handle urgent fixes during matches
- Balance between speed and code quality
- Whether branch protection rules allow direct commits

#### 5.3.2 Pull Requests & Code Reviews
- **PR Requirements:**
  - What information should be included? (What, Why, Testing done)
  - PR template for consistency
  - Required reviewers before merge
  - Link to related issues/tickets

**Proposed Pull Request Template:**

Based on review of industry best practices and FRC team needs, here is a proposed pull request template:

```markdown
## What This PR Does
<!-- Describe what your changes accomplish. Be specific about what subsystems, commands, or features are affected. -->

## Why
<!-- Explain why these changes are needed. What problem does this solve? What goal does this achieve? -->

## Testing
<!-- Describe how you tested these changes. Be specific about what was tested and the results. -->

### Testing Checklist
- [ ] Code compiles without errors
- [ ] Tested in simulator (if applicable)
- [ ] Tested on robot hardware (if applicable)
- [ ] No regressions in other subsystems
- [ ] Manual testing completed (describe below)

**Testing Details:**
<!-- Provide specific details about your testing:
- What scenarios did you test?
- What were the results?
- Any issues encountered?
- Screenshots or videos (especially for robot behavior)
-->

## Related Issues
<!-- Link to related issues using #issue-number (e.g., "Fixes #42" or "Addresses #15") -->

## Screenshots/Videos (if applicable)
<!-- Add screenshots or links to videos showing the changes in action, especially for robot behavior -->

## Checklist
- [ ] Code follows team coding standards
- [ ] Code is properly commented
- [ ] Spotless formatting passes (if applicable)
- [ ] No hardcoded values or magic numbers (use constants)
- [ ] No debug print statements left in code
- [ ] Documentation updated (if applicable)
- [ ] Appropriate reviewers requested
```

**Implementation Notes:**

1. **File Location**: Create this template as `.github/PULL_REQUEST_TEMPLATE.md` in your repository
2. **Automatic Population**: 
   - **GitHub Web Interface**: When a PR template is placed in `.github/PULL_REQUEST_TEMPLATE.md`, GitHub automatically pre-fills the pull request description field with the template content when creating a new PR. Users will see the template and can fill in the required information.
   - **GitHub Desktop**: GitHub Desktop also recognizes and uses PR templates. When creating a pull request through GitHub Desktop, the description field will be pre-filled with the template content from the repository.
3. **Customization**: Adjust the checklist items based on your team's specific standards
4. **Required vs. Optional**: Consider marking some sections as required in your branch protection rules
5. **FRC-Specific**: The template includes FRC-specific testing considerations (simulator, robot hardware)

**Alternative: Multiple Templates**

GitHub supports multiple PR templates for different types of changes. You could create:
- `.github/PULL_REQUEST_TEMPLATE/feature.md` - For new features
- `.github/PULL_REQUEST_TEMPLATE/bugfix.md` - For bug fixes
- `.github/PULL_REQUEST_TEMPLATE/refactor.md` - For refactoring

When using multiple templates, GitHub will show a template picker when creating a PR, allowing contributors to choose the appropriate template.

**Note**: The template must be committed to the default branch (usually `main`) for it to be available when creating pull requests.
  
- **Code Review Process:**
  - Who reviews what?
  - Code owners for different subsystems (drivetrain, arm, autonomous, etc.)
  - What if code owner is unavailable?
  - Review turnaround time expectations
  - How to handle review feedback

**Note on Code Owners:**

After reviewing the public repositories of top FRC teams (Teams 2052, 254, 1678, 1114, 67, 2056, 1323, 3206), **no specific evidence was found of CODEOWNERS files or formal code owner assignments** in their public repositories. This could mean:
- They use private repositories for active development where such practices may exist
- They use informal code ownership (team members know who works on what)
- They don't use formal code ownership structures

However, **code ownership is a common industry best practice** that can benefit FRC teams by:
- Ensuring knowledgeable reviewers for each subsystem
- Maintaining consistency within subsystem code
- Facilitating knowledge transfer and mentorship
- Using GitHub's CODEOWNERS feature to automatically request reviews from subsystem experts

**GitHub CODEOWNERS File:**

If your team decides to use code owners, you can create a `.github/CODEOWNERS` file that automatically requests reviews from specific team members when code in certain directories changes. Example:

```
# Robot subsystems
/src/main/java/frc/robot/subsystems/drivetrain/ @team-lead @drive-team
/src/main/java/frc/robot/subsystems/arm/ @team-lead @arm-team
/src/main/java/frc/robot/commands/autonomous/ @team-lead @autonomous-team

# All code requires at least one review
* @team-lead
```

This is an optional practice that teams can adopt based on their needs and team structure.

#### 5.3.3 Branch Management
- Short-lived feature branches (aligns with trunk-based development) [^1]
- Branch naming conventions (`feature/`, `fix/`, `refactor/`)
  - Consider adding GitHub username to branch name if only a single user typically works on a branch
  - For example: `bug/jmmaloney3-auto-mode-navi-fix`
- Regular merging from main to feature branches to prevent conflicts
- Delete branches after merge

#### 5.3.4 Merge Conflicts
- Prevention strategies (frequent integration, small changes)
- Resolution process when conflicts occur
- Who resolves conflicts?

**Conflict Resolution Responsibility:**

**General Rule: The person creating the pull request is responsible for resolving conflicts.**

**Simple Conflicts:**
- The PR author (person submitting the change) resolves simple merge conflicts
- These are typically straightforward conflicts like:
  - Two people modified different parts of the same file
  - Import statement conflicts
  - Obvious merge choices (one person added code, another modified nearby code)
- The PR author should:
  1. Pull the latest `main` branch
  2. Merge `main` into their feature branch
  3. Resolve conflicts locally
  4. Test that everything still works
  5. Push the resolved changes to their branch (PR updates automatically)

**Complex Conflicts:**
- When conflicts involve complex logic, architectural decisions, or conflicting implementations:
  - The PR author should seek help from someone familiar with the conflicting code
  - **Code owners are ideal for this** - they understand the subsystem and can help make informed decisions
  - Consider pair programming the conflict resolution
  - May require discussion with the team to determine the best approach

**Best Practices:**
- **Don't merge blindly**: If you don't understand the conflicting code, ask for help
- **Test after resolving**: Always test that the resolved code still works correctly
- **Communicate**: If a conflict is complex, discuss it with the team or code owner
- **Document decisions**: For complex conflicts, consider adding a comment explaining why a particular resolution was chosen

**Prevention is Better:**
- Frequent integration (pull from `main` daily or multiple times per day)
- Small, focused changes reduce conflict likelihood
- Communication about who's working on what reduces overlapping changes

### 5.4 Quality Assurance

#### 5.4.1 Code Quality Gates
- **Spotless** - Require passing Spotless before merging to main?
- Automated checks in CI/CD pipeline
- What blocks a merge? (Tests, linting, reviews)

#### 5.4.2 Continuous Integration/Continuous Deployment (CI/CD)

**What is CI/CD?**

Continuous Integration/Continuous Deployment (CI/CD) is an automated process that validates code quality before it reaches the main branch. A CI/CD pipeline automatically:
- Compiles code to catch compilation errors
- Runs automated tests (if you have them)
- Verifies code quality checks (formatting, linting, etc.)
- Prevents broken code from being merged to main

**Why CI/CD is Critical for "Always Deployable"**

Without automated checks:
- ❌ Broken code can be merged if reviewers miss compilation errors
- ❌ Tests might not be run consistently before merging
- ❌ Main branch can become broken, blocking all team members
- ❌ No automated verification that code is actually deployable

With CI/CD:
- ✅ Every PR is automatically checked for compilation errors
- ✅ Tests run automatically on every change
- ✅ Main branch stays healthy and deployable
- ✅ Issues are caught before they reach main
- ✅ Developers get immediate feedback when they push code

**How CI/CD Works**

The CI/CD pipeline runs automatically:
- **On feature branches**: Gives developers immediate feedback when they push code, catching issues early
- **On pull requests**: Ensures code is verified before merging to main
- **On main branch**: Validates that main stays healthy after merges

**Proposed CI/CD Configuration**

The following GitHub Actions workflow file (`.github/workflows/ci.yml`) provides automated build and test validation:

```yaml
name: CI

on:
  pull_request:
    branches: [ main ]
  push:

jobs:
  build:
    runs-on: ubuntu-latest
    # Skip CI if commit message contains [skip ci] or [ci skip] (only for push events, not PRs)
    if: |
      github.event_name == 'pull_request' || 
      !contains(github.event.head_commit.message, '[skip ci]') && 
      !contains(github.event.head_commit.message, '[ci skip]')
    
    steps:
    - name: Checkout code
      uses: actions/checkout@v4
      
    - name: Set up JDK 17
      uses: actions/setup-java@v4
      with:
        java-version: '17'
        distribution: 'temurin'
        
    - name: Grant execute permission for gradlew
      run: chmod +x gradlew
      
    - name: Build with Gradle
      run: ./gradlew build
      
    - name: Run tests
      run: ./gradlew test
      
    - name: Upload test results
      if: always()
      uses: actions/upload-artifact@v4
      with:
        name: test-results
        path: build/test-results/test/
        retention-days: 7
```

**What This Workflow Does:**

1. **Triggers**: 
   - Runs on every pull request to main (catches issues before merging)
   - Runs on every push to any branch (gives immediate feedback to developers)
   - Can be skipped on feature branches by adding `[skip ci]` to commit message (PRs always run)

2. **Build Step**: Compiles your code using Gradle (catches compilation errors)

3. **Test Step**: Runs all JUnit tests (if you have any)

4. **Artifact Upload**: Saves test results for review (even if tests fail)

**Integration with Branch Protection:**

Once CI/CD is set up, you can configure branch protection rules to:
- Require CI checks to pass before merging
- Block merges if builds fail
- Ensure main branch stays deployable

**Skipping CI When Needed:**

Developers can skip CI on feature branches (but not on PRs) by adding `[skip ci]` to their commit message:
```bash
git commit -m "WIP: fixing encoder issue [skip ci]"
```

This allows pushing work-in-progress code without triggering builds, while still ensuring PRs are always checked.

**Requirements:**

- `.wpilib/wpilib_preferences.json` must be tracked in git (contains team number required by Gradle build)
- See `docs/trunk-based-dev-guide.md` for detailed setup instructions

**Decision Points:**
- Will we adopt CI/CD for automated code validation?
- Should CI checks be required before merging to main? (Recommended: Yes)
- What should trigger CI? (All pushes? Only PRs? Both?)
- Should we allow skipping CI on feature branches? (Useful for work-in-progress code)
- What checks should run? (Build only? Build + tests? Build + tests + formatting?)
- Who is responsible for maintaining the CI/CD pipeline?

**Reference:**
- See `docs/trunk-based-dev-guide.md` section "Setting Up CI/CD with GitHub Actions" for detailed setup instructions

### 5.5 Deployment Process
- **Before submitting to Git:**
  - Test on laptop/simulator
  - Run local checks (build, Spotless)
  
- **Submit to Git:**
  - Create branch (if using feature branches)
  - Create PR
  - Code review
  
- **Deploy to robot:**
  - Process for deploying approved code
  - Who deploys?
  - Verification after deployment

---

## 6. Configuration Management

### 6.1 File Management
- **Tracked in Git:**
  - **Source code** (`.java` files)
    - Examples: `Robot.java`, `Main.java`, `Drivetrain.java`, `Arm.java`, `Autonomous.java`
  - **Configuration files**
    - Examples: `build.gradle`, `settings.gradle`, `gradle.properties`, `vendordeps/*.json`
  - **Documentation**
    - Examples: `README.md`, `docs/*.md`, design documents, team guides
  - **Build configuration** (Gradle files)
    - Examples: `build.gradle`, `settings.gradle`, `gradle/wrapper/gradle-wrapper.properties`
  
- **NOT Tracked (generated/downloaded):**
  - **Compiled classes**
    - Examples: `Main.class`, `Robot.class`, `Drivetrain.class`, `build/classes/**/*.class`
  - **Build artifacts**
    - Examples: `build/libs/*.jar`, `build/jni/**/*.dylib`, `build/tmp/**`, generated source files
  - **Vendor dependencies** (handled by Gradle)
    - Examples: WPILib libraries, third-party libraries downloaded by Gradle, `~/.gradle/caches/`
  - **IDE-specific files** (unless team standardizes)
    - Examples: `.vscode/` (user settings), `.idea/`, `.classpath`, `.project`, `.settings/`

**Proposed Repository Directory Structure:**

Based on WPILib standards, current project structure, and FRC best practices, here is a recommended repository structure:

```
repository-root/
├── .github/                          # GitHub configuration
│   ├── PULL_REQUEST_TEMPLATE.md      # PR template
│   ├── CODEOWNERS                    # Code owners (optional)
│   └── workflows/                    # GitHub Actions CI/CD pipelines
│       ├── build.yml                 # Build and test workflow
│       ├── spotless.yml              # Code formatting check (if using Spotless)
│       └── deploy.yml                # Deployment workflow (optional)
│
├── .vscode/                          # VS Code settings (if team standardizes)
│   ├── settings.json                 # Shared VS Code settings
│   └── launch.json                   # Debug configurations
│
├── .wpilib/                          # WPILib configuration (ignored by git)
│
├── build/                            # Build output (ignored by git)
│
├── docs/                             # Documentation
│   ├── trunk-based-dev-guide.md
│   ├── git-commands-reference.md
│   ├── simulator-guide.md
│   └── ... (other documentation)
│
├── gradle/                           # Gradle wrapper
│   └── wrapper/
│       ├── gradle-wrapper.jar        # Tracked
│       └── gradle-wrapper.properties # Tracked
│
├── src/
│   ├── main/
│   │   ├── java/
│   │   │   └── frc/
│   │   │       └── robot/
│   │   │           ├── Main.java                    # Entry point
│   │   │           ├── Robot.java                   # Main robot class
│   │   │           │
│   │   │           ├── commands/                     # Commands
│   │   │           │   ├── autonomous/              # Autonomous commands
│   │   │           │   │   ├── AutonomousCommand.java
│   │   │           │   │   └── ...
│   │   │           │   ├── drivetrain/              # Drivetrain commands
│   │   │           │   │   ├── DriveCommand.java
│   │   │           │   │   └── ...
│   │   │           │   └── ... (other command groups)
│   │   │           │
│   │   │           ├── subsystems/                   # Subsystems
│   │   │           │   ├── Drivetrain.java
│   │   │           │   ├── Arm.java
│   │   │           │   ├── Intake.java
│   │   │           │   └── ... (other subsystems)
│   │   │           │
│   │   │           ├── constants/                    # Constants
│   │   │           │   ├── Constants.java           # Robot-wide constants
│   │   │           │   ├── DrivetrainConstants.java
│   │   │           │   └── ... (subsystem-specific constants)
│   │   │           │
│   │   │           └── util/                        # Utilities
│   │   │               ├── MathUtils.java
│   │   │               └── ... (helper classes)
│   │   │
│   │   └── deploy/                                  # Deployment files
│   │       └── README.md
│   │
│   └── test/                                        # Test code (if using)
│       └── java/
│           └── frc/
│               └── robot/
│                   └── ... (test files)
│
├── vendordeps/                                      # Vendor dependencies
│   ├── README.md
│   └── *.json                                       # Vendor dependency files
│
├── .gitignore                                       # Git ignore rules
├── build.gradle                                     # Build configuration
├── settings.gradle                                  # Gradle settings
├── gradlew                                          # Gradle wrapper (Unix)
├── gradlew.bat                                      # Gradle wrapper (Windows)
├── README.md                                        # Project documentation
└── WPILib-License.md                               # WPILib license
```

**Key Structure Decisions:**

1. **`src/main/java/frc/robot/`** - Standard WPILib package structure
   - `Main.java` - Entry point (required by WPILib)
   - `Robot.java` - Main robot class (required by WPILib)

2. **`commands/`** - Command-based architecture
   - Organized by subsystem or function (e.g., `autonomous/`, `drivetrain/`)
   - Each command is a separate file

3. **`subsystems/`** - Robot subsystems
   - One file per subsystem (e.g., `Drivetrain.java`, `Arm.java`)
   - Encapsulates hardware and provides methods for commands

4. **`constants/`** - Configuration values
   - `Constants.java` - Robot-wide constants
   - Subsystem-specific constant files (e.g., `DrivetrainConstants.java`)
   - Prevents magic numbers and hardcoded values

5. **`util/`** - Utility classes
   - Shared helper methods and utilities
   - Math functions, conversion utilities, etc.

6. **`docs/`** - Documentation
   - Team guides, tutorials, references
   - Process documentation

7. **`meetings/`** - Meeting notes
   - Agendas, meeting notes, decisions

8. **`.github/`** - GitHub configuration
   - PR templates, CODEOWNERS file (if used)

**Alternative Structure Considerations:**

- **Flat commands structure**: Some teams put all commands in one `commands/` folder without subdirectories
  - Simpler for small teams
  - Can become cluttered as project grows
- **Feature-based organization**: Organize by feature rather than subsystem
  - Useful for large, complex robots
  - Can make code harder to find

**Recommendation:** Start with the subsystem-based structure shown above. It scales well and aligns with WPILib's command-based architecture.

**Decision Points:**
- What files should be tracked vs. generated?
- When do we need to commit generated files? (Rare cases)
- Should IDE settings (`.vscode/`) be committed for team consistency?
- Do we want to organize commands by subsystem or keep them flat?
- Do we want separate constant files per subsystem or one large Constants.java?

### 6.2 .gitignore Strategy
- Generated files should NOT be committed (`.class` files, build artifacts)
- Exception: When do we need to commit generated files? (Rare cases)
- Keep `.gitignore` comprehensive and up-to-date
- **Purpose**: Implements the file management decisions from section 6.1

**Proposed `.gitignore` File:**

Based on review of FRC team repositories and WPILib best practices, here is a comprehensive `.gitignore` file for FRC Java/Gradle projects:

```gitignore
# Apple file system
**/.DS_Store

# Java class files
**/*.class

# Build directories (Gradle)
build/
bin/

# Gradle
.gradle/
gradle-app.setting
!gradle-wrapper.jar
!gradle-wrapper.properties

# IDE - IntelliJ IDEA
.idea/
*.iml
*.iws
*.ipr
out/

# IDE - Eclipse
.classpath
.project
.settings/
bin/

# IDE - VS Code (optional - uncomment if you want to ignore user-specific settings)
# .vscode/

# WPILib
.wpilib/*
# But track wpilib_preferences.json (needed for CI/CD builds)
!.wpilib/wpilib_preferences.json

# Simulator runtime files
networktables.json
simgui*.json

# JVM crash logs
hs_err_pid*.log

# OS files
Thumbs.db
.DS_Store

# Temporary files
*.tmp
*.bak
*~

# Logs
*.log

# Editor backup files (Vim/Emacs)
*.swp    # Vim swap files
*.swo    # Vim swap files (alternate)
*~       # Backup files created by Vim, Emacs, and other editors

# Secrets and credentials (if any)
*.env
*.key
*.pem
secrets.properties
```

**Notes on `.gitignore` Entries:**

- **Build artifacts** (`build/`, `bin/`, `*.class`): Never commit compiled code - it's generated by Gradle
- **Gradle wrapper** (`!gradle-wrapper.jar`, `!gradle-wrapper.properties`): The `!` prefix means "don't ignore" - these should be committed
- **IDE settings**: Consider whether to commit `.vscode/` - some teams commit shared settings, others ignore all IDE configs
- **WPILib files** (`.wpilib/*`): Most WPILib configuration files shouldn't be committed, but `wpilib_preferences.json` must be tracked for CI/CD builds (contains team number required by Gradle)
- **Simulator files** (`networktables.json`, `simgui*.json`): Runtime configuration files generated by the simulator
- **JVM crash logs**: Generated when Java crashes, should never be committed
- **OS files**: System-generated files that vary by operating system

**Team Decision Needed:**
- Should `.vscode/` be ignored or committed? (Some teams commit shared VS Code settings for consistency)
- Are there any team-specific files that should be ignored? (e.g., team-specific config files, local test data)

---


## 7. Testing Strategy

### 7.1 Testing on Development Machines
- **Smoke tests / Sanity checks:**
  - What basic functionality should always work?
  - Can we automate these checks?
  
- **Simulator usage:**
  - When to use simulator?
  - What can be tested in simulator?
  - Limitations of simulator testing

**Evidence from Top FRC Teams:**

After reviewing public repositories of top FRC teams, **specific evidence of WPILib simulator usage in their development workflows is not publicly documented**. However, WPILib provides robust simulation capabilities that many teams likely utilize.

**WPILib Simulator Capabilities:**

1. **Drivetrain Simulation**
   - ✅ **Fully supported** - Can simulate tank drive, swerve drive, mecanum drive
   - Can test drive commands, path following, odometry
   - Validates kinematics and control algorithms
   - Can test autonomous path following

2. **Mechanism Simulation (Elevator, Arm, etc.)**
   - ✅ **Supported** - Can simulate mechanisms like elevators, arms, and other linear/rotary mechanisms
   - Requires creating mechanism models (physics-based or simplified)
   - Can test PID controllers, motion profiles, and control logic
   - Can validate mechanism behavior without physical hardware
   - **Note**: Requires more setup than drivetrain simulation

3. **Autonomous Mode Validation**
   - ✅ **Fully supported** - Can test complete autonomous routines
   - Can validate path following, trajectory generation
   - Can test decision-making logic and state machines
   - Can run autonomous code in simulation environment
   - WPILib provides model-based validation tools for autonomous routines

4. **Sensor Simulation**
   - ✅ **Supported** - Can simulate encoders, gyros, limit switches, etc.
   - Can test sensor-based logic and decision-making
   - Can validate sensor calibration and data processing

5. **Motor Controller Simulation**
   - ✅ **Supported** - Can simulate SparkMax, TalonFX, and other motor controllers
   - Can test motor control logic without hardware
   - Can validate current limiting, closed-loop control

**What Can Be Tested in Simulator:**

**Fully Supported:**
- Drivetrain movement and control
- Path following and trajectory generation
- Autonomous routines (complete sequences)
- PID controllers and control algorithms
- Sensor readings and data processing
- Motor controller behavior
- Mechanism control (with proper modeling)

**Requires Additional Setup:**
- Complex mechanism physics (elevator, arm) - need to create physics models
- Vision processing - limited simulation support
- Field element interactions - need to model field geometry

**Limitations of Simulator Testing:**

1. **Physics Accuracy**
   - Simulator physics may not perfectly match real-world behavior
   - Friction, inertia, and mechanical play may differ
   - Battery voltage effects may not be accurately modeled

2. **Hardware-Specific Issues**
   - Cannot detect mechanical problems (binding, loose connections)
   - Cannot validate actual sensor accuracy
   - Cannot test for electrical issues

3. **Environmental Factors**
   - Cannot account for field surface variations
   - Cannot test lighting conditions for vision
   - Cannot account for real-world disturbances

4. **Complex Mechanisms**
   - Requires creating accurate physics models
   - May not capture all mechanical behaviors
   - Setup time can be significant for complex mechanisms

**Best Practices for Simulator Usage:**

1. **Use for Development**
   - Test code logic before hardware is available
   - Validate control algorithms and PID tuning
   - Test autonomous routines early in development

2. **Use for Validation**
   - Verify code compiles and runs correctly
   - Test edge cases and error handling
   - Validate autonomous sequences

3. **Don't Rely Exclusively**
   - Always validate on physical hardware
   - Use simulator as a development tool, not final validation
   - Field testing is still essential

**Recommended Workflow:**

1. **Develop in Simulator** - Write and test code in simulation
2. **Validate Logic** - Ensure algorithms work correctly
3. **Test on Hardware** - Deploy to robot for real-world validation
4. **Iterate** - Use simulator for quick iterations, hardware for final validation

**Decision Points:**
- Will we use the simulator for development?
- What mechanisms will we simulate? (Drivetrain? Elevator? Arm?)
- Will we use simulator for autonomous validation?
- How much time will we invest in simulator setup vs. hardware testing?

### 7.2 Automated Testing
- **What can be tested without hardware?**
  - Unit tests for calculations (PID, kinematics)
  - Logic tests for state machines
  - Integration tests in simulator
  
- **CI/CD Pipeline:**
  - Run Gradle build to ensure code compiles
  - Run automated tests
  - Run Spotless checks
  - What happens if tests fail?

**Evidence from Top FRC Teams:**

After reviewing public repositories of top FRC teams (Teams 2052, 254, 1678, 1114, 67, 2056, 1323, 3206), **no specific evidence was found of automated test suites, JUnit test files, or CI/CD pipelines running automated tests** in their public repositories. This could mean:
- They use private repositories for active development where tests may exist
- Tests exist but aren't committed to version control
- They use different testing approaches (manual testing, Test Mode, simulation)
- Automated testing isn't widely adopted in the FRC community

**WPILib Testing Capabilities:**

WPILib provides support for automated testing:

1. **JUnit Framework Support**
   - WPILib projects can use JUnit for unit testing
   - Tests can be written in `src/test/java/` directory
   - Standard Gradle test task can run JUnit tests
   - Documentation: [WPILib Unit Testing](https://docs.wpilib.org/en/stable/docs/software/wpilib-tools/robot-simulation/unit-testing.html)

2. **Test Mode (Interactive Testing)**
   - WPILib provides a "Test Mode" for interactive subsystem testing
   - Allows testing motors, sensors, and components through LiveWindow
   - Useful for hardware validation but not automated

3. **Simulation Testing**
   - WPILib simulation can be used for integration testing
   - Allows testing code without physical hardware
   - Can test control algorithms and sensor integration

**Industry Best Practices (Applicable to FRC):**

1. **Testing Frameworks:**
   - **JUnit** - Standard Java testing framework (works with WPILib)
   - Can be integrated into Gradle build process
   - Tests run with `./gradlew test` command

2. **What to Test (Without Hardware):**
   - **Calculations**: PID controllers, kinematics, math utilities
   - **Logic**: State machines, command sequences, decision trees
   - **Data Structures**: Custom classes, data handling
   - **Constants**: Verify constant values are correct
   - **Unit Conversions**: Angle conversions, unit conversions

3. **CI/CD Integration:**
   - Run tests automatically on every commit/PR
   - Fail builds if tests fail
   - Provide test results in PR comments
   - Can use GitHub Actions or other CI/CD tools

4. **Local Testing:**
   - Developers should run tests locally before committing
   - `./gradlew test` runs all tests
   - Can run specific tests: `./gradlew test --tests "ClassName"`

**Recommended Testing Approach:**

**Minimal Viable Testing:**
1. **Build Verification**: At minimum, ensure code compiles (Gradle build)
2. **Calculation Tests**: Test PID controllers, kinematics, math utilities
3. **Logic Tests**: Test state machines and decision logic
4. **CI/CD Integration**: Run tests in GitHub Actions on every PR

**Example Test Structure:**
```
src/
├── main/java/frc/robot/
│   └── ... (robot code)
└── test/java/frc/robot/
    ├── subsystems/
    │   └── DrivetrainTest.java
    ├── util/
    │   └── MathUtilsTest.java
    └── commands/
        └── AutonomousCommandTest.java
```

**What Can Be Tested with JUnit in WPILib:**

1. **Calculations and Math**
   - ✅ PID controller calculations
     - *Example tests*: Verify PID output for given error, test integral windup prevention, validate derivative calculation
   - ✅ Kinematics (swerve, tank drive calculations)
     - *Example tests*: Convert robot velocity to wheel speeds, verify swerve module angles, test tank drive calculations
   - ✅ Unit conversions
     - *Example tests*: Degrees to radians, encoder ticks to distance, velocity conversions
   - ✅ Math utilities
     - *Example tests*: Clamping values to ranges, deadband calculations, angle normalization
   - ✅ Trajectory generation
     - *Example tests*: Generate paths between points, verify trajectory constraints, test path smoothing

2. **Logic and State Machines**
   - ✅ Command state machines
     - *Example tests*: Verify state transitions (IDLE → RUNNING → FINISHED), test state conditions, validate state completion
   - ✅ Decision trees
     - *Example tests*: Test autonomous decision-making based on sensor inputs, verify conditional logic paths, test game piece detection logic
   - ✅ Autonomous routine logic
     - *Example tests*: Verify autonomous sequence order, test routine selection logic, validate timing and sequencing
   - ✅ Conditional logic
     - *Example tests*: Test safety limit checks, verify boundary conditions, test error handling logic

3. **Subsystems (With Mocked Hardware)**
   - ✅ Subsystem initialization
     - *Example tests*: Verify subsystems start in correct state, test default values, validate hardware initialization
   - ✅ Subsystem methods (with mocked motors/sensors)
     - *Example tests*: Test setTargetPosition() sets correct motor commands, verify getPosition() reads encoder correctly, test periodic() updates correctly
   - ✅ Control logic within subsystems
     - *Example tests*: Verify PID control responds to position errors, test limit switch safety logic, validate closed-loop control behavior
   - ✅ State management
     - *Example tests*: Test subsystem state transitions, verify state persistence, test state reset functionality

4. **Commands (With Mocked Hardware)**
   - ✅ Command initialization
     - *Example tests*: Verify command sets up correctly, test initial conditions, validate command scheduling
   - ✅ Command execution logic
     - *Example tests*: Test drive command responds to joystick input correctly, verify elevator command moves to target, test command behavior with different inputs
   - ✅ Command state transitions
     - *Example tests*: Verify command completes when target reached, test command cancellation, validate command end conditions
   - ✅ Command scheduling
     - *Example tests*: Test command interruption when new command scheduled, verify command queuing, test parallel command execution

**Mocking Hardware for Testing:**

WPILib provides mock classes that allow you to simulate hardware inputs and outputs:

1. **Mocking Joystick Inputs**
   - Use `MockJoystick` or create mock implementations
   - Set joystick axis values: `joystick.setX(0.5)`, `joystick.setY(-0.3)`
   - Set button states: `joystick.setButton(1, true)`
   - Test how commands/subsystems respond to joystick inputs

2. **Mocking Sensors**
   - Mock encoders: Set encoder position/velocity values
   - Mock gyros: Set angle values
   - Mock limit switches: Set switch states (pressed/not pressed)
   - Mock distance sensors: Set distance readings
   - Example: `encoder.setPosition(100)` to simulate encoder reading

3. **Mocking Motors**
   - Mock motor controllers: Check motor output values
   - Verify motor speed/voltage commands
   - Test closed-loop control (PID) responses
   - Example: `motor.get()` to verify motor output after command execution

4. **Mocking Subsystems**
   - Create mock implementations of subsystems
   - Test commands that use subsystems
   - Verify subsystem method calls

**Validating System Responses:**

1. **Motor Output Validation**
   - After executing a command, check motor output values
   - Verify motors are set to expected speeds/voltages
   - Test PID controller output: `assertEquals(expectedSpeed, motor.get(), tolerance)`
   - Example: Drive forward command should set left/right motors to expected values

2. **Subsystem State Validation**
   - Verify subsystem reaches target states
   - Check position/velocity after movement commands
   - Validate elevator reaches target height: `assertEquals(targetHeight, elevator.getPosition(), tolerance)`
   - Validate arm reaches target angle: `assertEquals(targetAngle, arm.getAngle(), tolerance)`

3. **Sensor Reading Validation**
   - Verify sensors are read correctly
   - Test sensor-based decision making
   - Validate sensor calibration

4. **Command Completion Validation**
   - Verify commands complete when conditions are met
   - Test command scheduling and cancellation
   - Validate command state transitions

**Example Test Structure:**

```java
@Test
public void testDriveForward() {
    // Setup: Create mock hardware
    MockJoystick joystick = new MockJoystick();
    MockMotor leftMotor = new MockMotor();
    MockMotor rightMotor = new MockMotor();
    
    // Create subsystem with mocked hardware
    Drivetrain drivetrain = new Drivetrain(leftMotor, rightMotor);
    
    // Create command
    DriveCommand command = new DriveCommand(drivetrain, joystick);
    
    // Execute: Set joystick input
    joystick.setY(0.5);  // Forward
    command.execute();
    
    // Validate: Check motor outputs
    assertEquals(0.5, leftMotor.get(), 0.01);
    assertEquals(0.5, rightMotor.get(), 0.01);
}

@Test
public void testElevatorRise() {
    // Setup: Mock elevator hardware
    MockMotor elevatorMotor = new MockMotor();
    MockEncoder elevatorEncoder = new MockEncoder();
    
    Elevator elevator = new Elevator(elevatorMotor, elevatorEncoder);
    RaiseElevatorCommand command = new RaiseElevatorCommand(elevator, 100.0);
    
    // Execute: Run command
    command.initialize();
    command.execute();
    // Simulate time passing
    for (int i = 0; i < 100; i++) {
        command.execute();
        elevator.periodic();
    }
    
    // Validate: Check elevator reached target
    assertEquals(100.0, elevatorEncoder.getPosition(), 1.0);
}
```

**Limitations of JUnit Testing:**

1. **Hardware Abstraction Required**
   - Code must use WPILib's hardware abstraction (not direct hardware access)
   - Subsystems must accept motor/sensor objects (dependency injection)
   - Cannot test code that directly accesses hardware

2. **Physics Simulation**
   - JUnit tests don't simulate physics (gravity, friction, inertia)
   - Motor commands execute instantly (no acceleration/deceleration)
   - For physics simulation, use WPILib simulator instead

3. **Real-Time Behavior**
   - Tests run instantly, don't simulate real-time robot behavior
   - Cannot test timing-dependent behavior accurately
   - Use simulator for time-based testing

**Best Practices:**

1. **Design for Testability**
   - Use dependency injection (pass motors/sensors to constructors)
   - Separate logic from hardware access
   - Use interfaces where possible

2. **Test Logic, Not Hardware**
   - Focus on testing control logic and algorithms
   - Don't try to test hardware itself (that's what Test Mode is for)
   - Test that correct commands are sent to hardware

3. **Use Simulator for Integration Testing**
   - JUnit for unit tests (logic, calculations)
   - Simulator for integration tests (full subsystem behavior)
   - Hardware for final validation

**Decision Points:**
- Will we write automated tests? (Even simple ones help)
- What level of test coverage do we want?
- Should tests run locally before committing?
- Should CI/CD require tests to pass before merging?
- What types of tests are most valuable for our team?
- Will we design code for testability (dependency injection)?
- Will we have dedicated "test automation" engineers?
- What's the balance between JUnit tests vs. simulator tests vs. hardware tests?

### 7.3 Testing on Robot (QA)
- **Test script/checklist:**
  - Standard test procedure before deploying
  - Verify all features still work
  - Update test script as features are added
  
- **Who performs robot testing?**
- **When is code "ready" for robot?**

**Evidence from Top FRC Teams:**

After reviewing public repositories and documentation of top FRC teams (Teams 2052, 254, 1678, 1114, 67, 2056, 1323, 3206), **no specific evidence was found of:**
- Formal QA processes documented in public repositories
- Test scripts or checklists committed to version control
- Dedicated QA engineer roles
- Mandatory robot hardware testing before merging to main

This could mean:
- QA processes exist but aren't publicly documented
- Testing procedures are informal or verbal
- Test scripts exist but aren't in version control
- Teams use different approaches to QA

**Industry Best Practices (Applicable to FRC Teams):**

1. **Testing Before Merge to Main**
   - **Recommended**: Test on robot hardware before merging to main when possible
   - **Reality Check**: May not always be feasible (hardware availability, time constraints)
   - **Alternative**: Test on feature branch, then merge after validation
   - **Balance**: Weigh the need for testing against development speed

2. **Regression Test Scripts**
   - **Value**: Test scripts ensure consistent validation of all features
   - **Format**: Can be:
     - Markdown checklist in repository (`docs/test-checklist.md`)
     - GitHub Issue template for test results
     - Automated test suite (if feasible)
     - Simple text file with test steps
   - **Content**: Should include:
     - Basic functionality checks (drivetrain moves, sensors read)
     - Subsystem-specific tests (arm extends, elevator raises)
     - Autonomous routine validation
     - Safety checks (emergency stop, limit switches)

3. **QA Responsibilities**
   - **Dedicated QA Engineers**: Uncommon in FRC teams (resource constraints)
   - **Shared Responsibility**: All team members participate in QA
   - **Rotating QA Role**: Assign different team members to perform testing
   - **Code Owner Testing**: Subsystem owners test their subsystems
   - **Mentor Oversight**: Mentors may oversee QA process

**Recommended QA Approach for FRC Teams:**

**Option 1: Lightweight (Recommended for Most Teams)**
- Test on feature branch before creating PR
- PR author performs basic validation
- Reviewer may request additional testing
- Test on main branch after merge (regression testing)
- Use simple checklist (not necessarily in code)

**Option 2: Formal (For Larger Teams)**
- Create test checklist in `docs/test-checklist.md`
- Require test results in PR description
- Designate specific team members for QA
- Test on robot before merging critical changes
- Maintain test script that grows with features

**Option 3: Hybrid**
- Test critical changes on robot before merge
- Use test checklist for major releases/competitions
- Informal testing for small changes
- Formal regression testing before competitions

**Test Checklist Template:**

```markdown
# Robot Test Checklist

## Pre-Deployment
- [ ] Code compiles without errors
- [ ] Simulator testing completed (if applicable)
- [ ] Code review approved

## Basic Functionality
- [ ] Robot initializes correctly
- [ ] Drivetrain responds to joystick input
- [ ] All subsystems initialize without errors
- [ ] Emergency stop functions correctly

## Subsystem Tests
- [ ] Drivetrain: Forward/backward movement
- [ ] Drivetrain: Turning (left/right)
- [ ] [Subsystem Name]: [Specific test]
- [ ] [Subsystem Name]: [Specific test]

## Autonomous
- [ ] Autonomous mode selects correctly
- [ ] Autonomous routine executes without errors
- [ ] Path following works (if applicable)

## Safety
- [ ] Limit switches function correctly
- [ ] Emergency stop works
- [ ] No unexpected movements on startup
```

**Decision Points:**
- Do we test on robot before merging to main? (Always? Sometimes? Never?)
- Will we maintain a formal test checklist/script?
- Who is responsible for robot testing? (PR author? Reviewer? Designated tester?)
- How do we handle testing when hardware isn't available?
- What level of testing is required for different types of changes?
- Do we need formal regression testing, or is informal testing sufficient?

---

## 8. Special Topics

### 8.1 Refactoring Drivebase Code
- Is this a specific project?
- When to refactor vs. when to ship?
- How to plan refactoring work?

### 8.2 AI Usage in Code
- **When is AI appropriate?**
  - Code generation?
  - Debugging help?
  - Documentation?
  
- **Guidelines:**
  - Always review AI-generated code
  - Understand what AI code does
  - Don't blindly copy-paste
  - Use AI as a tool, not a replacement for learning

### 8.3 WPILib Version Updates
- **Upgrading to new WPILib version:**
  - Use AI for first pass? (With team code review)
  - Manual upgrade process?
  - Testing after upgrade?
  - When to upgrade? (During season vs. off-season)

### 8.4 Hot Fixes During Matches
- **Process for urgent fixes:**
  - How to handle critical bugs during competition?
  - Quick code review process?
  - Override branch protection rules? (If using them)
  - Emergency deployment process?
  
- **Prevention:**
  - How to reduce need for hot fixes?
  - Better testing before matches?

---

## Research Insights: Top-Tier FRC Teams

Based on research into how top-performing FRC teams organize:

### Key Practices:
1. **Trunk-Based Development with Short-Lived Feature Branches** [^1][^2][^3]
   - Feature branches last hours to days, not weeks
   - Frequent integration (multiple times per day)
   - Reduces merge conflicts significantly

2. **Code Reviews via Pull Requests** [^3][^4]
   - Even in trunk-based development, PRs are used for reviews
   - Small, focused PRs for quick reviews
   - Knowledge sharing through reviews

3. **Continuous Integration** [^2][^5]
   - Automated tests run before every commit/merge
   - Build must pass before merging
   - Catches issues early

4. **Feature Flags (Advanced)** [^6]
   - Some teams use feature flags to integrate incomplete features
   - Allows work-in-progress code in main without affecting stability
   - May be overkill for smaller teams

5. **Clear Ownership**
   - Code owners for different subsystems
   - Clear responsibility for different areas

6. **Testing Strategy**
   - Unit tests for calculations and logic
   - Simulator testing for integration
   - Robot testing for final validation

---

## Best Practices from Top FRC Teams

Based on review of publicly available resources from top-performing FRC teams, here are observed best practices:

### Team 2052 - KnightKrawler [^7][^8]

**Observations:**
- **Open Source Contributions**: Team maintains open-source projects (e.g., FRC-Krawler scouting app) demonstrating commitment to code quality and community contribution
- **Modular Architecture**: Separate repositories for different projects (scouting app, robot code, website) suggests modular design approach
- **Version Control Organization**: Well-organized GitHub organization with clear repository naming conventions (year-based: `2025-Reefscape`, `2024-Crescendo`)

**Key Practices:**
- Maintain separate repositories for different systems (scouting vs. robot code)
- Use consistent naming conventions for season-based repositories
- Open source tools benefit the broader FRC community

### Team 3206 - Royal T-Wrecks [^9][^10]

**Observations:**
- **Simulation-First Development**: Team actively uses simulation for development (SparkMax simulation samples, swerve drive simulation)
- **Code Examples and Resources**: Publicly shares code examples and resources, indicating strong documentation practices
- **Epilogue Logging**: Adoption of modern WPILib features (Epilogue annotation-based logging) shows commitment to staying current with best practices
- **Pathfinding Development**: Active development of on-the-fly pathfinding solutions demonstrates advanced autonomous capabilities

**Key Practices:**
- **Simulation Testing**: Heavy emphasis on simulation before hardware testing
  - SparkMax simulation for motor controllers
  - Swerve drive simulation
  - Flywheel simulation examples
- **Modern Tooling**: Quick adoption of new WPILib features and capabilities
- **Knowledge Sharing**: Public code repositories serve as learning resources

### Common Practices Across Top Teams

Based on analysis of multiple top-tier FRC teams (Teams 254, 1678, 1114, 67, 2056, 1323, 2052, 3206):

1. **GitHub Organization Structure** [^7][^8][^11]
   - Year-based repository naming (e.g., `2025-Reefscape`, `2024-Crescendo`)
   - Separate repositories for different systems when appropriate
   - Clear organization of code, CAD, and documentation

2. **Simulation and Testing** [^9][^10]
   - Extensive use of simulation before hardware deployment
   - Motor controller simulation (SparkMax, TalonFX)
   - Drivebase simulation (swerve, tank)
   - Integration testing in simulated environments

3. **Code Quality Standards**
   - Consistent code formatting and structure
   - Modern WPILib feature adoption
   - Well-documented code examples

4. **Modular Design**
   - Separation of concerns (drivetrain, manipulators, autonomous)
   - Reusable components across seasons
   - Clear subsystem boundaries

5. **Documentation and Knowledge Sharing**
   - Public code repositories (when appropriate)
   - Code examples and tutorials
   - Clear README files and documentation

6. **Version Control Best Practices**
   - Organized repository structure
   - Clear commit history
   - Tagged releases for competition code

### Trunk-Based Development and Code Review Practices

**Evidence from Pull Request Analysis:**

After reviewing the GitHub repositories of the top FRC teams, here is what we found regarding pull request usage:

**Team 2052 (KnightKrawler) - Strong Evidence of Pull Request Usage** [^7][^13]
- **Repository**: `2024-Crescendo`
- **Pull Requests**: **84 closed pull requests** (0 open at time of review)
- **Evidence**: Extensive use of pull requests throughout the 2024 season
- **Multiple Contributors**: Pull requests created by multiple team members (e.g., caleb-fynewever, MrNosnaws, MasonLilley, afomiamesfin, bherbst, Augustus-Schendel)
- **Conclusion**: Team 2052 clearly uses pull requests as a standard part of their development workflow

**Other Teams - Limited Public Evidence:**
- Most other top teams' repositories are either private or their public repositories don't show pull request history
- Some teams may use private repositories for active development
- Public repositories may be cleaned/archived versions that don't show development history

**What We Can Observe from Team 2052's Example:**
- **Extensive Pull Request Usage**: 84 PRs in a single season repository indicates pull requests are a core part of their workflow
- **Multiple Contributors**: Multiple team members creating PRs suggests collaborative development
- **Regular Integration**: The volume of PRs suggests frequent, small changes being integrated
- **Feature Branch Pattern**: PR titles suggest feature-based branches (e.g., "lobbin'", "four cameras", "automatic feed while moving")

**What We Cannot Determine from Public Repositories:**
- Whether branch protection rules are enabled on main branches
- Specific code review standards and requirements
- Whether direct commits to main are allowed (though 84 PRs suggests they're not the primary method)
- Exact branching strategy (though PR usage suggests feature branches)

**Evidence from Other FRC Teams:**

One documented example found in research is **FRC Team 6377 (Howdy Bots)** [^12], which has publicly documented their practices:
- **Feature Branch Strategy**: They develop each feature or fix on a separate branch
- **Pull Request Workflow**: All changes go through pull requests before merging
- **Code Review Process**: Pull requests require both student and mentor reviews
- **Peer Code Reviews**: Emphasis on peer reviews to foster collaboration and learning

**Industry Best Practices (Applicable to FRC Teams):**

Based on software engineering best practices that align with trunk-based development principles [^1][^2][^3]:

1. **Short-Lived Feature Branches with PRs**
   - Feature branches exist for hours to days, not weeks
   - All merges go through pull requests
   - Branch protection prevents direct commits to main

2. **Code Review Standards**
   - Small, focused pull requests (ideally under 400 lines of code)
   - Prompt reviews (within minutes to hours, not days)
   - Required approvals before merging
   - Automated tests must pass before merge

3. **Branch Protection Rules**
   - Require pull request reviews before merging
   - Require status checks to pass (build, tests)
   - Require conversation resolution before merging
   - Prevent force pushes to main branch

**Recommendation:**

Based on concrete evidence from **Team 2052's 2024-Crescendo repository** showing 84 closed pull requests, we can confirm that at least one top-tier FRC team uses:
- **Feature branches** (evidenced by PR titles and workflow)
- **Pull request workflow** (84 PRs demonstrates this is standard practice, not occasional)
- **Multiple contributors** (different team members creating PRs)

This aligns with trunk-based development principles when combined with short-lived branches and frequent integration, which is the approach recommended in your existing trunk-based development guide.

**Key Finding**: Team 2052's extensive use of pull requests (84 in one season) provides strong evidence that top FRC teams do use pull requests as a standard part of their development process, supporting the recommendation to adopt feature branches with PRs rather than direct commits to main.

### Recommendations Based on Top Team Practices

1. **Adopt Simulation-First Development**
   - Use WPILib simulation features extensively
   - Test motor controllers, drivetrains, and subsystems in simulation
   - Reduce hardware wear and development time

2. **Organize Repositories by Season**
   - Use year-based naming: `2025-RobotName` or `2025-CompetitionName`
   - Keep historical code accessible for reference
   - Maintain separate repos for tools vs. robot code when appropriate

3. **Share Knowledge Internally and Externally**
   - Document code examples and patterns
   - Create reusable components
   - Consider open-sourcing tools that benefit the community

4. **Stay Current with WPILib**
   - Adopt new features as they become available
   - Use modern logging and simulation capabilities
   - Participate in WPILib beta testing when possible

5. **Maintain Clean Repository Structure**
   - Clear naming conventions
   - Organized folder structure
   - Comprehensive README files

---

## Recommended Decisions to Make

1. **Branching strategy** - Feature branches + PRs vs. direct commits
2. **Code review requirements** - Who reviews? Required approvals?
3. **CI/CD pipeline** - Will we adopt automated build and test validation?
4. **Code quality gates** - Spotless? Automated tests? What blocks merge?
5. **Testing strategy** - What can be automated? Simulator usage?
6. **Stand-up meetings** - Frequency and format
7. **Mentor involvement** - Roles and how it changes over time
8. **Hot fix process** - How to handle urgent fixes during matches

---

## Next Steps After Meeting

1. Document decisions in team wiki/docs
2. Set up GitHub branch protection rules (if using feature branches)
3. Create PR template
4. Set up CI/CD pipeline (if decided - see section 5.4.2 for details)
5. Create test checklist/script
6. Set up Spotless (if decided)
7. Create code owners file (if using code owners)

---

## References

[^1]: TrunkBasedDevelopment.com. "Short-Lived Feature Branches." *Trunk Based Development*. https://trunkbaseddevelopment.com/short-lived-feature-branches/

[^2]: DORA (DevOps Research and Assessment). "Trunk-Based Development." *DORA Capabilities*. https://dora.dev/capabilities/trunk-based-development/

[^3]: Marco Patino. "Pull Requests in Trunk-Based Development." *Marco Patino's Blog*. https://www.marcopatino.dev/articles/prs-trunk-based-dev

[^4]: Atlassian. "Branch Deployments in Continuous Delivery Pipelines." *Atlassian Continuous Delivery*. https://www.atlassian.com/continuous-delivery/branch-deployments-in-continuous-delivery-pipelines

[^5]: DORA (DevOps Research and Assessment). "Trunk-Based Development." *DORA Capabilities*. https://dora.dev/capabilities/trunk-based-development/

[^6]: Unleash.io. "How to Implement Trunk-Based Development: A Practical Guide." *Unleash Blog*. https://www.getunleash.io/blog/how-to-implement-trunk-based-development-a-practical-guide

[^7]: KnightKrawler Robotics (FRC Team 2052). "Team 2052 - KnightKrawler." *GitHub Organization*. https://github.com/frc2052

[^8]: KnightKrawler Robotics (FRC Team 2052). "Knightkrawler Robotics - FRC Team 2052." *Team Website*. https://www.team2052.com

[^9]: Royal T-Wrecks (FRC Team 3206). "Programming and CAD Repository." *Woodbury High School Activities*. https://www.whsactivities.org/page/show/8911756-programming-and-cad-repository

[^10]: Royal T-Wrecks (FRC Team 3206). "Robotics Club - FRC Team 3206." *Woodbury High School Activities*. https://www.whsactivities.org/robotics

[^11]: Additional top FRC teams reviewed (practices observed from public repositories and websites):
  - The Cheesy Poofs (FRC Team 254): https://www.team254.com, https://github.com/team254
  - Citrus Circuits (FRC Team 1678): https://www.citruscircuits.org, https://github.com/frc1678
  - Simbotics (FRC Team 1114): https://www.simbotics.org, https://github.com/simbotics
  - HOT Team (FRC Team 67): https://www.hotteam67.org, https://github.com/hot67
  - OP Robotics (FRC Team 2056): https://2056.ca, https://github.com/Team2056
  - MadTown Robotics (FRC Team 1323): https://team1323.com, https://github.com/Team1323

[^12]: Howdy Bots (FRC Team 6377). "2025 Howdy Bots Tech Doc." *Howdy Bots Documentation*. https://howdybots.org/wp-content/uploads/2025/03/2025-Howdy-Bots-Tech-Doc-FINAL.pdf

[^13]: KnightKrawler Robotics (FRC Team 2052). "2024-Crescendo Pull Requests." *GitHub Repository*. https://github.com/frc2052/2024-Crescendo/pulls?q= (84 closed pull requests observed)

### Additional Resources

- **Trunk-Based Development Guide**: See `docs/trunk-based-dev-guide.md` in this repository for detailed workflow procedures
- **Git Commands Reference**: See `docs/git-commands-reference.md` for common Git operations

### Notes on Research

The research findings are based on industry best practices for trunk-based development and continuous integration, which are commonly adopted by high-performing software development teams. While specific FRC team practices are not always publicly documented, these practices align with software engineering principles that scale well for collaborative development environments like FRC code teams.

For FRC-specific resources, consider:
- FIRST Robotics Competition forums and community discussions
- Team websites and GitHub repositories of top-performing teams (when publicly available)
- FRC programming documentation and best practices guides

