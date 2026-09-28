# Repwerks

Repwerks helps a local AI agent plan workouts, guide sessions, and remember what you did. Your training stays in a folder you control.

## Get started

Copy this prompt into your agent:

```text
Help me set up Repwerks in a local folder I can find again: https://github.com/hufort/repwerks

First, check whether this session can read and write local files. If it cannot, tell me how to start a file-capable session in the app I'm using and ask me to send this prompt there. Don't try to complete setup in a web-only chat.
```

A file-capable agent can download and open the project for you. If it cannot download it, ask it to guide you through GitHub’s **Code → Download ZIP**, extracting the ZIP, and opening the folder in that session. Grant file access when asked. **Never extract a new copy over a folder with existing training data.**

## Keep your training safe

Your profile, approved exercises, plans, and results are saved locally, not automatically synced or backed up. Include the whole folder in your normal backups, especially if you've customized how the agent works. To get a newer copy of Repwerks, download it into a separate folder rather than replacing your training data.
