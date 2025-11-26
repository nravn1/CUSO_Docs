# 📘 Branching Standards — CUSO Development Workflow

This document defines the official branching, naming, and release workflow for all projects under the CUSO development organization.  
The goal is to maintain clean version control, safe deployments, and a repeatable sprint flow that scales with multiple developers.

---

## Branch Overview

Our branches follow a simple layered structure:

<img width="2674" height="733" alt="CUSOBranchChart" src="https://github.com/user-attachments/assets/e96f72be-1396-4351-a93e-923fd8b050da" />


Each branch has a clear purpose in the development lifecycle.

---

## 🔵 `main` — Production-Ready Code
- Always contains stable, deployable code.
- Protected branch — PRs required to modify it.
- Receives merges only after successful testing in each sprint.
- Every merge into `main` corresponds to a released version.

---

## 🟡 `Dev X.Y.Z` — Active Sprint Development
- Created from `main` at the start of each sprint.
- Named semantically using the target version (e.g., `Dev 1.1.0`).
- All feature branches originate from this branch.
- Serves as the integration branch for all features in the sprint.
- Renamed Rollback after it is merged back into main (e.g. `Rollback 1.1.0`).
---

## 🟢 `Feature-name` — Code Modification
- Created from `Dev X.Y.Z` when adding a new feature.
- Named based on the feature added with a prefix of `Feature-`.
- Sync often with Dev to avoid merge conflicts.
- Delete branch after it is merged back into Dev.
---

## 🟠 `Test X.Y.Z` — Sprint Testing & Stabilization
- Created from the matching Dev branch (e.g., `Test 1.1.0`).
- No new features are added here.
- Used strictly for:
  - QA testing
  - small fixes
  - verifying stability before release
- Bug branches are created from here.

---

## 🔴 `Bug-name` — Hot Bug Fix Branches
- Created when a bug is discovered during testing.
- Based off the Test branch.
- Named:

```
Bug-name
```

- `name` should be a short description (example: `Bug-login-error`).
- Merged back into Test and deleted once resolved.

---

## ** Rollback Branch Creation**
After merging into main:

```
Dev 1.1.0 → Rollback 1.1.0
```

This becomes the rollback branch for emergency reference.  
No changes should be made to rollback branches.

---

---

# Branch Summary Table

| Branch Type | Example Name | Created From | Purpose | Allowed Changes |
|------------|--------------|--------------|---------|-----------------|
| **Main** | `main` | — | Production code | Release merges only |
| **Dev** | `Dev 1.2.0` | `main` | Active development | Feature merges |
| **Feature** | `Feature-login` | `Dev X.Y.Z` | Add new functionality | Anything for feature |
| **Test** | `Test 1.2.0` | `Dev X.Y.Z` | QA testing & stabilization | Bug merges |
| **Bug** | `Bug-name` | `Test X.Y.Z` | Fix issues found in testing | Targeted fixes |
| **Rollback** | `Rollback 1.1.0` | Former Dev | Emergency fallback | No changes |

---

# Versioning

We use **Semantic Versioning**:

```
MAJOR.MINOR.PATCH
```

Examples:
- `1.1.0` – Minor release (new features)
- `1.1.1` – Patch release (bug fixes)
- `2.0.0` – Major release (significant changes)

---



Use this document as the authoritative guide for all branching activity.
