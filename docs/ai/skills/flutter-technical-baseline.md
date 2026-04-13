# Flutter Technical Baseline

This document defines the shared Flutter engineering skill baseline for AI agents working in this repository.

## Core Principles

- Prefer pure Dart and Flutter implementations.
- Use native Android or iOS bridges only when Flutter-side implementation is not enough.
- Favor pragmatic clean architecture over framework-heavy patterns.
- Keep the public API small, explicit, and package-consumer friendly.
- Minimize dependency count and setup friction for consumers.

## Package Shape

- one public Flutter library package
- one `example/` app for manual testing and demos
- internal code organized with a pragmatic layer-first structure
- future extraction into more packages should remain possible, but is not required now

## Architecture Rules

- Keep `core`, `domain`, `data`, and presentation layers focused and small.
- Do not create generic abstractions until they are justified by real duplication or multiple consumers.
- Keep package internals independent from transport or storage specifics where possible.
- `Dio` and `sqflite` must sit behind internal contracts or repositories.
- Host app stability takes priority over inspector completeness.

## Approved Packages

- `provider`
- `dio`
- `sqflite`

These packages are allowed because they are common, lightweight enough for the problem, and materially useful.

## Avoid By Default

- `bloc`
- `riverpod`
- `getx`
- `freezed`
- `json_serializable`
- `build_runner`
- large routing frameworks

Use any of these only with an explicit reason tied to product value or unavoidable complexity.

## State Management

- Prefer simple controllers and Flutter-native state mechanisms first.
- `provider` is acceptable when it simplifies dependency wiring or scoped state access.
- Do not turn `provider` into a sprawling app-wide architecture if smaller composition works.

## Public API Style

- Use a hybrid API design:
  - simple default setup for common usage
  - advanced configuration for modules, adapters, and shell behavior when needed
- Keep setup predictable and low-friction for package consumers.

## Alpha Runtime Contracts

- Console log support: capture `debugPrint`
- Do not claim full console/log-source capture in alpha
- Console log storage: in-memory only
- Network capture storage: in-memory only
- Mock rules: persisted in SQLite

## UI Rules

- Use Material 3 internally.
- Keep the inspector theme self-contained.
- Do not require consumer apps to adopt Material 3 globally.
- Default inspector mode is full-screen.
- Optional presentation mode may also support a bottom sheet or panel experience.

## Testing Rules

- Alpha automation scope is unit tests only.
- Focus unit tests on logic, policies, normalization, matching, filtering, and fail-safe behavior.
- Do not assume widget or integration test coverage for alpha.

## Naming Standards

- `snake_case` for files and directories
- `PascalCase` for classes, enums, typedefs, and extensions
- `camelCase` for methods, fields, parameters, and local variables
- Use descriptive, stable, consumer-friendly names
- Apply clear role suffixes when useful:
  - `Adapter`
  - `Config`
  - `Controller`
  - `Entry`
  - `Module`
  - `Repository`
  - `Rule`
  - `State`
