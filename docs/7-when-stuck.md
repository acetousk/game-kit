# 6. When you are stuck

## First: "check my setup"

Say **"check my setup"** to Claude. Claude checks Godot, git, GitHub, and GD-Sync. It changes nothing. You get a ✅/❌ list. Each ❌ says who fixes it: you or a parent.

## Common problems

| Problem | What to do |
|---|---|
| F5 does nothing, or Godot shows a red error | Copy the **exact** red line from Output. Say `bug:` and paste it. |
| The game crashes | Say `bug:` and paste the red line, or send a screenshot (**Win + Shift + S**). |
| Claude says the folder is not trusted, or it cannot run anything | Close Claude Code. Open it again in your game folder. Click **Yes, I trust this folder**. |
| Claude asks you to type a command | Say: `use the skill, don't make me type commands`. |
| A pop-up you do not understand | Click **No**. Ask: `what was that pop-up?` |
| You do not understand Claude's answer | Type `?` or `why?`. Claude explains, and does nothing more until you get it. |
| You are stuck on a quiz question | Try the hint. After 3 hints, ask Claude a question about the part that is not clear. |
| A change made the game worse | Say `undo`, or press **Esc** twice in Claude Code and pick the step to go back to. |
| The web version shows the old game | Press **Ctrl + Shift + R** on the game page. |
| The build on GitHub shows a red ❌ | Say `the build failed`. Claude reads the error and explains it. |
| A friend cannot join your room | Did you ship after you added the GD-Sync keys? Do both of you have the newest version? |
| The GD-Sync robot check fails | Use a normal browser: Chrome, Firefox, or Edge. |
| Your phone will not update the game | A parent checks the Android signing secrets in GitHub. |
| Stuck 3 times on the same problem | Stop. Ask a parent to sit with you for one build loop. |

## Words

| Word | Means |
|---|---|
| Card | One task in your plan: what goes in, what comes out, and how you check it |
| Scene, node, script, signal | See [2-godot-basics.md](2-godot-basics.md) |
| Ship | Send a new version to all 4 platforms |
| Tag | The version name on a save point, for example `v0.2.2`. A new tag starts the builds. |
| Secrets | A safe place in GitHub for keys. Nobody can read them after you save them. |
