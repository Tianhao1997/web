# Contributing to a class project

Use this workflow for every change: (new changes)

1. Create or claim an Issue with a clear outcome.
2. Update local `main`.
3. Create one branch for that issue: `feat/<name>-<short-task>` or `fix/<name>-<short-task>`.
4. Make only relevant changes and test them.
5. Inspect both unstaged and staged diffs.
6. Commit with a message that describes the outcome.
7. Push the branch and open a pull request into `main`.
8. Ask a teammate to review it.
9. Address comments on the same branch.
10. Merge only after approval and successful checks, then pull the updated `main`.

## Pull-request checklist

- [ ] The pull request links to its Issue or task.
- [ ] The title states the outcome.
- [ ] The description explains what changed and why.
- [ ] The branch contains no unrelated changes.
- [ ] The app builds or runs as expected.
- [ ] Relevant automated tests pass.
- [ ] Keyboard and responsive behavior were checked where relevant.
- [ ] Screenshots cover changed visual states.
- [ ] No secrets, `.env` files, private data, generated dependency folders, or personal files are included.
- [ ] Another student reviewed the complete diff.

## Review comments

A useful review comment identifies:

1. the exact location;
2. the observable problem or question;
3. why it matters to a user or collaborator;
4. a suggested direction when one is known.

Discuss competing design intentions with the author. Do not use a merge-conflict tool or LLM suggestion as an automatic decision.
