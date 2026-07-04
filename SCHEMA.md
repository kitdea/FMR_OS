# SCHEMA — How This Vault Is Maintained

> Layer 3 of the wiki pattern (raw sources → wiki → schema). This file documents structure and conventions so any session — mine or yours — can maintain this vault consistently instead of re-deriving the rules each time. Based on the ingest/query/lint pattern from https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f.

---

## The Three Layers, Applied Here

1. **Raw sources** — journals, reading notes (`00 Notes/`), and anything I write by hand. Immutable record of what actually happened/was said. Not to be rewritten, only appended to or referenced.
2. **The wiki** — `CLAUDE.md`, `GOALS.md`, Chess Moves docs, project `CLAUDE.md` files, Weekly/Monthly/Quarterly Reviews. These are living, LLM-maintained summaries that get updated as facts change.
3. **This file** — the schema itself.

---

## Folder Map & Page Types

| Path | Type | Update trigger |
|---|---|---|
| `CLAUDE.md` | Root config + Weekly Update section | Weekly (weekly-update skill), or ad hoc when a tracked open question resolves |
| `GOALS.md` | Master plan — North Star, 1-year/3-year goals, Active Plans table, metrics | When a goal, plan, or decision changes; reviewed weekly |
| `02 Chess Moves (Long-Term Planning)/` | Dated strategic-thinking sessions, one file per session, `(C)` prefixed | New file per Chess Moves session; existing files get TODOs filled in as decisions land (not rewritten wholesale) |
| `03 Projects/<name>/CLAUDE.md` | Per-project config, mirrors root structure at project scope | When project scope/status changes |
| `03 Projects/(PROJECT TEMPLATE)/` | Template only — never edit directly, copy for new projects | N/A |
| `04 Reviews/` | Weekly/Monthly/Quarterly/Yearly retrospectives | On the review's own cadence |
| `00 Notes/` | Raw reading/reference notes (Bible, Books, Courses, Videos) | Ad hoc, append-only in spirit |
| `01 Journals/` | Daily/personal journal | Daily, raw source — not synthesized into elsewhere automatically |
| `05 Skills/` | Claude skill definitions (`brain-setup`, `new-project`, `weekly-update`) | When a workflow changes |

---

## Conventions (from CLAUDE.md — do not override without permission)

- **AI-generated or AI-edited files get a `(C)` prefix.** Applies to new files; the Weekly Update section inside `CLAUDE.md` is edited in place without a prefix since it's a subsection, not a standalone file.
- **Never edit an existing note without asking first** — except filling in explicit `<!-- TODO -->` placeholders that were left as open slots for exactly this (e.g. Chess Moves docs), which counts as completing the note rather than rewriting it.
- **Cross-reference with `[[Note Name]]`** (Obsidian wikilink style), matching how the memory system links `[[name]]`.
- **Never change the user's stated rules** (CLAUDE.md's "Rules & Boundaries" section) without explicit permission.

---

## Operations

### Ingest
When new information surfaces in conversation (a decision, a number, a fact that changes a plan):
1. Identify which wiki page(s) it belongs on — usually `GOALS.md` (if it's a goal/metric/plan change), the relevant Chess Moves doc (if it resolves a TODO), a project `CLAUDE.md` (if project-scoped), or the Weekly Update section.
2. Update only the specific fact — don't rewrite surrounding context that's still accurate.
3. If the fact contradicts something already written, flag it explicitly rather than silently overwriting (ask first, per the no-silent-edit rule).

### Query
When asked something the vault might already answer:
1. Check `GOALS.md` and `CLAUDE.md` first (the compiled summaries) before searching raw sources.
2. Fall back to raw sources (`01 Journals/`, `00 Notes/`) only if the wiki doesn't have it — and if found, consider whether it should be ingested into the wiki so the next query doesn't need to re-search.

### Lint
Periodically (e.g. during a weekly-update run or when asked), check for:
- **Stale claims** — numbers/dates in `GOALS.md` or `CLAUDE.md` that are older than the review cadence implies they should be.
- **Contradictions** — e.g. a Chess Moves doc's TODO says undecided but `GOALS.md`'s Active Plans table already states a decision (or vice versa).
- **Orphaned pages** — project folders with no corresponding line in GOALS.md's "Current Projects" section, or Active Plans entries pointing at files that don't exist.
- **Broken `[[links]]`** — wikilinks referencing notes that don't exist.

---

## Known Current Gaps (as of 2026-07-03)

- Website Maintenance Package scope/pricing still undefined, and its target client is now unclear since Shumaker Roofing's existing $800/mo already bundles maintenance.
- 3-Year Picture (GOALS.md) not yet defined.
- Agentic SEO system build plan not yet created (queued Chess Moves session).
