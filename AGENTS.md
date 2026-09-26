# Repwerks

This repository uses local coding-agent skills as its interface. Read `workspace.yaml` first; if absent, assume `unconfigured`. For setup that is not yet configured, load `.agents/skills/onboarding/SKILL.md`. For workouts, training history, or requests to change how training works, load `.agents/skills/workout/SKILL.md`. Follow `docs/exercise-catalog.md` and `docs/plans-and-sessions.md`. If your harness does not discover repository-local skills, read the relevant file directly.

## Setup status

`workspace.yaml` holds local workspace metadata. Its `status` is `unconfigured`, `partially configured`, or `configured`. Keep it current after setup or later changes to readiness: inspect the personal files rather than trusting a stale flag. A configured workspace has a user profile, an equipment inventory (bodyweight-only is valid), and enough approved exercises for a useful workout. If the file is absent, treat the workspace as unconfigured and let onboarding inspect what's already there before writing anything.

## User-facing posture

Assume the user wants to use the training program, not understand its implementation. By default, treat them as non-technical: use plain language, handle files yourself, and describe what changed in user terms without detailing paths, formats, skills or project structure. Switch to an implementation-focused explanation only when the user explicitly asks for one.

## Updating the workspace

Interpret requests in ordinary language; don't ask the user to choose files. Save lasting personal goals, constraints and programming preferences in `user-profile.md`; equipment in `catalog/equipment.yaml`; exercise approvals in `catalog/approved-exercises.yaml`; prescriptions in `plans/`; and performed work in `sessions/`. Don't assume a universal workout duration, rest scheme or progression rule. Change local skill instructions only when the user intends to change the trainer's general behavior or workflow, not for ordinary personalization; clarify unclear scope. Preserve recorded results and referenced plans, and tell the user what was saved. Conversation is temporary live state; saved files are durable. There is no Python workout CLI.
