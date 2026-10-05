# Plans and sessions

These are small, agent-maintained files, not an executable schema. Stable IDs connect plans, exercises and results. Save plan files before using them; do not rewrite a plan referenced by a session result. Use UTF-8, YAML for plans and JSON for results.

## Plans

A file under `plans/` defines a reusable or one-off plan using approved exercises. For example:

```yaml
id: example-2026-09-01
name: Example
one_off: true
expected_duration_minutes: 40
blocks:
  - id: first
    type: circuit
    rounds: 2
    rest_seconds_after_round: 60
    exercises:
      - exercise_id: example-press
        sets:
          - reps: {min: 8, max: 10}
            load_lb: 20
            load_basis: per_hand
            effort: {type: rir, min: 2, max: 3}
        note: Optional setup detail.
  - id: finish
    type: exercise
    exercises:
      - exercise_id: example-curl
        sets:
          - reps: {min: 10, max: 10}
```

In a circuit, the listed sets are performed each round; a standalone exercise runs its listed sets once. Each set can instead have `duration_seconds`. Targets and rest are optional when unspecified. State whether load is per hand, total, or added to bodyweight when load is present. Use catalog IDs for planned exercises. If an approved exercise does not exist yet, obtain approval and add it first. A plan may include free-text notes and session-specific targets; catalog entries do not prescribe loads.

New plans record `expected_duration_minutes` as a number or a `{min, max}` range. Estimate total workout time including warm-up, rest, movement and setup transitions, and note any different scope. Use comparable sessions' expected and actual durations to refine future estimates; keep referenced plans unchanged.

## Session results

Save `sessions/<session-id>.json` at the user's explicit checkpoint or session end. Reference the plan by ID and path. One `actions` entry per logged set, in performed order. For a circuit, record the round; for all actions record the set index. Refer to the plan's block and catalog exercise ID where applicable. Extra work uses `planned: false`; unlisted extra exercises include their stated name. `target` records the target actually used when it differs from the original plan; the original remains in the referenced plan. Do not manufacture missing actuals or encode an unperformed planned set as skipped. Example (illustrative IDs, not a live session):

```json
{
  "id": "example-session-2026-09-01",
  "plan": {"id": "example-2026-09-01", "path": "plans/example-2026-09-01.yaml"},
  "status": "completed",
  "expected_duration_minutes": 40,
  "actual_duration_minutes": 35,
  "actual_duration_source": "user_reported",
  "started_at": "2026-09-01T17:00:00Z",
  "ended_at": "2026-09-01T17:35:00Z",
  "actions": [
    {"block_id": "first", "exercise_id": "example-press", "round": 1, "set": 1, "planned": true,
     "actual": {"status": "completed", "reps": 9, "load_lb": 20, "load_basis": "per_hand", "effort": {"type": "rir", "value": 2}}},
    {"block_id": "finish", "exercise_id": "example-curl", "round": 1, "set": 2, "planned": false,
     "actual": {"status": "completed", "reps": 10}}
  ]
}
```

Snapshot `expected_duration_minutes` from the plan when starting a session. For older plans with an explicit estimate only in their name or notes, copy that estimate without rewriting the plan; omit it if unknown. A session-specific estimate may replace the snapshot before work begins, with a note explaining the change. Never revise the estimate to match the actual afterward. Record `actual_duration_minutes` from the user's report with `actual_duration_source: user_reported`; omit it if unknown. Chat start/end timestamps alone do not establish workout duration. Use `duration_note` for known scope differences or interruptions rather than assuming whether they occurred or whether warm-up was included. Leave unknown historical durations unfilled.

If an action's target was revised in-session, add `target` on that action with the same set-target shape used in the plan. For a new exercise not in the plan, include its `exercise_name` and optionally a session-only `block_id`; if not yet approved, retain the given name even without an approved ID. Completed actuals may include `reps`, `duration_seconds`, `load_lb`, `load_basis`, `effort` (`rir` or `rpe` plus recorded `value`, or `min` and `max` for an effort range), and `note`, as available. A skipped actual has `status: skipped` and may have a note. When shorthand omits a field, an exact value from the effective prescription may be recorded as actual; do not turn a prescribed rep range into an exact actual. An omitted prescribed effort range may be recorded as an actual range. A unilateral result applies to both sides unless the user distinguishes them; if sides differ, record distinct actions with a `side` field (for example, `left` and `right`). `in_progress` files may omit `ended_at`; completed/abandoned files include it when known. A resaved checkpoint or correction updates this same file, not a second copy. Never infer unknown numeric results merely to fill a field.
