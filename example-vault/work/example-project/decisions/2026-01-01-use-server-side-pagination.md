# Use server-side pagination
**Date:** 2026-01-01
**Status:** decided

## Context
Report tables can exceed 10k rows. Client-side pagination froze the UI in testing.

## Decision
Paginate on the server (page + pageSize params). Why: keeps payloads small and the UI responsive at any dataset size.

## Consequences
Front-end fetches per page; API adds pagination params. Unblocks the reporting screen build.
