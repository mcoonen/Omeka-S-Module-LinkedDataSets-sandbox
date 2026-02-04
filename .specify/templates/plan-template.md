# Implementation Plan: [FEATURE]

**Branch**: `[###-feature-name]` | **Date**: [DATE] | **Spec**: [link]
**Input**: Feature specification from `/specs/[###-feature-name]/spec.md`

**Note**: This template is filled in by the `/speckit.plan` command. See `.specify/templates/commands/plan.md` for the execution workflow.

## Summary

[Extract from feature spec: primary requirement + technical approach from research]

## Technical Context

<!--
  ACTION REQUIRED: Replace the content in this section with the technical details
  for the project. The structure here is presented in advisory capacity to guide
  the iteration process.
-->

**Language/Version**: [e.g., PHP 7.4+, Laminas, or NEEDS CLARIFICATION]  
**Primary Dependencies**: [List justified composer packages or `MINIMIZE` if avoided]  
**Storage**: [if applicable, e.g., Omeka S resource storage, files or N/A]  
**Testing**: [e.g., phpunit, phpstan, or NEEDS CLARIFICATION]  
**Target Platform**: [e.g., Omeka S v4.x on Linux server or NEEDS CLARIFICATION]
**Project Type**: Omeka S module
**Performance Goals**: [domain-specific, e.g., stream datadumps to avoid OOM or NEEDS CLARIFICATION]
**Constraints**: [e.g., preserve Omeka S compatibility, avoid heavy deps or NEEDS CLARIFICATION]
**Scale/Scope**: [domain-specific, e.g., expected dataset sizes, number of item sets or NEEDS CLARIFICATION]

## Constitution Check

This project defines explicit constitution gates that MUST be validated before
Phase 0 completion. For this feature, confirm the following (document results
below):

- Dependency justification: any new composer dependency MUST include a short
  justification and maintenance plan (see `composer.json`).
- Tests: feature MUST include unit tests for core logic and integration tests
  for Omeka S interactions where applicable.
- CI: proposed changes MUST be runnable in CI using `phpstan`, `phpunit`, and
  `composer audit`.
- Compatibility: confirm the feature preserves Omeka S compatibility and does
  not require MAJOR version changes unless documented in the plan.

[Gates determined based on constitution file]

## Project Structure

### Documentation (this feature)

```text
specs/[###-feature]/
├── plan.md              # This file (/speckit.plan command output)
├── research.md          # Phase 0 output (/speckit.plan command)
├── data-model.md        # Phase 1 output (/speckit.plan command)
├── quickstart.md        # Phase 1 output (/speckit.plan command)
├── contracts/           # Phase 1 output (/speckit.plan command)
└── tasks.md             # Phase 2 output (/speckit.tasks command - NOT created by /speckit.plan)
```

### Source Code (repository root)
<!--
  ACTION REQUIRED: Replace the placeholder tree below with the concrete layout
  for this feature. Delete unused options and expand the chosen structure with
  real paths (e.g., apps/admin, packages/something). The delivered plan must
  not include Option labels.
-->

```text
# [REMOVE IF UNUSED] Option 1: Single project (DEFAULT)
src/
├── models/
├── services/
├── cli/
└── lib/

tests/
├── contract/
├── integration/
└── unit/

# [REMOVE IF UNUSED] Option 2: Web application (when "frontend" + "backend" detected)
backend/
├── src/
│   ├── models/
│   ├── services/
│   └── api/
└── tests/

frontend/
├── src/
│   ├── components/
│   ├── pages/
│   └── services/
└── tests/

# [REMOVE IF UNUSED] Option 3: Mobile + API (when "iOS/Android" detected)
api/
└── [same as backend above]
```

**Structure Decision**: [Document the selected structure and reference the real
directories captured above]

## Complexity Tracking

> **Fill ONLY if Constitution Check has violations that must be justified**

| Violation | Why Needed | Simpler Alternative Rejected Because |
|-----------|------------|-------------------------------------|
| [e.g., 4th project] | [current need] | [why 3 projects insufficient] |
| [e.g., Repository pattern] | [specific problem] | [why direct DB access insufficient] |
