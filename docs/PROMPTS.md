# LLM prompt library

These prompts work as starting points for coding agents such as Codex or Claude Code. Replace text inside `<angle brackets>` and `[square brackets]` with project-specific information.

A prompt can guide an agent, but it cannot guarantee safe behavior. Tool permissions, repository rules, diff review, testing, and human judgment remain necessary.

## 1. Establish safe operating boundaries

```text
You are working in a shared student GitHub repository.

Before changing anything:
1. Report the current branch and Git status.
2. Do not work directly on main.
3. Do not discard, reset, overwrite, or reformat unrelated work.
4. Create or use a branch named feat/<student-name>-<task>.
5. Modify only files relevant to the requested task.
6. Run the existing build or tests after editing.
7. Show a summary of changed files and important differences.
8. Ask before committing, pushing, opening a pull request, or merging.
9. Never force-push and never commit passwords, API keys, or .env files.
```

**What this lets the LLM do:** establish the branch, file, verification, and approval boundaries for the session before implementation begins.

**Human checkpoint:** verify the reported branch and status. Prompt text is not a security boundary; the agent’s actual permissions determine which actions are possible.

## 2. Understand an unfamiliar repository

```text
Inspect this repository without modifying it. Explain in simple language:

- what the app does;
- the important folders and files;
- how to start and test it;
- what framework it uses;
- whether Git currently has uncommitted changes;
- which files I would probably edit to change [feature].

Do not make any changes yet. Cite the project files that support each conclusion.
```

**What this lets the LLM do:** search and read the codebase, infer its structure, locate likely edit points, and report repository state without intentionally editing files.

**Human checkpoint:** compare the explanation with the README, package configuration, and visible Git status. Treat unsupported claims as hypotheses.

## 3. Implement a focused design change

```text
Create a new branch named feat/<name>-responsive-navigation.

Implement a responsive mobile navigation menu based on this description:
[describe the design, target screen sizes, states, and interaction].

Preserve existing behavior and other students’ work. Do not rewrite unrelated
files. Check keyboard accessibility and mobile layout. Run the existing build
and tests, then show the diff summary and test results. Do not commit or push
until I approve.
```

**What this lets the LLM do:** create an isolated line of work, modify relevant files, run available verification, and summarize the result.

**Human checkpoint:** use the app, test keyboard interaction and responsive states, then inspect the complete diff. A successful build does not prove that the design is correct.

## 4. Review before committing

```text
Review my uncommitted changes. Check for:

- accidental changes outside the task;
- broken functionality;
- responsive-layout problems;
- accessibility problems;
- exposed credentials or personal information;
- generated files or node_modules that should not be committed.

Do not edit anything. Separate findings into Must fix, Suggestions, and
Questions. Refer to exact files and lines where possible.
```

**What this lets the LLM do:** analyze the current diff as a reviewer and prioritize likely defects or repository hygiene problems without intentionally changing the working tree.

**Human checkpoint:** reproduce important findings. An LLM can miss defects or report false positives.

## 5. Prepare a pull-request description

```text
Based on the current branch and its diff from main, draft:

1. A concise pull-request title.
2. What changed.
3. Why the change was needed.
4. How it was tested.
5. Any limitations or review questions.
6. A short screenshot checklist.

Do not commit, push, open, or merge the pull request.
```

**What this lets the LLM do:** synthesize the branch diff into a structured review brief that helps teammates understand intent and verification.

**Human checkpoint:** confirm that every claim—especially test results—matches actions that actually occurred.

## 6. Review another student’s branch

```text
Review this branch against main without modifying files.

Focus on functional bugs, accessibility, responsive behavior, unclear code,
unintended deletion of existing work, and whether the implementation matches
the described design.

Separate findings into:
- Must fix before merging
- Suggestions
- Questions for the author

Refer to exact files and lines where possible. Explain the observable impact of
each Must fix item. Do not merge the pull request.
```

**What this lets the LLM do:** compare the proposed branch with `main`, inspect implementation risks, and draft evidence-oriented review comments.

**Human checkpoint:** a peer should still inspect the diff, run the app, and decide whether the change meets the design brief.

## 7. Explain a merge conflict safely

```text
Explain this merge conflict in plain language. Show what the current branch
intended and what main intended. Propose a combined version that preserves both
pieces of work.

Do not resolve the conflict, commit, or push until I approve the proposed
result. Identify any behavior that must be tested after resolution.
```

**What this lets the LLM do:** interpret conflict markers and surrounding code, reconstruct both intentions, and propose a resolution for discussion.

**Human checkpoint:** ask both authors when design intentions conflict. “Ours” and “theirs” are Git perspectives, not measures of which version is correct.

## A useful prompt pattern

Strong prompts usually specify:

1. **Context** — repository, branch, task, and audience.
2. **Outcome** — the observable result, not only “make it better.”
3. **Scope** — files or behavior that may and may not change.
4. **Constraints** — accessibility, responsive states, style system, privacy, and compatibility.
5. **Verification** — build, tests, manual scenarios, screenshots, and diff review.
6. **Approval boundary** — which actions require the student’s confirmation.

The LLM can inspect, propose, edit, execute available tools, and report evidence. It cannot decide the project’s values, guarantee correctness, or replace accountable peer review.
