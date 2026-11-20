# AGENTS.md

Guidance for AI agents working in this repo. Humans: see [README.md](README.md).

## What this is

A dormant 2014 LoopBack 2 experiment (package `gatewayd4`). Baseline-tier docs only. Profile: `legacy`.

## Stack

- Node.js and npm. The code targets the 2014 LoopBack 2 line: `loopback ^2.0.0`, `loopback-boot ^2.0.0`, `loopback-datasource-juggler ^2.7.0`. It needs a Node version from that era (0.10 to 0.12 at the time). Not verified on current Node.
- jshint for linting (`.jshintrc`), run as the `pretest` script.

## Layout

- `server/` app entry (`server.js`), `boot/` scripts, `config.json`, `datasources.json` (in-memory), `model-config.json`
- `common/models/` the `ripple_address` and `ripple_payments` models (JSON definition plus JS stub)
- `client/` empty placeholder
- `docs/STATUS.md` current state

## Commands

- Install: `npm install` (untested today)
- Run: `node server/server.js`
- Lint: `npm test` runs only `jshint .`. There are no real tests.
- These are known or likely not to work on today's toolchain. Say so plainly rather than guessing.

## Rules

- Add or update tests with every change.
- Never commit secrets. Keep credentials out of config files and use environment variables.
- Use Conventional Commits.
- Keep `docs/STATUS.md` current.

## What agents may and may not do

- May: improve docs, add tests, open PRs against `master`.
- May not, without Steven: archive the repo, publish it to npm, rewrite history, change the license, or change dependencies and CI in a docs-only PR.
