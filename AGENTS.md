# Super Debugger Agent Rules

This repository stores the shared AI workflow, agent-role definitions, and technical standards for `flutter-super-debugger`.

## Product Context

- Product: in-app Flutter mobile developer tool library
- Target platforms: Android and iOS
- Packaging target: one public Flutter library package plus one `example/` app
- Scope direction: Chucker + Hyperion + Flipper-inspired in-app inspection experience

Primary product artifacts:
- Notion PRD/workflow artifacts: `https://www.notion.so/34008c70baa6806b9084f0483f223746`
- Figma design file: `https://www.figma.com/design/GnWRZ0yqlyTg7Y36dy42rT/Super-Debugger`

## Workflow

Follow this sequence unless the user explicitly asks to bypass a stage:

1. `brainstorming-agent`
   Output: PRD-like document
   Artifact location: Notion

2. `design-agent`
   Output: Figma design
   Artifact location: Figma
   Gate: must be approved by `brainstorming-agent`

3. `planning-agent`
   Output: implementation plan and task breakdown
   Artifact location: Notion and GitHub Issue
   Gate: must be approved by `brainstorming-agent` and the human user

4. `implementation-agent`
   Output: code changes, unit tests, GitHub PR
   Artifact location: GitHub PR

5. `review-agent`
   Output: PR review comments or approval
   Artifact location: GitHub PR review/comments
   Loop: implementation and review iterate until issues are resolved

Manual validation is informal and performed by the human user when needed. It is not a required workflow stage.

Detailed workflow: [docs/ai/workflow.md](docs/ai/workflow.md)

## Architecture Bias

- Prefer pure Dart/Flutter implementations.
- Add native Android or iOS bridge code only when Flutter-side implementation is not sufficient.
- Use a pragmatic clean architecture with a layer-first structure.
- Keep shared layers small and intentional. Do not turn `core`, `domain`, or `data` into dumping grounds.
- Design internal boundaries so future package extraction is possible, but do not split into multiple publishable packages yet.

Shared technical baseline: [docs/ai/skills/flutter-technical-baseline.md](docs/ai/skills/flutter-technical-baseline.md)

## Dependency Policy

- Default to Flutter SDK and Dart SDK capabilities first.
- Allow a small number of common packages only when they materially simplify the library.
- Approved baseline packages:
  - `provider`
  - `dio`
  - `sqflite`
- Avoid heavyweight architectural or codegen stacks by default:
  - `bloc`
  - `riverpod`
  - `getx`
  - `freezed`
  - `json_serializable`
  - `build_runner`
  - large routing packages

## Testing Policy

- Alpha testing automation scope is `unit tests` only.
- Do not require widget tests or integration tests for alpha by default.
- Manual validation is performed by the human user when appropriate.
- Unit tests should focus on:
  - event normalization
  - rule matching
  - redaction
  - filtering and search logic
  - retention and truncation behavior
  - fail-safe behavior

## Product-Specific Technical Constraints

- Public package API style: hybrid
  - simple default integration
  - optional advanced customization
- Console log alpha contract:
  - capture `debugPrint`
  - do not claim full console/log-source capture
- Runtime data retention:
  - console logs: in-memory only
  - network logs: in-memory only
  - mock rules: persisted in SQLite
- Inspector container:
  - support full-screen and bottom-sheet/panel modes
  - full-screen is the default for alpha
- Inspector UI:
  - use Material 3 internally
  - keep the inspector theme self-contained so host app theme differences do not break the tool UI

## Naming Standards

Follow standard Dart and Flutter naming unless the codebase establishes a better reason not to.

- `snake_case` for files and directories
- `PascalCase` for classes, enums, typedefs, extensions
- `camelCase` for methods, variables, parameters, and fields
- Prefer clear, descriptive names over abbreviations
- Keep public API names stable and consumer-friendly
- Useful suffixes when semantically appropriate:
  - `Adapter`
  - `Config`
  - `Controller`
  - `Entry`
  - `Module`
  - `Repository`
  - `Rule`
  - `State`

## Agent Definitions

- [docs/ai/agents/brainstorming-agent.md](docs/ai/agents/brainstorming-agent.md)
- [docs/ai/agents/design-agent.md](docs/ai/agents/design-agent.md)
- [docs/ai/agents/planning-agent.md](docs/ai/agents/planning-agent.md)
- [docs/ai/agents/implementation-agent.md](docs/ai/agents/implementation-agent.md)
- [docs/ai/agents/review-agent.md](docs/ai/agents/review-agent.md)
