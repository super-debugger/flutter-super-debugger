# Shared AI Workflow

This workflow is the shared delivery model for `flutter-super-debugger`.

## Stage Flow

1. Brainstorming
2. Design
3. Planning
4. Implementation
5. Code Review

Manual validation may be performed by the human user as needed, but it is not a formal stage gate.

## 1. Brainstorming

- Owner: `brainstorming-agent`
- Purpose: define product intent and constrain scope before design or implementation
- Output: PRD-like document
- Artifact location: Notion

Responsibilities:
- define feature goal, non-goals, and acceptance criteria
- keep alpha scope narrow and valuable
- combine product, architecture, and tech-lead thinking during grooming
- approve or reject downstream planning/design artifacts against the agreed scope

Handoff condition:
- the PRD-like document is clear enough for UI design and technical planning

## 2. Design

- Owner: `design-agent`
- Purpose: turn product intent into a UI/UX design that is clear, feasible, and easy for non-developers to use
- Output: Figma design
- Artifact location: Figma
- Gate: requires `brainstorming-agent` approval

Responsibilities:
- create simple, clean, minimalist interfaces
- optimize for non-developer comprehension
- avoid visually noisy or engineer-hostile designs
- keep complex animation purposeful and implementation-aware
- provide clear states for available, mocked, empty, loading, and error scenarios

Loop:
- `design-agent` updates the design
- `brainstorming-agent` reviews for fit with the PRD
- repeat until approved

## 3. Planning

- Owner: `planning-agent`
- Purpose: convert approved product and design artifacts into an implementation plan and execution tracker
- Outputs:
  - detailed implementation plan
  - task breakdown
- Artifact locations:
  - Notion: detailed plan
  - GitHub Issue: execution tracker and linked summary
- Gate: requires `brainstorming-agent` approval and explicit human approval

Responsibilities:
- define architecture and task boundaries
- keep dependency choices within the repo policy
- produce work small enough for implementation and review loops
- ensure the plan reflects the approved design and product scope

## 4. Implementation

- Owner: `implementation-agent`
- Purpose: implement the approved plan
- Outputs:
  - code changes
  - unit tests
  - GitHub PR
- Artifact location: GitHub PR

Responsibilities:
- follow the plan and repo technical baseline
- keep public API stable and explicit
- write unit tests for logic that matters
- preserve host app stability
- keep naming consistent with Dart and Flutter conventions

## 5. Code Review

- Owner: `review-agent`
- Purpose: review implementation quality before merge
- Outputs:
  - PR review comments
  - approval or requested changes
- Artifact location: GitHub PR review/comments

Responsibilities:
- review architecture fit, maintainability, dependency discipline, host-app safety, and unit-test effectiveness
- verify naming conventions are consistent and readable
- request changes when implementation violates workflow, architecture, or code-quality standards

Loop:
- `review-agent` leaves feedback
- `implementation-agent` addresses the issues
- `review-agent` re-reviews until the PR is acceptable

## Artifact Source Of Truth

- Repo docs: workflow, agents, and technical rules
- Notion: product and planning artifacts
- Figma: design artifacts
- GitHub Issue: execution-tracking artifact
- GitHub PR: implementation and review artifact
