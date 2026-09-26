# Exercise catalog and equipment

These are small, agent-maintained YAML files, not an executable schema. Stable IDs connect exercises, plans and results. See `examples/` for illustrative file shapes, not personal data.

`catalog/approved-exercises.yaml` contains `exercises`, the closed list for planning. Each entry has `id`, `name`, `primary`, `secondary` (lists of muscle names), `equipment` (IDs from the equipment file), and optional `setup_notes`. A historical name is not approved merely because it appears in `catalog/exercise-candidates.yaml`. Candidate records have a historical ID, observed names, and source protocol IDs; some also have `approved_as` pointing to a shared approved exercise when historical IDs describe the same movement. An ID without `approved_as` is approved only if it appears in the approved catalog. Keep the candidate list for provenance rather than selecting exercises from it.

`catalog/equipment.yaml` describes equipment, availability and shared setup in plain language. If equipment is no longer available, retain its ID while approved entries reference it and note its unavailability; don't plan with it.
