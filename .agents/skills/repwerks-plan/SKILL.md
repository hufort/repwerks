---
name: repwerks-plan
description: Design, revise, and save workouts or reusable training plans in a configured Repwerks workspace. Use when the user asks what to do next, requests a plan, or wants a plan/template changed; hand off to repwerks-run to perform it.
---

# Plan a workout

Work from the repository root. Follow `AGENTS.md` for setup status and onboarding. Read `user-profile.md`, `catalog/equipment.yaml`, `catalog/approved-exercises.yaml`, `docs/exercise-catalog.md`, and `docs/plans-and-sessions.md`. Read only relevant history and plans. The approved catalog is the closed list for planning; `catalog/exercise-candidates.yaml` is provenance, not approval. Check approved IDs, including candidate aliases mapped by `approved_as`. If an unlisted exercise would help, propose it but ask before including it in a plan; use the repwerks-approve-exercise skill to add it first.

- Use the current profile, available equipment, approved exercises and relevant history to design the workout. Exclude movements the user no longer wants to do without removing historical catalog entries. If essential programming choices are open, discuss them rather than applying universal defaults. A block is a repeated grouping such as a circuit or superset.
- Preview the prescription (order, blocks, rounds, sets, targets, rest and notes as applicable). After approval, save a YAML plan under `plans/` before beginning. Even a one-off plan is saved; mark it `one_off: true`.
- Save `expected_duration_minutes` in each new plan, including warm-up, prescribed rest, movement and setup transitions. Calibrate estimates against reported actual durations of comparable sessions, accounting for differences in work, rest and interruptions rather than applying a universal correction from one session.
- If a saved plan conflicts with current preferences, propose a revised version rather than silently changing a reusable plan for one session. Use a unique plan ID. Never edit a plan referenced by a session result; create a new plan/version instead.
- For a request to start working out, hand the approved saved plan to repwerks-run. That skill owns live guidance, results and session IDs; planning does not log performed work.
