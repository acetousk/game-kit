# Game Kit

Make your own video game with Claude, from the first idea to a game your friends play on the web, on Android, and on Windows or Linux.

The kit is made for a 16-year-old with no coding background. **You** make every choice. Claude writes the code, and it builds only what you understand: it shows a plan, asks you 1–3 questions, and gives hints, never the answers.

- **Engine:** [Godot 4.7.2](https://godotengine.org) (free)
- **AI helper:** Claude Code
- **Builds and hosting:** GitHub (free): web, Android, Windows, Linux
- **Online:** GD-Sync rooms with a 4-digit code, up to 4 players (free)

## See it work (90 seconds)

![A kid, played by a second AI, and Claude turn an island game into a lunchroom food fight. The video plays on its own and repeats.](docs/media/stormring-kid-and-claude.webp)

With sound: [download the video with narration (MP4, 7 MB)](docs/media/stormring-kid-and-claude.mp4)

A real test run of the kit. The kid asks for a change to the example game Stormring: "no guns, a food fight in a giant school lunchroom". You see:
1. The kid says the idea. Claude splits it into small steps.
2. Claude asks questions about the plan. A wrong answer gets a hint, not the answer.
3. Nothing changes until the kid says yes. Then Claude builds one step, and the kid plays it.
4. Claude reads its own test run and finds a bug (the bots splat you in 2 seconds).
5. The finished Lunchroom Food Fight. The maintainer finished it later with the same kit.

In this test, a second AI (Claude Haiku) plays the kid. The game's own Claude does all the work, the same way as for a real kid.

## Try it yourself (about 20 minutes)

Play the example game Stormring, then ask Claude to change it. This is a quick test. The full setup for a kid is in [docs/1-setup.md](docs/1-setup.md).

### What you need
- A Windows, Mac, or Linux computer.
- A paid Claude plan (Pro or higher). The free plan does not include Claude Code. For a kid, use the parent's account (18+).

### 1. Get Claude Code
Choose **one**:

| Option | How |
|---|---|
| **Desktop app** (easiest) | Download it from [claude.com/download](https://claude.com/download). Install it and sign in. Open the **Code** tab. |
| **Terminal** | Run the command for your system (below). Then open a new terminal and type `claude`. Sign in in the browser. |

```bash
# Mac, Linux, WSL
curl -fsSL https://claude.ai/install.sh | bash
```
```powershell
# Windows PowerShell
irm https://claude.ai/install.ps1 | iex
```

On Windows, also install [Git for Windows](https://git-scm.com/downloads/win).

### 2. Start in an empty folder
1. Make a new, empty folder, for example `games`.
2. Open Claude Code in that folder. In the desktop app, choose the folder. In a terminal, `cd` into it and type `claude`.

### 3. Copy and paste this prompt
Claude installs what is missing and opens the game. It asks before each install. Say yes or no each time.

```text
Set up the Game Kit example game for me on this computer. I am new to this, so explain each step in one short sentence.

1. Check my operating system. Ask me before you install anything.
2. Install Godot 4.7.2 (the standard version, not .NET) from the official site godotengine.org or the official GitHub releases. Use this exact version.
3. Make a "godot" command that works in this terminal, so you can run Godot yourself. Check it with "godot --version".
4. Install git if it is missing. Clone https://github.com/acetousk/stormring into this folder.
5. In the stormring folder, run "godot --headless --import" once. Fix nothing in the game. Only tell me if there are errors.
6. Open the project in the Godot editor for me.
7. Tell me how to play: press F5 to start, and the keys to move and throw.
8. Then read the AGENTS.md and CLAUDE.md files in stormring, and follow their rules from now on. Ask me what I want to change in the game.
```

### 4. Change the game
Play one round. Then tell Claude one thing to change, in plain words. For example: *"Make the food bounce off walls"* or *"Add a pie that is slow but big"*.

Claude shows a plan, asks you 1–3 questions, and waits for your "yes". This is the same loop as in the video.

To start your own game instead, see [docs/1-setup.md](docs/1-setup.md). It uses the empty project in [starter/](starter).

## Start here

| Who | Read |
|---|---|
| **Parent** | [PARENTS.md](PARENTS.md): what your kid does and learns, safety, cost, and your 10 minutes a week. No tech needed. |
| **Setup adult + kid** | [docs/1-setup.md](docs/1-setup.md): the one-time setup (about 4 hours). For an adult who is comfortable with computers. |
| **Kid** | [docs/2-godot-basics.md](docs/2-godot-basics.md): what Godot is, how a game is built, and how to use the editor |
| **Kid** | [docs/3-make-the-game.md](docs/3-make-the-game.md): how you work with Claude, then your first game |
| **Kid** | [docs/4-make-it-better.md](docs/4-make-it-better.md): tune the feel, new ideas, art and sound |
| **Kid** | [docs/5-ship-and-play.md](docs/5-ship-and-play.md): release a version, the 4 platforms, online rooms |
| **Kid** | [docs/6-friends-and-feedback.md](docs/6-friends-and-feedback.md): bug reports and ideas from friends, and the docs for your players |
| **Kid** | [docs/7-when-stuck.md](docs/7-when-stuck.md): common problems and what to do |

## Keep your chats out of AI training

Claude Pro is on an adult's account. If its training setting is on, Anthropic may use its chats and Claude Code sessions to train new AI models. Make sure that it is off before the first session:

1. Sign in at claude.ai with the account Claude Code uses.
2. Open [claude.ai/settings/data-privacy-controls](https://claude.ai/settings/data-privacy-controls) (your name → **Settings** → **Privacy**).
3. Turn off the switch that lets Anthropic use your chats to improve its AI models.

With the switch off:
- New chats are not used for training.
- Anthropic keeps them for 30 days, not 5 years.

The switch covers Claude Code too. The kit does the rest: [starter/.claude/settings.json](starter/.claude/settings.json) turns off `/feedback`, `/bug`, `/share`, and the session survey. Those would send the chat and code to Anthropic, kept for 5 years.

More: [Claude Code data usage](https://code.claude.com/docs/en/data-usage) and [how to change the setting](https://privacy.claude.com/en/articles/12109829-how-do-i-change-my-model-improvement-privacy-settings).

## What is in this repo

```
game-kit/
├── README.md       This page
├── PARENTS.md      For parents (no tech needed)
├── docs/           The guides, in order
├── starter/        The files for a new game repo: Claude's rules and skills, the build pipeline, an empty Godot project
└── examples/       Two games made with this kit
```

- **[starter/](starter/)**: copy everything in it into your new game repo ([docs/1-setup.md](docs/1-setup.md), part C). Then open the folder in Claude Code and say `What do we do first?`. The list of what to say to Claude is in [starter/SKILLS.md](starter/SKILLS.md).
- **[examples/](examples/)**: [Stormring](https://github.com/acetousk/stormring) (3D, online food fight) and [Lantern Deep](https://github.com/acetousk/lantern-deep) (2D, turn-based cave crawler).

## The rules Claude follows

1. You say what you want. Claude says if it is possible, and how it works.
2. Claude shows a plan and asks you 1–3 questions. Wrong? A hint, never the answer. After 3 hints, you ask Claude a question.
3. Nothing changes until you get them right and say yes.
4. Claude does one small step. You press F5 and play.
5. Nothing ships until you can explain what is new.

Claude cannot change these rules, ask for passwords or keys, make you type commands, add chat, or copy another game.
