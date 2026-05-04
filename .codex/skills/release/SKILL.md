---
name: release
description: Use when releasing completed work in this repository by committing the current feature branch, squash-merging it into main, validating the Hugo build, and pushing origin main.
---

# Release

Use this skill for this repository's normal release flow.

## Workflow

1. Inspect context:
   - `git status --short`
   - `git branch --show-current`
   - `git diff --stat`
   - `git diff --cached --stat`
2. Do not release directly from `main` unless the user explicitly asks for a direct `main` commit.
3. Identify files relevant to the completed task. Stage those files only. Do not stage `public/`, `resources/_gen/`, `.hugo_build.lock`, unrelated work, or local scratch files.
4. Run:

   ```sh
   hugo --gc --minify --noBuildLock
   ```

5. Commit the feature branch using a concise imperative message inferred from the diff, for example:
   - `Add site logo and favicon`
   - `Add placeholder nav pages`
   - `Use Arcana Hugo theme`
6. Switch to `main`.
7. Squash-merge the feature branch:

   ```sh
   git merge --squash <feature-branch>
   ```

8. Run the Hugo build again.
9. Commit the squashed change on `main`, usually with the same message as the feature-branch commit unless the squash diff suggests a clearer one.
10. Push:

    ```sh
    git push origin main
    ```

11. Finish with:
    - feature branch commit SHA
    - `main` squash commit SHA
    - push result
    - build result
    - final branch and working-tree status

## Guardrails

- If the working tree includes unrelated changes, stop and ask before staging.
- If the feature branch has no changes to release, stop.
- If a build fails, do not commit, merge, or push until the failure is resolved.
- Never use destructive Git commands such as `git reset --hard` or `git checkout --` unless the user explicitly requests them.
