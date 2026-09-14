# Team Development Guidelines & Repository Rules

This document outlines our repository structure, branch protection rules, branch naming standards, and the day-to-day Scrum workflow for our 4-person team.

---

## 1. Branch Architecture & Protection Policies

| Branch | Purpose | Permissions & Protection Rules |
| :--- | :--- | :--- |
| **`main`** | **Production** | • **Strictly Admin Only**: No direct pushes from non-admins.<br>• All code updates and merges into `main` must be performed by the repository admin.<br>• Branch deletions and force pushes (`git push --force`) are blocked. |
| **`dev`** | **Staging / Integration** | • **Pull Requests Required** for team members (direct pushes blocked).<br>• **No Reviews / Approvals Required (0 approvals)**: Teammates may merge their own PRs once ready.<br>• **Admin Bypass**: The repository admin has bypass access to push directly if hotfixes or quick adjustments are needed.<br>• Branch deletions and force pushes are blocked. |
| **Feature / Ticket Branches** | **Active Work** | • Short-lived branches created off `dev`.<br>• Deleted automatically upon merging the PR into `dev`. |

---

## 2. Branch Naming Conventions

When starting a ticket, create a branch off the latest `dev` branch using the following format:

```text
<type>-<your_name>-<what_you_worked_on>
```

### Allowed Types

* `feat` — Adding a new feature, endpoint, or UI component.
* `bug` — Fixing a defect, crash, or unexpected behavior.
* `refactor` — Code cleanup, performance optimization, or restructuring with no external behavior changes.

### Examples

* `feat-alex-user_auth_modal`
* `bug-sam-login_token_expiry`
* `refactor-jordan-database_queries`

> **Note:** Keep the description brief, lowercase, and separated by underscores or dashes.

---

## 3. Pull Request (PR) Requirements

Before merging any ticket into `dev`, open a Pull Request adhering to these rules:

1. **Target Base:** Always target **`dev`** as the base branch (never target `main`).
2. **Link GitHub Issues / Work Items:**
   * Reference the related issue number in the PR description using auto-close keywords (e.g., `Closes #12`, `Fixes #45`, or `Relates to #34`).
3. **Screenshots & Media:**
   * Attach screenshots, screen recordings, or GIFs for any UI or visual updates.
   * Attach API response samples, logs, or terminal outputs for backend/schema changes when applicable.
4. **Self-Review & Merge:**
   * Since formal peer approvals are not required (0 approvals needed), do a self-review of your changes in the **Files changed** tab.
   * Verify all conversation threads or checkmarks are clean.
   * Click **Squash and merge** to keep the `dev` commit history clean.

---

## 4. Standard Scrum Team Workflow

Follow this step-by-step lifecycle for every ticket:

### Step 1: Sync Your Local Environment
Before starting a new ticket, ensure your local `dev` is up to date:
```bash
git checkout dev
git pull origin dev
```

### Step 2: Create Your Working Branch
Cut your branch off `dev` using the naming convention:
```bash
git checkout -b feat-yourname-ticket_description
```

### Step 3: Develop & Commit
Commit your work regularly with clear commit messages:
```bash
git add .
git commit -m "feat: add user authentication form validation"
```

### Step 4: Push to GitHub & Open a PR
Push your local branch to GitHub:
```bash
git push -u origin feat-yourname-ticket_description
```
1. Open the repository on GitHub and click **Compare & pull request**.
2. Ensure the base branch dropdown is set to **`dev`**.
3. Link the relevant issue number and attach screenshots/logs if applicable.

### Step 5: Merge into `dev`
Once your checks pass and you have self-verified the code, click **Squash and merge**. GitHub will automatically delete your feature branch.

### Step 6: Production Release to `main` (Admin Only)
At the end of a sprint or milestone:
1. The **repository admin** opens and reviews a PR from `dev` into `main` (or merges directly).
2. Code deployed to `main` represents the stable production release.