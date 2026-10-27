# LabTestSystem

## Agent skills

### Issue tracker

GitHub Issues on `trungkien87/LabTestSystem`, driven through the REST API (`gh api`), not `gh issue`. See `docs/agents/issue-tracker.md`.

### Triage labels

Default vocabulary: `needs-triage`, `needs-info`, `ready-for-agent`, `ready-for-human`, `wontfix`. See `docs/agents/triage-labels.md`.

### Domain docs

Single-context: one `GLOSSARY.md` and `docs/adr/` at the repo root. See `docs/agents/domain.md`.

## Project conventions

### Document file naming

Versioned documents handed over or submitted for approval (design system, specs, mockup packs, checklists filled for this project, reports) are named `<Name>_<Lang>_<YYYYMMDD>_Rev<xx>.<ext>`, e.g. `DESIGN_EN_20261027_Rev01.md`. `Rev01` is the first issue; every re-issue with changed content bumps the Rev and the date. The document also states its version inside (e.g. `Version: 20261027 Rev.01`).

Files that the repo or tools refer to by a fixed name keep that name: `AGENTS.md`, `CLAUDE.md`, `GLOSSARY.md`, `README.md`, ADRs (`docs/adr/NNNN-slug.md`), `docs/agents/*`, and the converted source snapshot in `docs/source/` (whose originals keep their own file names).

### UI design

All UI (mockups, Web, and the service app on measurement-equipment PCs) follows `docs/source/design-system/DESIGN_EN_20261027_Rev01.md` and checklist group E in `docs/source/quality-checklist/e-ui-ux-design.md`.

### Languages

The UI must support at least Vietnamese and English on both the Web and the service app on measurement-equipment PCs (checklist F1, mandatory).
