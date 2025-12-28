# AGENTS

## Purpose
- Give Copilot/Codex a lightweight operating manual for this repository so generated changes stay safe, scoped, and easy to review.

## Repository Notes
- Goal: tools to harvest/analyze GitHub review comments. Prioritize clarity and traceability of any data handling.
- Stack defaults: Node.js 20, TypeScript with ESM modules, `npm` for scripts. If introducing tooling, prefer `eslint` + `prettier` + `node --test`.
- Auth: never hardcode tokens. Expect a personal access token via environment variable (e.g., `GITHUB_TOKEN`) and keep it out of git and logs.
- Data: avoid writing outside the repo. If you must cache, use a `.cache/` folder and add it to `.gitignore`.

## Working Style
- Confirm unknown requirements early; do not invent APIs. Describe the intended inputs/outputs before large implementations.
- Keep dependencies lean; flag any new runtime dependency with a short rationale.
- Tests/docs: add or update minimal coverage and README snippets when behavior changes or new commands are added.
- Changes should stay scoped and explained with concise summaries and sample commands.

## Git & Templates
- Use feature branches and descriptive commits (avoid "WIP"). Follow the `.github` templates for PRs and issues.
- If CI/tooling is missing, propose a small starter workflow but avoid breaking changes to the default branch.

## Response Style for Agents
- Default to concise, actionable answers. Include what changed, how to run it, and test results.
- Surface risks or follow-ups explicitly; prefer checklists for manual steps.
