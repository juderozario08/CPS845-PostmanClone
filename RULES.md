# Team Development Guidelines & Repository Rules

This document outlines our repository branching policies, branch naming standards, pull request conventions, and the day-to-day Scrum workflow for our 4-person team.

---

## 1. Branch Architecture & Protection Policies

Our repository maintains two permanent primary branches: `main` and `dev`.

| Branch | Role | Rules & Permissions |
| :--- | :--- | :--- |
| **`main`** | **Production** | • **PR Required**: All updates must come through a Pull Request. Direct pushes are blocked.<br>• **Source**: Merges into `main` should only originate from `dev`.<br>• **Permanent**: This branch can **never** be deleted.<br>• Anyone on the team can merge the PR once ready. |
| **`dev`** | **Staging / Integration** | • **PR Required**: All ticket work must be merged into `dev` through a Pull Request. Direct pushes are blocked.<br>• **Permanent**: This branch can **never** be deleted.<br>• No peer approvals are required; authors can merge their own PRs once ready. |

> **Note on Enforcement:** Aside from requiring a Pull Request for updates, blocking direct pushes, and preventing branch deletion on `dev` and `main`, no other restrictions or review approval thresholds are enforced.

---

## 2. Branch Naming Conventions

When picking up a ticket or task, create a dedicated branch cut from the latest `dev`. 

Branches must follow the pattern:
```
<type>-<your_name>-<what_you_worked_on>
```

### Allowed Branch Types
* **`feat-`**: New features, UI additions, or functionality.
* **`bug-`**: Fixes for existing issues, defects, or broken functionality.
* **`refactor-`**: Code restructuring, cleanup, performance enhancements, or technical debt removal without changing user-facing behavior.

### Examples
* `feat-alex-user-authentication`
* `bug-sam-cart-checkout-crash`
* `refactor-jordan-api-service-layer`

---

## 3. Pull Request Guidelines

Whenever you are ready to integrate your changes into `dev` (or when staging changes are prepared for `main`), open a Pull Request.

### What to Include in Every PR
1. **Clear Description**: Briefly explain the changes made and the problem solved.
2. **Linked Work Items**: Directly link the corresponding GitHub issue or ticket (e.g., `Closes #12` or `Resolves #45`) so the project board updates automatically.
3. **Attachments & Proof**:
   * For frontend/UI changes: Attach screenshots, GIFs, or short screen recordings demonstrating the change.
   * For backend/API changes: Include console output, test run logs, or Postman/cURL responses showing success.

---

## 4. Daily Scrum Workflow

1. **Sync Local Workspace**
   Always make sure your local staging branch is up to date before starting:
   ```bash
   git checkout dev
   git pull origin dev
   ```

2. **Create a Working Branch**
   ```bash
   git checkout -b feat-<your_name>-<what_you_worked_on>
   ```

3. **Develop & Commit**
   Keep commit messages concise and descriptive:
   ```bash
   git add .
   git commit -m "feat: implement user login form validation"
   ```

4. **Push Branch & Open PR to `dev`**
   ```bash
   git push -u origin feat-<your_name>-<what_you_worked_on>
   ```
   * Open a PR on GitHub with the base set to **`dev`**.
   * Fill out the description, link your issue, and attach media/verification proofs.
   * Merge your PR into `dev` once finished.

5. **Release to `main`**
   * Periodically, after features are validated together on `dev`, open a PR from **`dev`** into **`main`**.
   * Any team member can merge this PR into `main` to deploy or release to production.