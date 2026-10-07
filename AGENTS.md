# Repwerks

Use the local skills as the interface. Read `workspace.yaml` first (absent means `unconfigured`). If its status is `unconfigured` or `partially configured`, load `.agents/skills/repwerks-onboard/SKILL.md` and continue setup with the user, including immediately after opening a newly downloaded copy. In a configured workspace, load the skill for the task: `repwerks-plan` to design or revise plans, `repwerks-run` to perform or log a session, `repwerks-history` for recaps and history, `repwerks-personalize` for lasting goals, constraints or equipment, and `repwerks-approve-exercise` for catalog additions. For a new workout, plan and save it before running it; load both skills when a request spans both phases. Read skill files directly if your harness does not discover them. Follow `docs/exercise-catalog.md`, `docs/training-programs.md`, and `docs/plans-and-sessions.md` as relevant.

## Setup status

Keep `workspace.yaml` status (`unconfigured`, `partially configured`, or `configured`) current by inspecting personal files, not trusting the flag. `configured` requires a profile, equipment inventory (bodyweight-only is valid), and enough approved exercises for a useful workout. If the file is absent, let onboarding inspect existing data before writing. If the flag says `configured` but required personal data is missing, correct it and use onboarding before training.

## User-facing posture

Use plain language, handle files yourself, and describe changes in training terms rather than paths or formats. Explain implementation when asked. Default to tables for line-item or naturally tabular information (one exercise per row for workouts); use another format when it has a clear benefit.

## Updating the workspace

Save lasting goals, constraints and programming preferences in `user-profile.md`; equipment in `catalog/equipment.yaml`; approvals in `catalog/approved-exercises.yaml`; goal-directed training programs in `training-programs/`; workout plans in `plans/`; and performed work in `sessions/`. Don't assume a universal duration, rest scheme or progression rule. Change skill instructions only for intended changes to the trainer's general behavior or workflow; clarify unclear scope. Preserve results and referenced plans, and tell the user what was saved. Conversation is temporary; files are durable.
