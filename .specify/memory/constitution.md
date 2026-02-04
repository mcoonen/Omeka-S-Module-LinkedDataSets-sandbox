<!--
Sync Impact Report
- Version change: TEMPLATE -> 1.0.0
- Modified principles (added):
  - Module-First, Framework-Aligned
  - Minimize Dependencies
  - Compatibility & Stability
  - Test-First & Quality Gates
  - Observability & Simplicity
- Added sections:
  - Constraints & Requirements
  - Development Workflow
- Removed sections: none
- Templates requiring updates:
  - .specify/templates/plan-template.md ✅ updated
  - .specify/templates/spec-template.md ✅ updated
  - .specify/templates/tasks-template.md ✅ updated
  - .specify/templates/checklist-template.md ⚠ pending (not modified)
  - .specify/templates/commands/*.md ⚠ pending (directory missing)
- Follow-up TODOs:
  - TODO(RATIFICATION_DATE): original adoption date unknown; maintainers should provide the ratification date.
-->

# Linked Data Sets Constitution

## Core Principles

### I. Module-First, Framework-Aligned
All code in this repository MUST conform to Omeka S and Laminas conventions, PSR-4
autoloading, and PSR-12 coding style. Module integration MUST be implemented via
supported Omeka S extension points and Laminas components rather than framework
workarounds. Rationale: following framework conventions ensures maintainability,
compatibility with Omeka S upgrades, and predictable behavior for integrators.

### II. Minimize Dependencies
External dependencies are a cost: each new package increases maintenance,
security surface, and upgrade complexity. New composer dependencies MUST be
proposed with a clear justification (functional gap that cannot be met by built-in
PHP or Laminas features) and an explicit maintenance plan. Prefer builtin
Laminas components, native PHP extensions, or small, well-audited libraries.
Rationale: the module targets Omeka S environments where adding heavy dependency
sets causes friction; minimizing deps improves portability and security.

### III. Compatibility & Stability
The module MUST support the baseline declared in `composer.json`: Omeka S v4.x
and PHP >=7.4 (or the versions declared in `composer.json`). Public APIs and
storage formats MUST remain backward compatible across PATCH and MINOR releases.
MAJOR version bumps are reserved for breaking changes to persisted data, public
APIs, or principle redefinitions. Rationale: stable compatibility reduces upgrade
cost for deployments and preserves user data integrity.

### IV. Test-First & Quality Gates
All new features and bug fixes MUST include automated tests: unit tests for core
logic and integration tests for Omeka S interactions (e.g., Item sets, resources,
serialization). Tests must be runnable locally and in CI. Changes to behavior that
affect stability, data, or public contracts require test coverage demonstrating
both the old and new behavior where applicable. Static analysis (phpstan) and
coding-style checks (php-cs-fixer / phpcs) MUST pass in CI. Rationale: tests and
static checks catch regressions early and codify expectations for maintainers.

### V. Observability & Simplicity
Error conditions MUST produce clear, structured logs and actionable error
messages. Complex features MUST be decomposed into smaller, well-documented
units that are independently testable. Avoid premature optimization; prefer
clarity over cleverness. Rationale: readable, observable code is easier to
support and debug in production Omeka S deployments.

## Constraints & Requirements

- Supported platform: Omeka S v4.x (see `composer.json`) and PHP >=7.4.
- License: follow the repository LICENSE.md.
- Security: any new dependency MUST pass `composer audit` in CI and include a
  mitigation plan if vulnerabilities are discovered.
- Performance: data-dump and export routines SHOULD stream output and avoid
  unbounded memory usage when processing large Item Sets.

## Development Workflow

- All proposed changes MUST be submitted as a pull request with a clear
  description, migration plan for breaking changes, and accompanying tests.
- Code review: PRs require at least one approving review from a project
  maintainer or an experienced contributor. Significant API or principle changes
  SHOULD include discussion in an issue before implementation.
- CI gates: pipeline MUST run `phpstan`, `phpunit`, `phpcs`/`php-cs-fixer`, and
  `composer audit`. PRs that fail CI MUST not be merged.

## Governance

Amendments to this constitution or to core principles MUST follow this process:
1. Open an issue describing the proposed amendment and its rationale.
2. Submit a pull request that updates this document and any impacted templates
   or docs. The PR MUST include a migration plan for consumers of the module.
3. The PR MUST pass CI and receive at least one approving review from a
   project maintainer. For MAJOR changes (redefining or removing principles,
   breaking persisted formats, or changing public APIs), approval from a
   majority of core maintainers is REQUIRED; if maintainers are not clearly
   defined, require two independent contributor approvals.

Versioning policy:
- MAJOR: incompatible changes to public APIs, storage formats, or principle
  redefinitions.
- MINOR: addition of new principles, new non-breaking features, or material
  guidance expansions.
- PATCH: clarifications, typo fixes, or non-semantic wording changes.

Compliance review:
- Every release MUST include a short checklist stating which principles the
  release impacts and how compliance was validated (tests, migration steps,
  dependency reviews).

For runtime development guidance, see `doc/Development.md` and `README.md`.

**Version**: 1.0.0 | **Ratified**: TODO(RATIFICATION_DATE): original adoption
date unknown - maintainers should provide | **Last Amended**: 2026-02-04
