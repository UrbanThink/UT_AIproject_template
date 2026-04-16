---
applyTo: "/memories/**"
---


# Memory Compaction — Project-specific defaults (sessions only)

This file contains project-level compaction parameters and operational guidance for compaction of ephemeral chat/session transcripts. It does NOT authorize compaction or deletion of canonical `/memories/` files; those files are the authoritative project memory and must be updated only via explicit, reviewed operations.

## Trigger

- Default threshold: 60% of allotted session/chat transcript storage or session-memory usage. When reached, a compaction run on session transcripts SHOULD be initiated (automated or manual).

## Objectives

- Reduce ephemeral session storage footprint while producing high-value canonical facts suitable for addition to thematic `/memories/` files.
- Keep thematic organization and auditability for the canonical memory.

## Default preservation rules

- Preserve provenance lines and any explicit `source:` metadata in generated canonical facts.
- Preserve entries tagged `preserve`, `decision`, or `canonical` when creating canonical notes.
- Keep the most recent 5 canonical decisions per theme in the canonical memory (configurable per theme).
- Summarize long session transcripts into a 2–5 line canonical note per theme; store the canonical note in the appropriate `/memories/` thematic file.

## Default compaction actions (session transcripts)

- Operate only on session/chat transcripts: summarize conversational noise and produce canonical facts for `/memories/`.
- Do NOT remove or compact existing canonical entries inside `/memories/` as part of session compaction.
- Archive raw transcripts to a designated external archive or to `/memories/archives/` only when explicitly allowed; archival must preserve a pointer from the thematic canonical note to the raw transcript location.
- If a secret or credential is found inside a session transcript, remove it immediately from session storage and notify repository owners; do not place secrets into `/memories/` or archives.

## Exclusions

- Session transcripts or entries explicitly marked `no-compact` MUST be excluded from automated session compaction.

## Operational steps (recommended)

1. Run a dry-run compaction on session transcripts that produces a summary and a proposed set of canonical facts (as a diff) for review.
2. Create a pull request that applies the new canonical facts to the relevant `/memories/` thematic files (include the dry-run report and provenance).
3. After human review, merge and tag the changes (e.g., `mem-session-compact/YYYYMMDD`).
4. Optionally archive raw transcripts in `/memories/archives/` or an external store only if policy allows; record archive paths in the associated thematic notes.

## Scheduling and frequency

- Default: trigger when threshold met. Optionally schedule periodic compaction runs (weekly/monthly) for repositories with steady chat activity.

## Owners and approvals

- Define owners in the repository README or header of this file (example: `owners: @team-leads`).
- Major session compaction runs (that would produce changes to many thematic files) SHOULD require explicit human approval.

## Configuration hints

- Tune `recent decisions kept` per-theme in this file as needed.
- Use tags inside thematic files (`preserve`, `no-compact`, `decision`) to control whether generated canonical facts are preserved during subsequent maintenance.

## Done criteria

- Session compaction reduced ephemeral session storage below threshold while canonical `/memories/` files reflect accurate, reviewed, provenance-backed facts.
- Dry-run report and PR exist for the compaction.
