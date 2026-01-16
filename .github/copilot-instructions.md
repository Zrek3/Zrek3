<!-- Copilot instructions for AI coding agents in this repository -->
# Copilot / AI Agent Instructions

Purpose: help an AI coding agent become productive quickly in this repository by
giving a compact discovery checklist, repo-specific conventions, and safe next
steps for any code changes.

1) Quick repository health check
- If files are missing, run these quick checks locally to discover the project type:
  - Look for a JavaScript/Node project: `package.json` at project root.
  - Look for a Python project: `pyproject.toml`, `requirements.txt`, or `setup.py`.
  - Look for a .NET project: `*.csproj` or `global.json`.
  - Look for Docker usage: `Dockerfile` or `docker-compose.yml`.
  - Look for CI: `.github/workflows/` files.

2) Architecture & entrypoints (discovery steps for the agent)
- If no README or obvious entrypoints exist, inspect these places in order:
  - [package.json](package.json) (scripts → start/test/build)
  - [pyproject.toml](pyproject.toml) or [requirements.txt](requirements.txt)
  - Source dirs: `src/`, `app/`, `lib/`, `services/`, or `cmd/`
  - Dockerfile for runtime command and exposed ports
  - `.github/workflows/` for build/test commands used by CI

3) Developer workflows and commands
- Prefer to mirror the project's own scripts. If `package.json` exists, run:
  - `npm ci` then `npm test` then `npm run build` (where available).
- For Python, create a venv and run:
  - `python -m venv .venv` then `pip install -r requirements.txt` then `pytest`.
- For .NET, run `dotnet build` and `dotnet test`.
- If CI files exist under `.github/workflows/`, follow the exact actions used there.

4) Code patterns & conventions (how to detect and follow them)
- Use the project's linters and formatters if present: search for `.eslintrc*`,
  `pyproject.toml` sections, `prettier` configs, or `.editorconfig`.
- Match existing module layout: prefer adding code inside existing top-level
  source folders (e.g., `src/` or `app/`) and follow naming patterns found there.
- Tests should live alongside source if the repo uses that pattern, or under
  `tests/` if present. Copy the style of existing tests when adding new ones.

5) PRs and edits to make (safe editing rules)
- Small, focused commits that update one feature or fix one bug at a time.
- Run local tests and linters before opening a PR. If tests or linters are not
  available, run basic type checks (mypy for Python, `tsc` for TypeScript).
- When adding or editing code, include or update minimal tests demonstrating
  the behavior change.

6) If the repository appears empty or missing guidance
- Tell the human: "Repository has no README or detectable language files. Which
  area should I focus on (frontend/backend/tooling)? Provide the main entry
  file or the build command and I will proceed."  Include the discovery steps
  you ran and their results.

7) Examples (how to reference files when making changes)
- Add a new module under `src/` if that directory exists. Link changes in PR
  description to files like [src/module.js](src/module.js) or
  [src/module.py](src/module.py).

8) Contacting the maintainer
- If unsure about high-level goals or deployments, ask the maintainer for the
  intended runtime (Node/Python/.NET), target environment, and any API
  contracts that must be preserved.

--
If this file looks incomplete, tell me which directories/files are the
primary app entrypoints and I'll update these instructions with precise,
example-driven guidance.