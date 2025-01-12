### Advanced Git Commands and Scenarios for HackerRank Tests

#### 1. **Rewriting History**
- **Amend the Last Commit**:
  ```bash
  git commit --amend -m "Updated commit message"
  ```
  *Use this to edit the last commit's message or include additional changes.*

- **Rebase to Clean Up Commits**:
  ```bash
  git rebase -i HEAD~3
  ```
  *Allows you to squash, edit, or reorder the last 3 commits.*

- **Reset Author of the Last Commit**:
  ```bash
  git commit --amend --author="New Author <newauthor@example.com>"
  ```

#### 2. **Cherry-Picking**
- Apply a specific commit from another branch:
  ```bash
  git cherry-pick <commit-hash>
  ```
  *Use this to copy a specific change without merging the entire branch.*

#### 3. **Reset and Revert**
- **Soft Reset (Keep Changes):**
  ```bash
  git reset --soft HEAD~1
  ```
- **Mixed Reset (Unstage Changes):**
  ```bash
  git reset HEAD~1
  ```
- **Hard Reset (Discard Changes):**
  ```bash
  git reset --hard HEAD~1
  ```
- **Revert a Commit (Undo Without History Loss):**
  ```bash
  git revert <commit-hash>
  ```

#### 4. **Branch Management**
- **Create and Switch to a New Branch**:
  ```bash
  git checkout -b <branch-name>
  ```
- **Merge Without Fast-Forward**:
  ```bash
  git merge --no-ff <branch-name>
  ```
- **Rebase Instead of Merge**:
  ```bash
  git rebase <branch-name>
  ```
- **Delete a Local Branch Forcefully**:
  ```bash
  git branch -D <branch-name>
  ```
- **Prune Deleted Remote Branches**:
  ```bash
  git fetch --prune
  ```

#### 5. **Conflict Resolution**
- **Identify Conflicts After a Merge or Rebase**:
  ```bash
  git status
  ```
  *Conflicting files will be listed. Resolve them manually.*

- **Mark as Resolved and Continue**:
  ```bash
  git add <file>
  git rebase --continue  # Or git merge --continue
  ```

#### 6. **Remotes and Collaboration**
- **Track Remote Branch Locally**:
  ```bash
  git checkout -b <branch-name> origin/<branch-name>
  ```
- **Fetch Remote Changes Without Merging**:
  ```bash
  git fetch origin
  ```
- **Compare Remote and Local Branch**:
  ```bash
  git diff origin/<branch-name>
  ```
- **Pull with Rebase**:
  ```bash
  git pull --rebase
  ```
- **Push to a Specific Remote Branch**:
  ```bash
  git push origin <branch-name>
  ```

#### 7. **Stashing**
- **Save Stash with a Message**:
  ```bash
  git stash save "WIP: fixing bug"
  ```
- **Apply Specific Stash**:
  ```bash
  git stash apply stash@{2}
  ```
- **Drop a Specific Stash**:
  ```bash
  git stash drop stash@{1}
  ```
- **Create a Branch from a Stash**:
  ```bash
  git stash branch <new-branch-name> stash@{0}
  ```

#### 8. **Tags**
- **Create and Push Tags**:
  ```bash
  git tag -a v1.0 -m "Release version 1.0"
  git push origin v1.0
  ```
- **List All Tags**:
  ```bash
  git tag
  ```
- **Checkout a Specific Tag**:
  ```bash
  git checkout tags/<tag-name>
  ```

#### 9. **Logs and Blame**
- **Search Commit History for a Keyword**:
  ```bash
  git log --grep="keyword"
  ```
- **See Who Modified a Specific Line**:
  ```bash
  git blame <file>
  ```
- **View Logs with File Changes**:
  ```bash
  git log -p
  ```
- **Short Log Summary**:
  ```bash
  git log --oneline --graph
  ```

#### 10. **Temporary Work**
- **Work with Detached HEAD**:
  ```bash
  git checkout <commit-hash>
  ```
- **Restore to Last Commit Without Reset**:
  ```bash
  git restore --source HEAD --staged --worktree <file>
  ```
- **Switch Back to the Default Branch**:
  ```bash
  git switch main
  ```

#### 11. **Optimizing and Troubleshooting**
- **Remove Untracked Files**:
  ```bash
  git clean -f
  ```
- **Find Large Files in History**:
  ```bash
  git rev-list --objects --all | grep <file-name>
  ```
- **Bisect to Find Bug-Introducing Commit**:
  ```bash
  git bisect start
  git bisect bad              # Mark the current commit as bad
  git bisect good <commit-hash>  # Mark a known good commit
  ```

#### Sample Test Questions
1. **Fix the last commit message and push to remote.**
   ```bash
   git commit --amend -m "New message"
   git push --force
   ```

2. **Rebase to squash commits into one.**
   ```bash
   git rebase -i HEAD~3
   ```

3. **Resolve a merge conflict.**
   - After `git merge`, edit files manually.
   - Run:
     ```bash
     git add <file>
     git merge --continue
     ```

4. **Cherry-pick a commit from another branch.**
   ```bash
   git cherry-pick <commit-hash>
   ```

5. **Stash changes and create a new branch from it.**
   ```bash
   git stash
   git stash branch <new-branch-name>
   ```

6. **Push tags to remote and list them.**
   ```bash
   git tag -a v1.1 -m "Release v1.1"
   git push origin --tags
   ```

