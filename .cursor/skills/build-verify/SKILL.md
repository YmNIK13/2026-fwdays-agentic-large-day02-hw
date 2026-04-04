---
name: build-verify
description: Run `yarn build` at the project root after code changes, fix compilation errors without `@ts-ignore`, `any`, or test-file hacks, and report the final status with fixes and full output. Use when the user asks to build, verify, or check compilation, or after edits that may affect compilation.
---

# Build & Verify

Run the project build from the repository root and treat build failures as implementation work. Fix the real source error, re-run the build, and stop after three total build attempts if the project still does not compile.

## Workflow

1. Determine the project root. Use the repository root unless the user specifies a different build target.
2. Collect the likely changed files from conversation context or `git diff` so the final report can name them.
3. Run `yarn build` at the project root.
4. If the build passes, report `PASS`, list changed files if known, and include the full build output.
5. If the build fails:
   - Read the error output carefully and identify the failing file, line, and error class before editing.
   - Open only the files needed to understand the failure.
   - Fix the underlying issue. Prefer correct types, imports, syntax fixes, or small refactors that keep the build honest.
   - Re-run `yarn build`.
   - Repeat until the build passes or three total build attempts have been used.

## Fixing Rules

- Do not silence errors with `@ts-ignore`, `// @ts-nocheck`, `any`, or similar escape hatches unless the user explicitly asks for that approach.
- Do not modify tests just to make the build pass.
- Do not add build-only hacks, dead code, or environment-specific workarounds that weaken the production codepath.
- Keep fixes scoped to the actual compilation problem, but follow through on directly related breakage surfaced by the next build attempt.

## Reporting

Always report:

- `Build status`: `PASS` or `FAIL`
- `Fixes applied`: concise list, or `none`
- `Changed files`: from `git diff` or conversation context when available
- `Full build output`: stdout and stderr from the final build attempt

If the build still fails after three attempts, stop and report the remaining errors instead of guessing further.
