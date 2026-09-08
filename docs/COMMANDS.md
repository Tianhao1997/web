# Command guide

Students may use GitHub Desktop instead of the terminal. Showing the commands is still valuable because it reveals what the interface—or an AI coding agent—is doing.

## Minimal command set

| Purpose | Command | GitHub Desktop equivalent | What changes |
|---|---|---|---|
| Download a project | `git clone REPOSITORY-URL` | **File → Clone repository** | Creates a local working directory and repository |
| Inspect the current state | `git status` | **Changes** panel | Changes nothing; reports branch, staged, unstaged, and untracked files |
| Change to the stable branch | `git switch main` | **Current Branch → main** | Changes the checked-out branch and working files |
| Update the current branch | `git pull` | **Fetch origin / Pull origin** | Fetches remote commits and integrates them into the current branch |
| Create and enter a branch | `git switch -c feat/name-task` | **Current Branch → New Branch** | Creates a branch from the current commit |
| Inspect unstaged changes | `git diff` | Select a changed file | Changes nothing; shows edits not yet staged |
| Inspect staged changes | `git diff --staged` | Review checked files | Changes nothing; shows the proposed next commit |
| Select one file | `git add path/to/file` | Tick the file | Adds that file’s current changes to the staging area |
| Save a checkpoint | `git commit -m "Add mobile menu"` | Enter **Summary → Commit** | Records the staged changes in local history |
| Upload a new branch | `git push -u origin feat/name-task` | **Publish branch** | Sends the branch’s commits to GitHub and sets its upstream |
| View compact history | `git log --oneline --graph --decorate --all` | **History** panel | Changes nothing; displays commit and branch history |
| Delete a merged local branch | `git branch -d feat/name-task` | **Branch → Delete** | Deletes the local branch only if Git considers it merged |
| Discard one file’s unstaged edits | `git restore path/to/file` | **Discard Changes** | Destructively replaces uncommitted edits; use only after checking the target |

Placeholders such as `REPOSITORY-URL`, `name`, `task`, and `path/to/file` must be replaced. Do not paste them literally.

## Safe daily routine

Start from the latest shared version:

```sh
git switch main
git pull
git switch -c feat/tianhao-responsive-navigation
```

What this does:

1. `git switch main` moves to the shared stable branch.
2. `git pull` obtains and integrates the latest remote work.
3. `git switch -c ...` creates a separate workspace for this task.

After editing, inspect and record only the intended file:

```sh
git status
git diff
git add src/components/Navigation.jsx
git diff --staged
git commit -m "Add responsive navigation"
git push -u origin feat/tianhao-responsive-navigation
```

What this does:

1. `status` identifies all changed and untracked files.
2. `diff` lets the student inspect edits before selecting them.
3. `add` selects one relevant file for the checkpoint.
4. `diff --staged` previews exactly what the commit will contain.
5. `commit` records the checkpoint locally with an explanatory message.
6. `push` publishes the branch so it can become a pull request.

After a reviewer approves and merges the pull request on GitHub:

```sh
git switch main
git pull
git branch -d feat/tianhao-responsive-navigation
```

This returns to `main`, obtains the merged work, and removes the now-unneeded local feature branch.

## Actions on GitHub

After pushing the branch:

1. Open a pull request from the feature branch into `main`.
2. Explain what changed, why it changed, and how it was tested.
3. Ask another student to open **Files changed**.
4. The reviewer leaves one overall comment and at least one line-specific comment.
5. The reviewer approves or requests changes.
6. The author responds and pushes revisions to the same branch.
7. Merge only after requested changes are addressed and checks pass.

## Do not teach these first

- `git push --force`
- `git reset --hard`
- rewriting published history
- interactive rebase

These operations can remove, replace, or obscure work. Introduce them only after students understand branches, the working tree, local history, and remotes.

## If something looks wrong

Stop and inspect before acting:

```sh
git status
git diff
git diff --staged
```

Do not use a destructive “fix” copied from the internet or suggested by an LLM until someone can explain which files and commits it will affect.
