# Game Kit: How It Works (for Parents)

## What this is

Your kid makes their own video game. Claude, an AI helper, writes the code. Your kid makes every choice and must understand each part before it is built.

- **The tools:** Godot (a free game maker), Claude Code (the AI helper), and GitHub (a free website that stores the game and builds it).
- **The result:** a real game that friends play in a web browser, on an Android phone, or on a Windows or Linux PC. Up to 4 players can play together online.
- **The time:** the first playable game takes about 2 hours of sessions. Then the kid makes it better week by week.
- **What your kid learns:** how games work, how to plan, how to test, and how to explain their own work. Claude teaches. It does not just do the work.

Two example games made with this kit: [Stormring](https://github.com/acetousk/stormring) and [Lantern Deep](https://github.com/acetousk/lantern-deep).

## Who does what

| Who | Does | Does not |
|---|---|---|
| **Your kid** | Picks the idea, the look, the rules, and every change. Answers Claude's questions. Plays and tests each step. Says "ship it" to release. | Type commands or write code (they can, but they do not have to). |
| **Claude** | Explains each idea. Writes a plan. Asks questions to check understanding. Builds one small step at a time. Runs all the git and release work. | Choose for your kid. Give answers to its own quiz questions. Change the kit's rules. |
| **You (the parent)** | Sets up the computer and the Claude account once. Helps make accounts. Clicks through two one-time setup jobs (online keys, Android signing). Plays the game. | Need to know how to code. |

Claude follows a fixed set of written steps for each kind of job, called **skills**. For example: *new game*, *add a feature*, *fix a bug*, *make art*, *make a sound*, *ship it*, and *play online*. Your kid starts a skill by saying what they want in their own words.

## What a session looks like

Every change follows the same loop: **plan → quiz → build → play**.

1. **Your kid asks.** Example: "add an enemy that chases me."
2. **Claude teaches and plans.** It explains the idea in plain words. Then it shows a short plan: what goes in, what comes out, the steps, and how to test it.
3. **Claude asks 1–3 questions.** Example: "If the enemy is faster than you, what happens when you run?" The questions check understanding. They are not a test to pass or fail.
4. **Nothing is built until your kid answers well and says yes.**
5. **Claude builds one small step.** Your kid presses F5 and plays it.
6. **Your kid answers:** `ok` (next step), a tweak ("faster"), `bug: …`, `idea: …`, `?` (explain more), or `undo`.
7. **To release, your kid says "ship it".** Claude asks what is new before it sends the game out.

### Teach, don't tell

Claude never gives the answer to its own questions. A wrong answer gets a hint, in this order:

1. A smaller, easier question.
2. A pointer to a line in the plan, or to something in the game to try.
3. A real-life example ("like a dog that runs faster than you").

After 3 hints, Claude asks your kid to ask **it** a question about the part that is not clear. It answers that question with a hint, then asks a new question.

If your kid says "skip the quiz", Claude asks the easiest question instead. The rule is: Claude builds only what your kid understands.

## Safety

The kit has locked rules. Claude cannot change them, and your kid does not need to.

**Claude can:**

- Read and change the game's own files on this computer.
- Run the game maker to check its work.
- Send the game to your kid's GitHub, but only after your kid clicks **Allow**.

**Claude cannot:**

- Change the kit's rules, its skills, or the release setup.
- Ask for, show, or store a password, key, or code.
- Ask your kid to type commands.
- Add text chat, voice chat, or ask for personal data in the game.
- Download files from the internet, or copy another game's name, characters, art, or levels.

### Pop-ups

Sometimes Claude Code shows a pop-up that asks to allow an action.

| Pop-up | What to do |
|---|---|
| "git tag" or "git push" during *ship it* | Click **Allow**. This sends the game to GitHub. |
| Anything else your kid does not understand | Click **No**. Then ask Claude "what was that pop-up?" |

### Secrets

- Each account password lives in your kid's **Bitwarden** (a free password manager), not in a note or the chat.
- Online keys go only into Godot and GitHub settings, never into the chat with Claude.
- If a key is pasted in the chat by mistake, delete it on the GD-Sync website and make a new one.

### What is public

- The game's code and its web page are public on GitHub. Anyone with the link can play.
- The game has no chat and no accounts for players. Online rooms use a 4-digit code that only friends who get it can join.
- Do not put real names, photos, or a home town in the game or its name.

## Accounts and costs

Your kid makes each account with their own email. They keep each password in their own Bitwarden. Claude is the one exception: it uses your account, because it needs an adult (18+).

| Account | Owner | What it is for | Cost | When |
|---|---|---|---|---|
| Claude Pro | Parent | The AI helper | Paid monthly plan | Day 1 |
| Email | Kid | Signs up for the others | Free | Day 1 |
| Bitwarden | Kid | Keeps all passwords safe | Free | Day 1 |
| GitHub | Kid | Stores the game, builds it, hosts the web page | Free | Day 1 |
| GD-Sync | Kid | Online rooms for friends | Free (4 players per room, 200 MB of data a day) | When the game goes online |
| itch.io | Kid | Optional game store page | Free | Launch (optional) |

The software is free: Godot, Git, and the art and sound tools. The only cost is the Claude plan.

If an account has a problem, Claude says which account it is. A parent fixes it.

## How friends play

When your kid says "ship it", GitHub builds the game for 4 platforms. This takes about 10 minutes.

| Platform | How to play | Updates |
|---|---|---|
| **Web** | Open the game's link in Chrome, Firefox, or Edge. | Automatic. If the old version shows, press Ctrl+Shift+R. |
| **Android** | Install the free app **Obtainium**. Add the game's GitHub link once. | Obtainium tells you when a new version is ready. |
| **Windows** | Download the `.zip` file from the game's GitHub page. Unzip it and run the game. | Download the new zip. |
| **Linux** | Download the `.tar.gz` file from the game's GitHub page. Unpack it and run the game. | Download the new file. |

Mac and iPhone are not supported. Mac and iPhone players can use the web version in a browser.

### Online rooms

Up to 4 players can play together on different computers or phones.

1. One player clicks **Host**. The game shows a 4-digit room code.
2. That player sends the code to friends, for example by text message.
3. Each friend types the code and clicks **Join**.

Online play needs a one-time setup with GD-Sync keys (see the checklist below). Before that setup, online works only on the kid's own computer, inside Godot.

## Parent checklist

Do these once. Claude can guide you through each one. Your kid can say "check my setup" at any time to get a ✅/❌ list. The full steps are in [docs/1-setup.md](docs/1-setup.md).

**Day 1**

- [ ] Install Godot, Git, and Claude Code on the computer.
- [ ] Sign in to Claude Code with your Claude Pro account.
- [ ] Help your kid make an email, a Bitwarden account, and a GitHub account. Each password goes into Bitwarden.
- [ ] Make the game folder from the [starter](starter/).
- [ ] Open the folder in Claude Code. When it asks, click **Yes, I trust this folder**.
- [ ] Open the game in Godot once and press F5.

**When the game goes online**

- [ ] Your kid makes a GD-Sync account. Use a normal browser (Chrome, Firefox, or Edge). The robot check fails inside some app windows.
- [ ] On the GD-Sync website, make the game and its API keys. Save both keys in Bitwarden.
- [ ] Put the keys in Godot: **Project → Tools → GD-Sync**.
- [ ] Put the keys in GitHub: the game's **Settings → Secrets and variables → Actions**. Add `GDSYNC_PUBLIC_KEY` and `GDSYNC_PRIVATE_KEY`.
- [ ] Your kid says "ship it". Then test a room on two devices.

**For Android phones**

- [ ] Add the Android signing secrets in GitHub, as the setup guide says. This lets phones install updates over the old version.
- [ ] Install Obtainium on each phone that plays the game.

**Every week (5 minutes)**

- [ ] Play the newest version.
- [ ] Ask your kid to explain one new thing in the game. If they can, the kit works.

## When something goes wrong

First step for any problem: your kid says **"check my setup"** to Claude. Claude checks everything and changes nothing. Each ❌ line says what is wrong and who fixes it.

| Problem | Fix |
|---|---|
| Claude says the folder is not trusted, or it cannot run anything | Close Claude Code and open it again in the game folder. Click **Yes, I trust this folder**. |
| The GD-Sync robot check fails or loops | Use a normal browser (Chrome, Firefox, or Edge), not a window inside another app. |
| The web game shows the old version | Press **Ctrl+Shift+R** on the game page. |
| A friend cannot join a room | Check that the game was shipped after the online keys were added. Check that both players have the newest version. |
| The game crashes or acts wrong | Your kid says "bug:" and pastes the exact red line from Godot's Output panel, or sends a screenshot. |
| A release shows a red ❌ on GitHub | Your kid says "the build failed". Claude reads the error and explains it. |
| The Android phone will not update the game | The Android signing secrets are missing or changed. A parent checks them in GitHub. |
| Claude asks your kid to type a command | Your kid says: "use the skill, don't make me type commands". |
| A pop-up nobody understands | Click **No**. Ask Claude "what was that pop-up?" |

To undo a step: press **Esc** twice in Claude Code and pick the step to go back to.

## Word list

| Word | Meaning |
|---|---|
| **Godot** | A free program that makes games. The game is built and tested in it. |
| **Claude Code** | The program where your kid talks to Claude, the AI helper. |
| **Skill** | A fixed set of steps that Claude follows for one kind of job, for example *fix a bug*. |
| **Plan** | Claude's short list of what it will build and how to test it. |
| **Quiz** | 1–3 questions about the plan. They check understanding before anything is built. |
| **F5** | The key that starts the game in Godot. |
| **GitHub** | A free website that stores the game, builds it, and hosts the web version. |
| **Git** | The tool that saves each version of the game. Claude runs it. |
| **Ship** | Send a new version of the game out to all platforms. |
| **Version** | A numbered release, for example v0.2.1. A bigger number is newer. |
| **Build** | The finished game file for one platform. |
| **GD-Sync** | The free service that runs online rooms. |
| **Room code** | The 4-digit code that friends type to join a game. |
| **Keys** | Two secret codes that link the game to GD-Sync. They are like passwords. |
| **Secrets** | A safe place in GitHub settings for keys. Nobody can read them after they are saved. |
| **Obtainium** | A free Android app that installs and updates games from GitHub. |
| **Bitwarden** | A free password manager. |
| **Pop-up** | A box in Claude Code that asks permission for an action. |
