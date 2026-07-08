# Developer Handoff — Reporting screen v1
**Date:** 2026-01-02
**Source:** proposals/2026-01-01-reporting-proposal.md

## Context
Client needs a filterable report with CSV export. First delivery of the reporting epic.

## What to build
- Report table with server-side pagination.
- Filters: date range, status.
- CSV export of the current filtered view.

## Technical notes / gotchas
- Datasets can exceed 10k rows — see [[2026-01-01-use-server-side-pagination]].

## Out of scope
- PDF export, scheduled reports.

## Acceptance criteria (testable)
- [ ] Table paginates server-side.
- [ ] Filters apply to both table and export.
- [ ] CSV matches the on-screen filtered rows.

## Definition of done
- [ ] Code + tests
- [ ] Meets acceptance criteria
- [ ] Reviewed
