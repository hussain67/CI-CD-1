# Protect the main branch (MOST IMPORTANT)

Steps

Go to GitHub repo → Settings

Click Branches

Under Branch protection rules, click Add rule

Set Branch name pattern:

main

Enable these options ✅

✔ Require a pull request before merging
✔ Require approvals (1 or more)
✔ Require status checks to pass before merging
✔ Require branches to be up to date before merging
✔ Restrict who can push to matching branches (leave empty)

❌ Do NOT allow direct pushes

This alone blocks git push origin main for everyone.

# Close the Pull Request (Most common)

This is the correct way.

Via GitHub UI

Open the Pull Request

Click Close pull request

# MERGE CONFLICT

      Scenario

      You have a feature branch locally:

      feature/login: A---B---C
      main:         D---E

      You pushed the feature branch and opened a Pull Request on GitHub.

      You merged the PR on GitHub → now remote main has your commits:

      origin/main: D---E---A---B---C

Your local main is still behind:
Option A — If you have local commits on main

      local main: D---E

      Step 1: Switch to your local main branch
      git checkout main

      Step 2: Update local main from GitHub
      Option A — Fast-forward (if no local commits on main)
      git pull origin main

      Git will fast-forward local main to match remote main.

      Local main becomes:

      local main: D---E---A---B---C

      ✅ Clean, linear history

Option B — If you have local commits on main

If you made commits on local main before pulling, fast-forward may fail. You’ll see:
fatal: Not possible to fast-forward, aborting.

Solutions:

      1️⃣ Rebase your local commits
      git pull --rebase origin main


      Git will apply your local commits on top of the updated remote main

      Keeps history linear

Delete feature branch locally

      After merging:

      git branch -d feature/login
