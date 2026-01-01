# Exercise 2: Rebase and Push

## Step 1: Rebase Your Branch
1. Ensure you are on your branch:
   ```bash
   git checkout ${your branch name}
   ```
2. Update local main branch with remote branch contents
```bash
    git checkout main
    git pull origin main    
```
Rebase your branch onto the `main` branch:
   ```bash
   git checkout ${your branch name}
   git rebase main
   ```

---

## Step 2: Resolve Conflicts (if any)
1. If there are conflicts, Git will pause the rebase process and indicate the files with conflicts.
2. Open the conflicting files in your code editor and resolve the conflicts.
3. After resolving conflicts, stage the changes:
   ```bash
   git add <file-with-conflicts>
   ```
4. Continue the rebase:
   ```bash
   git rebase --continue
   ```

---

## Step 3: Force Push Your Changes
1. Push your rebased branch to the remote repository:
   ```bash
   git push origin ${your branch name} --force
   ```

---

## Step 4: Create a Pull Request
1. Go to the repository on GitHub (or your Git hosting platform).
2. Create a pull request from your branch to `main`.
3. Add a meaningful title and description for your pull request.
4. Submit the pull request.

---
