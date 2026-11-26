# 3. Make the game

Setup is done ([1-setup.md](1-setup.md)), and you know the Godot basics ([2-godot-basics.md](2-godot-basics.md)). Godot is on the left, Claude Code is on the right.

## 1. How you work with Claude

### Ask first: can it be done, and how does it work?

**The main rule: Claude builds nothing you do not understand.**

When you ask for something, Claude first works out how to do it. Then it gives one of 3 answers:

| Answer | What Claude tells you | Example |
|---|---|---|
| **Yes** | How it works, in 2–4 plain lines | "Double jump: the game counts your jumps. In the air you get 1 more. Landing resets the count." |
| **Yes, but big** | About how many steps, and a smaller version | "A level editor is about 40 steps. A smaller version: levels from a text file, about 6 steps." |
| **Not possible here** | Why, how the real thing works, and the closest option | See below |

Then Claude shows a plan and asks you **1–3 questions** about it. If you get one wrong, Claude gives you a hint, not the answer, and you try again. Nothing gets built until you get them right and say yes.

#### "Not possible here": common examples

| You ask | Why not | How it really works | Closest option |
|---|---|---|---|
| "100 players online" | The GD-Sync free plan has at most 4 per lobby | One host sends the game state to each player through a relay. More players = more data every second. | 4 players, co-op |
| "Graphics like a big console game" | The web and phone builds use the simple Compatibility renderer | Big games use teams of artists and strong GPUs for light and shadow | One strong art style with a small palette |
| "Text or voice chat" | A safety rule in this project | Chat needs moderation: people and filters that check messages | Quick-message buttons ("Nice!", "Help!") |
| "Download this model from a website" | Claude does not download assets | Each asset has a license. You must check that it is free to use. | You download a CC0 asset and list it in `CREDITS.md` |
| "Make it like <a famous game>" | We do not copy other people's games | Games use the same ideas (genres), but their names, art, and levels belong to their makers | Your own game in the same genre |

If you do not understand an answer, type **`?`** or **`why?`**. Claude explains again, and does nothing more until you get it.

### Every task is a card

Claude does most of the work. You **choose**, **check**, and **approve**.
Each task is a **card** in `PLAN.md` with 3 parts. Claude makes `PLAN.md` in your first session.

| Part | Question | Example (G2) |
|---|---|---|
| **Input** | What does Claude read? | `DESIGN.md` |
| **Output** | What does Claude make or change? | `player.tscn`, `player.gd`, art |
| **Done when** | How do you check it? | F5 → you do the main action |

**Why cards work:**
- Claude reads only the Input. It does not wander through the project.
- Claude changes only the Output. Nothing else breaks.
- "Done when" tells you, not Claude, when the task is finished.

### The build loop

Two loops: a **card loop** (5–30 min) and, inside it, a **step loop** (about 1 min).

```
 CARD LOOP
 1. ASK       Type: "Do task G2"
 2. CAN IT?   Claude says: Yes / Yes, but big / Not possible here,
              and how it works.
 3. PLAN      Claude shows Input, Output, and numbered steps. Read them.
    QUIZ      Claude asks 1–3 questions about the plan. Wrong? A hint, then try again.
 4. APPROVE   Choose "Yes, and auto-accept edits". Then no pop-up stops each step.
   │
   ▼
 ┌─ STEP LOOP (about 1 minute) ─────────────────────────────┐
 │ a. Claude does one step: "How: …" + "▶ Play: … look for …"│
 │ b. You press F5 (F5 again restarts it). Play 20 seconds. │
 │ c. You answer in one line:                               │
 │      ok              → next step                         │
 │      faster          → Claude changes only that          │
 │      bug: <what you see, or the exact red error>         │
 │      idea: <new idea> → saved for later, not done now    │
 │      ?  or  why?     → Claude explains, then waits        │
 │      undo            → press Esc twice in Claude Code    │
 └──────────────── repeat until the card is done ───────────┘
   │
   ▼
 5. SAVE      Claude asks "Ship it now?" Say no: Claude saves the
              card on this computer. Say yes: Claude ships it.
 6. NEXT      The next card, or stop
```

**Your answers are scoped:**

| You say | Claude does |
|---|---|
| `ok` | The next step |
| A tweak (`faster`, `easier`) | Changes only that, then ▶ again |
| `bug: …` | Fixes it if it is inside the card's Output. If not, adds it to Bugs. |
| `idea: …` | Writes it in "Not in v1.0". Does not do it now. |
| `?` or `why?` | Explains the step. Does no more steps until you get it. |
| `undo` | Press Esc twice in Claude Code and choose the step to go back to |

#### Faster than 1 minute: tune it yourself
1. Press **F5** and leave the game running.
2. In Godot, open the **Scene** panel and click **Remote**.
3. Click **Tune** (all the feel numbers live there). Change a number, like `player_speed`, in the **Inspector**.
4. The game changes at once. When you like it, tell Claude: "Set player_speed to 320."

