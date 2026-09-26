# Repwerks

A file-based training toolkit your local agent uses to plan workouts and keep a useful training history. Your agent can help build an exercise catalog, design workouts, guide a live session, record the result, and compare saved sessions. No app, runtime dependencies, or per-set script calls are required.

## Get started

Give a **file-capable** agent [the public Repwerks repository](https://github.com/hufort/repwerks) and say: **“Help me set up Repwerks in a local folder I can find again.”** Codex, Claude's local coding/file-access mode, and pi can work with local files; an ordinary chat that can only read a web page cannot save your workouts. The agent should read this README first, then follow [`AGENTS.md`](AGENTS.md) and the [onboarding skill](.agents/skills/onboarding/SKILL.md). You do not need a GitHub account.

The repository must be **publicly accessible** for anonymous link-based setup. If the link is not accessible without signing in, ask the maintainer for a public copy; the agent cannot fetch a private repository on your behalf without access.

The agent should download the public source as a ZIP (on GitHub: **Code → Download ZIP**), extract it to a folder you choose, and open that folder in its local file workspace. An anonymous Git clone is optional if you already use Git. If your agent cannot download or write local files, ask it to walk you through the ZIP download, extraction, and opening the folder in a file-capable agent. Grant file access when asked. Do not extract a new ZIP over a folder containing existing training data.

Onboarding is a short conversation: describe your equipment (bodyweight-only is fine), any movements to avoid, how familiar you are with strength training, and what you're training for. You can share your usual time budget and any preferences about format, rest or progression; leave anything you haven't decided open. You can give a simple exercise list such as “push ups, pull ups, curls, sit ups,” or optionally share a workout PDF, text, or link to find candidate exercises. The agent will suggest a small starter catalog and inventory for your approval and save your stated preferences in a local profile. A supplied workout is **not** imported as a saved plan. Setup does not start a workout.

After setup, ask the agent to plan or run a workout. It should follow the [workout skill](.agents/skills/workout/SKILL.md) (or use `/skill:workout` in pi). Review and approve a plan before starting. The agent saves a YAML plan, holds set-by-set results in conversation during the workout, then saves one JSON session file on completion or when you explicitly request a checkpoint. Unsaved work can be lost if the conversation is interrupted.

You can also tell the agent what should change going forward: “don't plan that exercise,” “keep workouts under 45 minutes,” “I have a new piece of equipment,” or “change how you approach progression.” It will save personal preferences locally, update the inventory or catalog as appropriate, or clarify whether you mean a change to your training or to the trainer's general behavior. You do not need to edit the files yourself.

## Your local data

- `user-profile.md` (created during onboarding): your ongoing goals, preferences and programming choices, in plain language.
- `workspace.yaml` (created during setup): local setup progress; absent means not yet configured.
- `.agents/skills/` and `AGENTS.md`: local instructions for interpreting and updating the workspace; not personal data or a preset training program.
- `catalog/equipment.yaml`: your equipment and setup constraints.
- `catalog/approved-exercises.yaml`: exercises you have approved for planning.
- `catalog/exercise-candidates.yaml`: optional unresolved or historical exercise names and provenance; it does **not** authorize planning.
- `plans/`: approved reusable and one-off plans, saved before use.
- `sessions/`: individual structured workout results.
- `docs/exercise-catalog.md` and `docs/plans-and-sessions.md`: file conventions.

The tracked files in `examples/` show file shapes; they are not your personalized catalog or a ready-to-use plan. Your profile, catalog files, saved plans, and sessions are ignored by Git by default; edits to the tracked instructions are not. A source ZIP has no automatic sync or update path: keep this folder and include your personal files (and any customized tracked instructions) in your normal backup. To update the source later, use a separate folder rather than extracting over your training data.

For a recap or simple history comparison, ask the agent to use saved session results. Historical candidates in the catalog are provenance, not a second planning list.
