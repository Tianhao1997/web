# Two-hour lesson plan

## Audience and aim

This session is designed for master’s design students with little or no command-line experience. Its aim is collaborative control of a web-app project, not memorization of Git syntax.

## Preparation

Before class, the teacher should:

- create one repository per student group;
- add a small web app and a clear `README.md`;
- invite students with write access but not administrator access;
- protect `main` when the account or organization settings allow it;
- install GitHub Desktop on classroom computers;
- verify that the app can start and that its tests or build can run;
- confirm permission to redistribute the figure in `assets/git-four-areas.png`.

## Schedule

| Time | Activity | Evidence of learning |
|---:|---|---|
| 0–15 min | Mental model: Git, GitHub, four storage areas, and the limitations of Figure 1 | Students explain add, commit, push, and pull in their own words |
| 15–35 min | Create and share: repository, README, clone, `.gitignore`, first commit, invite collaborators | Every group has a shared repository and local clone |
| 35–55 min | Individual branch: pull `main`, create a branch, make one visible interface change, inspect diff, commit, push | Each student publishes one focused branch |
| 55–85 min | Peer review: pull-request description, Files changed, overall comment, line comment, requested revision, approval | Every pull request contains substantive peer feedback |
| 85–105 min | Conflict exercise: two students change the same button label on separate branches | Students explain why Git cannot choose the intended wording automatically |
| 105–120 min | AI-assisted workflow: inspect or review with an LLM, then verify its evidence | Students identify one useful agent action and one required human check |

## Conflict exercise

1. Give two students branches created from the same `main` commit.
2. Ask each to change the same button text to a different phrase.
3. Merge the first pull request.
4. Update or merge `main` into the second branch so the conflict becomes visible.
5. Compare both intended meanings before editing conflict markers.
6. Construct a deliberate combined result, then test and review it.

The learning objective is negotiation and traceability—not choosing “ours” or “theirs” mechanically.

## Peer-review requirements

Each student must:

- leave one overall comment about the change;
- leave one line-specific comment or suggestion;
- request one small, justified improvement when appropriate;
- respond constructively to received feedback;
- approve only after concerns are addressed and the app is checked.

## Assessment rubric

| Criterion | Developing | Competent | Strong |
|---|---|---|---|
| Branch discipline | Edits `main` or mixes tasks | Uses one task branch | Uses a focused branch with a clear name and current base |
| Commit quality | Large or unclear checkpoint | Focused commit with descriptive message | Focused history that explains intent |
| Diff literacy | Accepts changes without inspection | Identifies intended changed files | Detects unrelated, generated, or sensitive content |
| Review quality | Gives vague approval | Gives specific, actionable feedback | Connects evidence to user impact and verifies revisions |
| AI judgment | Treats output as automatically correct | Checks diff and reported tests | Challenges assumptions and adds targeted manual checks |

## Closing questions

- What is saved when you save a file, commit, and push?
- Why is a branch safer than editing `main`?
- What information makes a pull request easy to review?
- Which LLM actions should require confirmation?
- What would you test manually even after an automated build passes?
