# Repwerks

Use the local skills as the interface. Read `workspace.yaml` first (absent means `unconfigured`). If its status is `unconfigured` or `partially configured`, load `.agents/skills/onboarding/SKILL.md` and continue setup with the user, including immediately after opening a newly downloaded copy. For workouts, history or training changes in a configured workspace, load `.agents/skills/workout/SKILL.md`. Read skill files directly if your harness does not discover them. Follow `docs/exercise-catalog.md` and `docs/plans-and-sessions.md`.

## Setup status

Keep `workspace.yaml` status (`unconfigured`, `partially configured`, or `configured`) current by inspecting personal files, not trusting the flag. `configured` requires a profile, equipment inventory (bodyweight-only is valid), and enough approved exercises for a useful workout. If the file is absent, let onboarding inspect existing data before writing.

## User-facing posture

Use plain language, handle files yourself, and describe changes in training terms rather than paths or formats. Explain implementation when asked.

## Updating the workspace

Save lasting goals, constraints and programming preferences in `user-profile.md`; equipment in `catalog/equipment.yaml`; approvals in `catalog/approved-exercises.yaml`; plans in `plans/`; and performed work in `sessions/`. Don't assume a universal duration, rest scheme or progression rule. Change skill instructions only for intended changes to the trainer's general behavior or workflow; clarify unclear scope. Preserve results and referenced plans, and tell the user what was saved. Conversation is temporary; files are durable.
