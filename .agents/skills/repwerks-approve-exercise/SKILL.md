---
name: repwerks-approve-exercise
description: Review and approve exercises for future Repwerks planning, including historical candidates and exercises performed outside a plan. Use when adding or changing entries in the approved exercise catalog; not for recording performed work.
---

# Approve exercises

Work from the repository root. Follow `AGENTS.md` for setup status and onboarding. Read `docs/exercise-catalog.md`, `catalog/equipment.yaml`, and `catalog/approved-exercises.yaml`. Read `catalog/exercise-candidates.yaml` when reconciling historical names or aliases; candidates are provenance, not permission to plan an exercise. Check for an existing approved ID or candidate `approved_as` alias before adding an entry. Review inferred muscle tags, equipment and constraints with the user; get explicit approval before adding or changing an entry. Add a stable ID, name, primary and secondary muscle tags, equipment IDs and optional free-text setup notes to `catalog/approved-exercises.yaml`. Preserve candidate provenance and historical references. Do not silently add an unlisted exercise merely because it appeared in a workout; repwerks-run may record actual work without catalog approval. Tell the user what was approved.
