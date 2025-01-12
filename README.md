
Advanced Git Commands and Scenarios for HackerRank Tests

1. Rewriting History

- Amend the Last Commit:
git commit --amend -m "Updated commit message"
This command allows you to change the message of your last commit or add more changes to it.

- Rebase to Clean Up Commits:
git rebase -i HEAD~3
This allows you to review and change your last 3 commits: you can combine them into one (squash), edit them, or change their order.

- Reset Author of the Last Commit:
git commit --amend --author="New Author <newauthor@example.com>"
This command allows you to change the author information of the last commit.

2. Cherry-Picking

- Apply a Specific Commit from Another Branch:
git cherry-pick <commit-hash>
Use this to copy just one specific change from another branch without merging the entire branch.

3. Reset and Revert

- Soft Reset (Keep Changes):
git reset --soft HEAD~1
This moves the HEAD pointer back to the previous commit but keeps your changes as uncommitted.

- Mixed Reset (Unstage Changes):
git reset HEAD~1
This moves the HEAD pointer and removes changes from the staging area, but they remain in your working directory.

- Hard Reset (Discard Changes):
git reset --hard HEAD~1
This moves the HEAD pointer and deletes your changes from both the staging area and working directory.

- Revert a Commit (Undo Without History Loss):
git revert <commit-hash>
This creates a new commit that undoes the changes of a previous commit. It’s useful for undoing changes without losing history.

4. Branch Management

- Create and Switch to a New Branch:
git checkout -b <branch-name>
This creates a new branch and automatically switches to it.

- Merge Without Fast-Forward:
git merge --no-ff <branch-name>
This forces a merge to create a new commit, even if a fast-forward merge is possible.

- Rebase Instead of Merge:
git rebase <branch-name>
This applies changes from one branch onto another in a clean, linear way, instead of merging.

- Delete a Local Branch Forcefully:
git branch -D <branch-name>
This deletes a local branch even if it has unmerged changes.

- Prune Deleted Remote Branches:
git fetch --prune
This cleans up references to branches that no longer exist on the remote.

5. Conflict Resolution

- Identify Conflicts After a Merge or Rebase:
git status
After merging or rebasing, Git shows which files have conflicts that need resolving.

- Mark as Resolved and Continue:
git add <file>
git rebase --continue  # Or git merge --continue
After resolving conflicts manually, stage the resolved files and continue the rebase or merge process.

6. Remotes and Collaboration

- Track Remote Branch Locally:
git checkout -b <branch-name> origin/<branch-name>
This creates a local branch and sets it to track a remote branch.

- Fetch Remote Changes Without Merging:
git fetch origin
This updates your local copies of remote branches without merging any changes.

- Compare Remote and Local Branch:
git diff origin/<branch-name>
This shows the differences between your local branch and the remote branch.

- Pull with Rebase:
git pull --rebase
This pulls changes from the remote and applies your local commits on top, instead of merging them.

- Push to a Specific Remote Branch:
git push origin <branch-name>
This pushes your local branch to a specific remote branch.

7. Stashing

- Save Stash with a Message:
git stash save "WIP: fixing bug"
This saves your current changes (work in progress) and gives it a label for easy identification.

- Apply Specific Stash:
git stash apply stash@{2}
This applies a specific stash from your stash list.

- Drop a Specific Stash:
git stash drop stash@{1}
This deletes a specific stash from the list.

- Create a Branch from a Stash:
git stash branch <new-branch-name> stash@{0}
This creates a new branch from the stashed changes.

8. Tags

- Create and Push Tags:
git tag -a v1.0 -m "Release version 1.0"
git push origin v1.0
Create a tag (a version marker) and push it to the remote.

- List All Tags:
git tag
This lists all tags in your repository.

- Checkout a Specific Tag:
git checkout tags/<tag-name>
This checks out a specific tag, letting you view the state of your project at that tag.

9. Logs and Blame

- Search Commit History for a Keyword:
git log --grep="keyword"
Search commit messages for a specific keyword.

- See Who Modified a Specific Line:
git blame <file>
Shows who made changes to each line of a file.

- View Logs with File Changes:
git log -p
Shows commit logs with the actual changes made to the files.

- Short Log Summary:
git log --oneline --graph
Shows a simple and graphical representation of the commit history.

10. Temporary Work

- Work with Detached HEAD:
git checkout <commit-hash>
This allows you to explore a specific commit without switching branches (detached HEAD).

- Restore to Last Commit Without Reset:
git restore --source HEAD --staged --worktree <file>
Restores a file to its state from the last commit.

- Switch Back to the Default Branch:
git switch main
Switches back to the main branch.

11. Optimizing and Troubleshooting

- Remove Untracked Files:
git clean -f
Deletes untracked files that are not part of your version history.

- Find Large Files in History:
git rev-list --objects --all | grep <file-name>
Helps you search for large files that have been committed in the past.

- Bisect to Find Bug-Introducing Commit:
git bisect start
git bisect bad              # Mark the current commit as bad
git bisect good <commit-hash>  # Mark a known good commit
Helps you find which commit introduced a bug by checking out commits between good and bad commits.

Sample Test Questions

1. Fix the Last Commit Message and Push to Remote:
git commit --amend -m "New message"
git push --force

2. Rebase to Squash Commits into One:
git rebase -i HEAD~3

3. Resolve a Merge Conflict:
After git merge, edit files manually.
Run:
git add <file>
git merge --continue

4. Cherry-Pick a Commit from Another Branch:
git cherry-pick <commit-hash>

5. Stash Changes and Create a New Branch from It:
git stash
git stash branch <new-branch-name>

6. Push Tags to Remote and List Them:
git tag -a v1.1 -m "Release v1.1"
git push origin --tags
