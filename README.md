# Repwerks

Repwerks helps a local AI agent plan workouts, guide sessions, and remember what you did.

## Get started

### Prefer to clone the project yourself?

```sh
git clone https://github.com/hufort/repwerks.git
```

Open the project in your preferred, file-capable harness and ask it to run through onboarding. The agent will guide you from there.

### Want the agent to handle it for you?

Copy this prompt into your agent:

```text
Help me set up Repwerks in a local folder I can find again: https://github.com/hufort/repwerks

First, check whether this session can read and write local files. If it cannot, tell me how to start a file-capable session in the app I'm using and ask me to send this prompt there. Don't try to complete setup in a web-only or chat-only session.
```

A file-capable agent can download and open the project for you. If it cannot download it, ask it to guide you through GitHub’s **Code → Download ZIP**, extracting the ZIP, and opening the folder in that session. Grant file access when asked. **Never extract a new copy over a folder with existing training data.**

## Work with Repwerks

Once setup is complete, open your Repwerks folder with your agent whenever you want to train or look back on past workouts.

### What can Repwerks do?

Ask your agent to plan a workout around your goals, equipment, and available time. It can guide you through the workout, save what you did, and later recap a session or compare it with past workouts.

### Make it your own

Repwerks is a starting point, not a fixed program. Tell your agent what fits and what doesn't; it can carry your preferences into future workouts. You can also ask it to change how the trainer works. For example:

- “Don't include that exercise in future workouts.”
- “I've got a pull-up bar now.”
- “Show me a shorter summary between sets.”
- “Add a workout rating system and use it when planning new workouts.”
- “Help me build a monthly review that spots patterns in my training and suggests what to change.”

You don't need to edit the project yourself. Talk through a change with your agent and ask it to save it for next time.

## Keep your training safe

Your profile, approved exercises, plans, and results are saved locally, not automatically synced or backed up. Include the whole folder in your normal backups, especially if you've customized how the agent works. To get a newer copy of Repwerks, download it into a separate folder rather than replacing your training data.