#### Multiplayer test (when the task touches multiplayer)
1. In Godot, click **Debug > Customize Run Instances**.
2. Turn on **Enable Multiple Instances**. Set it to **2**.
3. Press **F5**. Two game windows open.
4. Make a room in window 1. Join with the code in window 2.
5. Test the feature in both windows.
6. Close window 2 in the middle of the game. Window 1 must keep working.

#### Release (once a week, or at a milestone)
1. In Claude Code, type: "ship it."
2. Claude asks you what is new and how one change works. Wrong? A hint, then try again. Nothing ships that you can't explain.
3. Check the version Claude suggests. Say **go**.
4. Click **Allow** on each pop-up (one for `git tag`, one for each `git push`). Claude does every git step. You never type a command.
5. Wait about 10 minutes. Then check:
   - GitHub > **Actions**: a green check
   - GitHub > **Releases**: the new version
   - The web version on GitHub Pages. Press **Ctrl + Shift + R** once, or the browser can show the old version for 10 minutes.
   - The phone: Obtainium shows an update

#### Session rules
- One card at a time. One step at a time.
- Play after **every** step. Do not let Claude do 3 steps at once.
- Claude slow? Type `/fast` in Claude Code.
- Never accept a change you do not understand. Type `?` instead.
- Always paste the **exact** error. Do not write it from memory.
- End every session with a save point (Claude asks "Ship it now?" after each card). Ship at least once a week, so your work is on GitHub.
- When you get stuck 3 times on the same problem, stop and ask the parent.

**What to say:** open `SKILLS.md` in your game folder. It lists each keyword ("ship it", `bug: …`, `idea: …`, "make a level", "check my setup", "make a skill") and what Claude does.

The repo makes Claude follow this flow. You do not need to read these files:
- `AGENTS.md`: the rules, for any game and any request.
- The skills in `.claude/skills/`: `game-plan` sorts each request to `new-game`, `feature`, `bug`, `ship`, `doctor`, `create-2d`, `create-3d`, `create-audio`, `create-background`, `create-environment`, `explain`, `online`, `issues`, or `create-skill`.
- `.claude/settings.json`: Claude Code starts in plan mode, so it cannot edit before you approve.

---

## 2. The first playable game (day 1)

Your first game starts with the **First playable**: 7 cards that work for any game, 2D or 3D. The scope is set by Claude's work time, not the clock: **about 75 minutes of Opus 5.5 work, about 65 steps.** You play after every step, so you get about 65 feedback loops. Your own play time comes on top.

The result is a complete game: start screen → play → win or lose → play again, with sound, online with 2–4 players, on Windows, phone, and web.

| Card | Claude budget | Result (any genre) |
|---|---|---|
| G1 Design + scope | 5 min | `DESIGN.md` core + a step count that fits |
| G2 Core loop | 15 min | World, player, main action, camera |
| G3 Goal | 10 min | You can win |
| G4 Pressure | 10 min | You can lose |
| G5 Online | 15 min | Host or join a room with a code. The host runs the game. |
| G6 Flow + sound + touch | 12 min | Start, end, play again, touch controls, sound |
| G7 Ship | 8 min | `v0.1.0` on all platforms |

**How the scope stays inside the budget:**
1. In G1, Claude asks about your game, then writes the steps for G2–G7.
2. Claude counts them. Over about 65? You choose. Or say "you pick", and Claude chooses what moves to "Not in v1.0".
3. During the cards, a step that takes Claude more than 1–2 minutes gets split.
4. Over the budget? Skip the "tune" and "effect" steps. Do them in week 1.

| Idea | Fits the first playable | Goes to later |
|---|---|---|
| 3D racer | 1 car, 1 track, 3 laps, a timer | More cars, AI drivers, more tracks |
| 2D platformer | 1 level, coins, 1 enemy type | More levels, bosses |
| Top-down splat arena (water balloons, paint) | 1 arena, waves of 1 enemy type | More throwables, upgrades |
| 3D puzzle | 3 small puzzles in 1 room | A story, more rooms |

Start with: **"Do task G1."** Claude asks you one question at a time and fills in `DESIGN.md`.

| ✓ | Type this | You check |
|---|---|---|
| ☐ | "Do task G1" → answer one question at a time | `DESIGN.md` says what you want, and it fits the budget |
| ☐ | "Do task G2" | You do the main action, and it feels OK |
| ☐ | "Do task G3" | You can win |
| ☐ | "Do task G4" | You can lose |
| ☐ | "Do task G5" | Install GD-Sync from the AssetLib when Claude asks. Then do the multiplayer test above. |
| ☐ | "Do task G6" | Start → play → end → play again, with sound |
| ☐ | "Do task G7" | Plays on Windows. After the build: on the phone and the web. |

