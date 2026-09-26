---
name: workout
description: Design, run, checkpoint, review, and personalize training in this repository. Use for workouts, exercise approval, training history, or requests to change preferences, equipment, or trainer behavior.
---

# Workout workflow

Work from the repository root. Read `workspace.yaml` if present; absence means `unconfigured`. If it is not `configured`, or if the profile, equipment or usable approved catalog is missing, follow `.agents/skills/onboarding/SKILL.md` with the user before planning and correct a stale flag; do not assume the tracked examples are personalized. Read `docs/exercise-catalog.md` and `docs/plans-and-sessions.md` for file conventions and `user-profile.md` if present for this user's current goals, preferences and programming choices. Read `catalog/equipment.yaml` for available equipment and `catalog/approved-exercises.yaml` for exercises authorized for *planning*. `catalog/exercise-candidates.yaml` preserves historical names and provenance; it is not a planning catalog. Check `catalog/approved-exercises.yaml` for approval, including aliases mapped by `approved_as` in the candidate list. Read only the plan and results needed for the request. No Python CLI is needed.

## Plan and start

- Discuss workout design and suggestions freely. Plan with approved catalog entries; you may propose an unlisted exercise, but ask the user before adding it to the catalog or including it in a plan. Do not treat a candidate as approved.
- Use the current profile, inventory, approved exercises and relevant history when designing a workout. Exclude movements the user no longer wants to do without removing their approved entries from historical references. If essential programming choices are still open, discuss them with the user rather than applying universal defaults. A block is a repeated grouping such as a circuit or superset; preferences are not barriers to recording work actually done.
- Preview the prescription (order, blocks, rounds, sets, targets, rest and notes as applicable). After approval, save a YAML plan to `plans/` before beginning. A one-off plan is a saved plan too; label it `one_off: true`. If a saved plan conflicts with current preferences, propose a revised version; do not silently change a reusable plan in place for a session.
- Use a unique plan ID and a unique session ID; write the session result to `sessions/<session-id>.json` at finish or explicit checkpoint. The saved plan is the baseline, referenced by path and ID from the result. If a plan needs edits after a result references it, create a new plan/version instead of changing the referenced original.

## In session

- On arriving at each circuit, preview a minimal table: exercise, counts (rounds × sets), and targets (reps or duration, load, effort). Omit setup instructions and rest from this preview. During work, show only a compact next-action table row with block/round/set, exercise, target/load and any rest; do not echo each logged result. Use prose only for a clarification or change.
- Keep the live work in context. Listen to natural responses and record clear results without confirmation; an otherwise clear result without a stated status is completed. Parse `12/3` as 12 reps at 3 RIR when RIR is the applicable effort measure, and `12/4 30lb` as 12 reps at 4 RIR with a 30 lb load override. For omitted values, use exact values from the effective prescription (including agreed session-specific changes). Do not invent exact reps from a range: ask for the rep count when omitted. An omitted effort target range may be recorded as that range rather than a single value. Ask briefly when an interpretation is genuinely ambiguous.
- `same` copies reps, effort and load from the most recent completed set of the same exercise and side, then applies any explicit override (for example, `same 27.5lb`). Do not copy status or notes. If there is no comparable completed set, ask for clarification. By default, a single result for a unilateral movement applies to both sides unless the user specifies otherwise.
- Track every action in order, including skipped sets and user-performed extra sets or exercises. An explicit report of extra work is enough to record it, even for an unlisted exercise; mark it unplanned, and separately ask whether the exercise should enter the approved catalog for future plans. Do not block historical logging on catalog approval.
- You may suggest changing future actions; ask before applying a suggested change to the active prescription. A user-requested change needs no second confirmation if clear. Keep the original plan intact and represent revised targets as session-specific deviations in the result. Template changes require a separate explicit request and a new saved version.
- If a reported actual is corrected, update the in-context entry (or the saved session file if already checkpointed) rather than adding a duplicate action.
- At user request, checkpoint the full current session as `in_progress` in a single JSON file. On resumption, read that file and its referenced plan, reconstruct the completed actions and continue from there. If context is lost before a checkpoint, explain that unsaved results cannot be recovered.
- At finish, save the full result as `completed`, including work performed even if some planned sets were skipped or never reached. Use `abandoned` only when the user explicitly abandons the workout. Write/update one file per session, not one file per set. Clearly distinguish unknown/unperformed planned sets from explicitly skipped ones.

## Improve the workflow

- If a concrete ambiguity or friction point suggests a simple way to prevent it next time, briefly flag the observed issue and possible refinement, and ask whether the user wants the workflow changed. Do not propose speculative optimizations or modify the system without approval.
- During an active workout, keep such observations in context (or in ignored scratch if needed) and bring them up only after the session result is saved, so they do not interrupt logging.

## Review

- For a recap or history comparison, read saved result files and referenced plans. Give source-linked counts, reps, loads and effort where recorded; distinguish missing values and unplanned work. Simple arithmetic is fine; no reporting engine or weekly dashboard is required.
- For a new catalog entry, get the user's approval and then add a stable ID, name, muscle tags, equipment IDs and free-text setup notes to `catalog/approved-exercises.yaml`. Review inferred tags/constraints with the user rather than treating archive metadata as certain. Preserve the candidate list as provenance.
