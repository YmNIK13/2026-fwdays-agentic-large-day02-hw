---
name: codebase-explorer
description: Explore unfamiliar parts of a repository by locating relevant files, reading local entry-point docs or comments, mapping responsibilities, tracing data flow, and identifying dependencies. Use when the user asks to explore or investigate a module, feature, symbol, or file pattern, or asks how part of the codebase works.
---

# Codebase Explorer

Understand the requested area without changing files. Base every conclusion on code, comments, and repository docs that actually exist.

## Inputs

- Area of interest: module, feature, path, symbol, or file pattern

## Workflow

1. Locate the relevant area with repository search tools such as `rg --files`, `rg`, `find`, `@folder`, or `@codebase`.
2. Read the nearest `README`, package manifest, or top-level comments that describe the area.
3. Identify the entry points and list the key files with a one-line responsibility for each.
4. Trace the main flow from caller or input through processing to side effects, return values, or UI output.
5. Note important imports from other packages or layers, especially shared state, APIs, persistence, and rendering boundaries.
6. Cross-check uncertain conclusions by opening concrete call sites or implementations instead of inferring from filenames.
7. Summarize the findings and list the next files worth reading for deeper investigation.

## Output

Report:

- Purpose of the area
- Key files and responsibilities
- Main data flow or control flow
- Dependencies on other packages, modules, or services
- Related files for deeper investigation
- Open questions or unknowns if the code was inconclusive

## Safety

- Stay read-only. Do not modify files during exploration.
- Verify findings against the actual code and local docs, not assumptions.
- State uncertainty explicitly when behavior was not fully verified.