For each card:
1. Claude says if it is possible, and how it works.
2. Read Claude's plan (Input, Output, steps, test). Answer its 1–3 questions.
3. Choose **"Yes, and auto-accept edits"**.
4. After each step: read the "How" line, press F5, play, and answer in one line: `ok`, a tweak, `bug: …`, `idea: …`, `?`, or `undo`.
5. After the last step, Claude asks "Ship it now?". No → Claude saves it on this computer. Yes → Claude ships it.

**Done when:** You have a working game on 3 platforms, and 2 windows play together on one PC. 🎉

---

## 3. Week 1: make it feel good

- [ ] Type `/config` in Claude Code. Set the **output style** to **Learning**. Now Claude also teaches you as it works.

Type: **"Plan the next milestone: make it feel good."** Say what you want, for example: gamepad, a 2nd player on one PC, animation, more sounds, pause, save the best score, and play stats (F3). Claude makes the cards for your game.

- [ ] Write the **Feel goals** in `PLAYTEST.md` (how long to a first win, how it should feel).
- [ ] From now on, start each session with **"Tune round."** See [4-make-it-better.md](4-make-it-better.md).
- [ ] After each card: ask *"Explain what you changed and why."*
- [ ] After each card: do the "try it by hand" task Claude gives you.

**Done when:** `v0.2.0` works with 2 players on one PC.

---

## 4. Weeks 2–3: online multiplayer

Card G5 made online play in local mode (one network, no key). Now make it work over the internet.

Type: **"set up online rooms"**. The `online` skill teaches how rooms work, quizzes you, then guides you:
- [ ] Log in at gd-sync.com in a **normal** browser (the robot check fails in other browsers). Make your game there, then **API Keys → Create**. Save both keys in Bitwarden.
- [ ] Put the 2 keys in Godot: **Project > Tools > GD-Sync**. They go in `addons/GD-Sync/keys.cfg`, which git ignores.
- [ ] Add the same keys on GitHub: repo → **Settings → Secrets and variables → Actions**: `GDSYNC_PUBLIC_KEY` and `GDSYNC_PRIVATE_KEY` (see [1-setup.md](1-setup.md), part C).
- [ ] Say **"ship it"**. Only new builds get the keys.
- [ ] Room test: host on the web, a friend joins with the 4-digit code on a phone or PC.
- Never paste a key in the Claude chat.

Type: **"Plan the next milestone: online with a key."** The usual cards are: online mode → players leave → version check → release.

- [ ] Paste the matching **GD-Sync docs page** when Claude asks. Claude must not guess.
- [ ] Test every card with 2 instances (**Debug > Customize Run Instances > 2**).
- [ ] Final test: Windows + phone + web in **one** room.

**Done when:** `v0.3.0` — 3 devices on 3 platforms play together.

---

## 5. Weeks 4–6: content

Type: **"Plan the next milestone: content."** For example: more levels, new threats, final art, title screen, music.

- [ ] Art and sound order: **Claude makes it → CC0 stock → make it yourself.** See [4-make-it-better.md](4-make-it-better.md).
- [ ] Draw each level on paper first. Give Claude a photo as the Input.
- [ ] Put every stock asset in `CREDITS.md`.

**Done when:** All levels play from start to end, alone and online.

---

## 6. Week 7: polish and test

### Test matrix
| Test | Windows | Android | Web (PC) | Web (phone) |
|---|---|---|---|---|
| Starts with no errors | ☐ | ☐ | ☐ | ☐ |
| Controls work | ☐ | ☐ | ☐ | ☐ |
| Sound plays | ☐ | ☐ | ☐ | ☐ |
| Save stays after a restart | ☐ | ☐ | ☐ | ☐ |
| Fills the screen | ☐ | ☐ | ☐ | ☐ |
| Joins a room | ☐ | ☐ | ☐ | ☐ |
| Phone on mobile data | — | ☐ | — | ☐ |
| Obtainium update installs | — | ☐ | — | — |

### Playtest
- [ ] 3–5 testers who have not seen the game.
- [ ] Watch. Do not help or explain. Write down where they get stuck.
- [ ] Write what testers said in `PLAYTEST.md`, in their own words.
- [ ] Give Claude the notes: *"Tune round with these notes. Make task cards for problems Tune cannot fix."*
- [ ] Then: **"Plan the next milestone: polish."** For example: particles, flashes, screen shake, the top 3 fixes.

**Done when:** All tests pass, and no tester gets stuck.

---

## 7. Week 8: launch

- [ ] Type: **"Plan the next milestone: launch."** Cards: a README with a screenshot and install steps, a credits check, then tag `v1.0.0`.
- [ ] Share the links with family and friends.
- [ ] Celebrate. 🎉

## 8. After launch
- [ ] Bug cards → `v1.0.1`, `v1.0.2`, …
- [ ] One idea from "Not in v1.0" → `v1.1.0`
- [ ] Write 3 things you learned. Start game #2.
