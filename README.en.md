# AIWebUITester

> An "AI-pair" testing tool where a human and an AI review a web UI/UX together, one check at a time

[日本語 README](README.md)

## Overview

Most AI testing tools delegate execution to the AI and only surface failures to humans. AIWebUITester takes the opposite approach: **the AI sits next to the screen as a review partner**, combining human eyes and AI analysis equally.

- AI generates UI/UX test plans and procedures from specs, design docs, and source code
- A human drives the target web UI following the test chart; every action is recorded (screenshots / action log / network)
- Switch to review mode to annotate issues directly; ask the AI about specs in-context via chat
- On completion, a test report with evidence (PDF / HTML dev report / HAR / GIF / PNG) is generated automatically

See the [competitive analysis & product plan](docs/planning/PRODUCT_PLAN_COMPETITIVE_ANALYSIS.md) (Japanese) and the [ver1.0.0 concept sketch](docs/planning/VER_1_0_0_CONCEPT_SKETCH.png).

## Status

**Planning / foundation stage.** No application code yet. Scope and technical decisions for ver1.0.0 are recorded in [docs/REPO_POLICY.md](docs/REPO_POLICY.md) and [ADR-0001](docs/adr/0001-browser-embedding.md).

## Planned stack

- Tauri 2 + TypeScript (desktop app)
- Playwright (browser driving & recording engine) — sidecar mode for ver1.0.0; in-app embedding validated via spike ([ADR-0001](docs/adr/0001-browser-embedding.md))
- GitHub Flow + Conventional Commits + release-please

## License

[MIT](LICENSE)
