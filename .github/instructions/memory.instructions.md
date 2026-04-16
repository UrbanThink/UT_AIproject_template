---
applyTo: "/memories/**"
---

# Memory Instructions

Apply these instructions whenever agents create, view, or modify persistent repository memory under `/memories/`.

## Purpose

Provide a concise, reliable, and reviewable memory system that persists useful facts across conversations.

## Structure

- A top-level index file `/memories/MEMORY.md` MUST exist and act as the thematic index (not a chronological log).
- Detailed notes belong in separate thematic files under `/memories/`, for example `/memories/debugging.md`, `/memories/patterns.md`.
- Organization is by theme (topic) — do NOT use a single chronological file to append conversational logs.

## Rules for writing memory

- Keep entries short, factual, and verifiable.
- Use clear theme-based filenames and headings inside thematic files.
- Do not store secrets, credentials, or any sensitive data in `/memories/`.
- Always cite a short provenance line when a memory is added (e.g., "source: conversation #123, 2026-04-16").

## Mandatory maintenance rules

- « Mets à jour ou supprime les souvenirs qui s'avèrent erronés ou obsolètes. N'écris pas de souvenirs en double. »
- Before adding a memory, search existing thematic files and `MEMORY.md` to avoid duplicates.
- If a memory becomes incorrect, update the thematic file and, if needed, update `MEMORY.md` to reflect the change.

## Tooling and operations

- Use the repository memory tooling (the `/memories/` files and the platform `memory` APIs) to `view`, `create`, `insert`, `str_replace`, `delete`, and `rename` memory files.
- Prefer updating an existing thematic file (`str_replace`/`insert`) rather than creating many near-duplicate files.

## Review and ownership

- When adding or changing memory entries, include a one-line rationale and the author's identifier.
- Periodically review thematic files for relevance; archive or delete outdated themes.

## Done criteria

- `MEMORY.md` index lists current themes and links to the thematic files.
- No duplicate facts across thematic files.
- No secrets or sensitive data present.

## Compaction policy (chat sessions)

- Scope: compaction applies to ephemeral chat/session transcripts and session storage — NOT to the canonical `/memories/` files which must remain the complete project memory.
- Trigger: when session/chat transcript storage or session-memory usage reaches 60% of allowed capacity, start a compaction operation focused on essential information from those sessions.
- Goal: compress and summarize chat transcripts into high-value canonical facts suitable for addition to thematic `/memories/` files while preserving provenance and auditability.
- Method:
	- Operate on session transcripts: produce theme-focused summaries and canonical facts destined for `/memories/`.
	- Preserve provenance lines and include pointers to original full transcripts (which may be archived separately).
	- Remove conversational noise from session storage and avoid duplicating facts in canonical `/memories/` files.
	- Never delete or compact authoritative entries inside `/memories/` as part of session compaction; updates to `/memories/` must be explicit, reviewed, and follow the repository's memory write rules.
	- If secrets are discovered in session transcripts, remove them immediately from session storage and notify repository owners; do not store secrets in `/memories/` or archives.
- Compaction parameters (frequency, thresholds, and preservation rules) that are specific to this repository SHOULD be defined in `.github/instructions/memory.compaction.md` and MUST state whether raw transcripts may be archived under `/memories/archives/` or must be kept externally.

