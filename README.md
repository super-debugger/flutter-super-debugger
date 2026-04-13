# Super Debugger

Super Debugger is an in-app developer tool for Flutter mobile apps. It is designed to help internal teams inspect app behavior directly on the device, without depending on a desktop companion app, browser dashboard, or hosted service.

The product direction is inspired by the most useful parts of tools like Chucker, Hyperion, and Flipper, but shaped for a Flutter-first in-app experience that small teams can adopt quickly and non-developer stakeholders can still understand.

## Product Direction

Super Debugger is intended to become a modular in-app inspector suite for Flutter mobile apps.

Planned product modules:

- Console Log
- Network Inspector
- Storage Inspector
- SQLite Inspector
- UI Inspector

## MVP Scope

The MVP focuses on a narrow first release that is still clearly useful.

Included in the MVP:

- home page with vertically stacked inspector menus
- working `Console Log` module
- working `Network Inspector` module
- basic HTTP response mocking inside `Network Inspector`
- search and filtering for logs and network entries
- clear labeling for mocked traffic
- support for different request and response body representations
- internal-build access control and sensitive-data protection hooks

Visible but not implemented in the MVP:

- `Storage Inspector`
- `SQLite Inspector`
- `UI Inspector`

Explicitly out of scope for the MVP:

- desktop companion app
- browser dashboard
- remote sync of logs, requests, or mock rules
- advanced mock-rule scripting
- regex or wildcard matching
- path-parameter matching
- dynamic mock templates
- stateful mocking scenarios
- storage or database editing
- full UI inspection behavior

## For Future Users

This repository is still in the early product-definition stage. The intended package direction is:

- one public Flutter library package
- one `example/` app for manual testing and demos
- simple consumer-facing API
- internal modularity so the package can grow over time

Current technical direction:

- Android and iOS only
- Flutter/Dart-first implementation
- pure Flutter where possible, native bridge only when necessary
- minimal third-party dependencies
- clean architecture with a pragmatic layer-first structure

## For Contributors

This repository uses a shared AI-assisted workflow and repo-local agent definitions so collaborators can work with the same expectations and standards.

Key docs:

- [AGENTS.md](AGENTS.md)
- [docs/ai/workflow.md](docs/ai/workflow.md)
- [docs/ai/skills/flutter-technical-baseline.md](docs/ai/skills/flutter-technical-baseline.md)

Workflow stages:

1. Brainstorming
2. Design
3. Planning
4. Implementation
5. Code Review

Artifact sources of truth:

- Repo docs: workflow, agents, and technical rules
- Notion: product and planning artifacts
- Figma: design artifacts
- GitHub Issue: execution tracking
- GitHub PR: implementation and review

## Project Links

- Notion home page: `https://www.notion.so/34008c70baa6806b9084f0483f223746`
- Figma file: `https://www.figma.com/design/GnWRZ0yqlyTg7Y36dy42rT/Super-Debugger`

## Status

Status: early definition and workflow setup

The product direction, workflow, and technical baseline are being established before the first MVP implementation work begins.
