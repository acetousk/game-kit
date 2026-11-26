# 4. Make it better

How the game gets better over time, in plain words. Read [3-make-the-game.md](3-make-the-game.md) first.

## 1. The tune loop

You say how it **feels**, in plain words. Claude turns that into **one** small change. You play and decide.

### The loop (2–5 minutes per round)

```
 1. PLAY     Play one run. Press F3 to see the stats.
 2. SAY      Say how it feels, in plain words:
               "the start is boring"   "jumps feel floaty"   "I die and don't know why"
 3. WHY      Claude asks which number you think causes it, and gives hints.
             Then it names 1–3 numbers in Tune, and asks what one change will do.
 4. CHANGE   Claude changes ONE number: "enemy_speed 120 → 90".
 5. PLAY     Play again. Look at F3: did the stats move?
 6. DECIDE   "keep" or "undo".
 7. LOG      Claude adds one line to PLAYTEST.md.
   │
   └──► next feeling, or stop
```

### Where the numbers live

All feel numbers are in one file: `scripts/tune.gd` (the `Tune` node).
Each number has a plain name and a comment, for example:

```gdscript
@export var player_speed := 300.0   # How fast you move. Higher = faster.
@export var enemy_speed := 120.0    # How fast enemies move. Higher = harder.
@export var safe_time := 1.0        # Seconds you cannot be hit after a hit.
```

You can also change them yourself while the game runs: **Scene > Remote > Tune > Inspector**.

### Feeling → numbers (examples)

Claude reads your game. These are only examples.

| You say | Numbers it is often | Why |
|---|---|---|
| "Too hard" | threat speed, damage, lives, how often threats come | Less pressure per second |
| "Too easy" / "boring" | the same, the other way; how fast it gets harder | More pressure, or it grows sooner |
| "Floaty" / "heavy" | gravity, jump or acceleration, friction | How fast speed changes |
| "Unfair" | hitbox size, safe time, warning time | You need time to see a danger and react |
| "Slow start" | time to the first goal or threat | The fun must start in the first 10 seconds |
| "I don't know what to do" | — (no number) | It needs a **card**: a hint, a sign, or a clear goal on screen |

When no number fits, Claude makes a task card instead. Then the normal plan flow runs.

### The stats (F3)

Ask for these in the "feel good" milestone: *"Add play stats with an F3 screen."*

The game saves simple stats on **your** device only (`user://stats.json`). Nothing goes online.

| Stat | What it tells you |
|---|---|
| Time per run | Is it too short or too long? |
| Win or lose | Is it too hard or too easy? |
| Where you lost | Which part is the problem |
| Score | Do you get better over time? |

Compare the stats with the **Feel goals** at the top of `PLAYTEST.md`. That is how you know a change helped, not only felt different.

### Juice: can you see and hear it?
A game feels good when it answers you. Play one run and check:

| Ask yourself | If not, say to Claude |
|---|---|
| Do I hear and see it when I do something? | "Picking up a box has no sound" |
| Do I know when my hit lands? | "I can't tell if I hit" |
| Do I know who hit me, and from where? | "I lose and don't know why" |
| Do I know where to go when there is danger? | "I don't know where to run" |
| Can I tell the enemies apart? | "All the bots look the same" |

Claude also tests your game with a **robot player** that plays a match and takes screenshots. A game window opens by itself for about 2 minutes: do not click it. The robot finds bugs. Only you can say if it is fun.

### Rules
- **One change at a time.** With 2 changes, you cannot tell which one helped.
- **Play at least one full run** before "keep" or "undo".
- **Your feeling wins.** The stats help you decide, but they do not decide for you.
- **Log every change**, also the undos. Then you do not try the same thing twice.
- **Ask other people.** You get used to your own game. A new player feels it fresh.

## 2. New cards for new ideas

| Rule | Good | Bad |
|---|---|---|
| One visible result | "Player can double jump" | "Improve the player" |
| 5–30 minutes, steps of about 1 minute | "Coin pickup sound" | "All the sound" |
| Input is small | `player.gd`, `DESIGN.md` | "the whole project" |
| Output is named | `scenes/pause.tscn` | "some UI" |
| "Done when" is a test you can do | "Esc pauses the game" | "It works" |

When you do not know the Output, ask Claude: *"Write a task card for: \<idea\>."* Claude writes the card. You check it, then say "Do it."

Too big? Split it:

| Too big | Split into cards |
|---|---|
| "Make multiplayer" | connect → make lobby → join → sync players → host owns state → leave handling |
| "Make level 2" | draw on paper → layout → enemies → pickups → playtest |

## 3. Weekly planning (15 minutes, kid + parent)

1. **Show (5 min):** Play the newest version. Read the last week of `PLAYTEST.md`.
2. **Look back (3 min):** Which cards are done? Why are the others not done?
3. **Choose (5 min):** One week goal and 3–8 cards in "This week".
4. **Scope (2 min):** New ideas go to "Not in v1.0" in `DESIGN.md`.

When cards are not done 2 weeks in a row, they are too big. Split them.

## 4. Milestones

| Version | Name | When |
|---|---|---|
| `v0.1.0` | First playable | Day 1 (about 75 min of Claude work) |
| `v0.2.0` | Feels good (co-op, sound, animation) | Week 1 |
| `v0.3.0` | Online multiplayer | Week 2–3 |
| `v0.4.0` – `v0.6.0` | Content | Week 4–6 |
| `v0.9.0` | Polish + test | Week 7 |
| `v1.0.0` | Launch | Week 8 |

If the plan slips, **cut cards, not quality.** Move cards to "Not in v1.0". Keep the launch week.

## 5. Art and sound

### The order: Claude → stock → make it yourself

For every art or sound item, try these in order:

| Step | Who | How | Use it when |
|---|---|---|---|
| **1. Claude makes it** | Claude Code | Writes SVG files, or runs a small script in `tools/` that outputs PNG or WAV files | Claude's result looks good enough |
| **2. Stock asset** | Kid downloads it | Kenney.nl first (CC0), then other CC0 / CC-BY sites | Claude's result does not look good enough |
| **3. Make it yourself** | Kid | Pixelorama, jsfxr, BeepBox | No good stock asset fits |

Ask Claude for the item. Look at it in the game. If it is not good enough after 2 tries, go to the next step.

### Step 1 — What Claude makes well

| Item | How Claude makes it | Usually good enough? |
|---|---|---|
| UI: buttons, panels, icons, health bars | SVG | ✅ Yes |
| Simple characters and enemies (shapes, flat colors) | SVG | ✅ Yes |
| Tiles with simple patterns | SVG or a PNG script | ✅ Mostly |
| Backgrounds: sky, gradients, stars, hills | SVG, a script, or a Godot shader | ✅ Yes |
| Effects: particles, flashes, trails, screen shake | Godot code | ✅ Yes |
| Game icon | SVG | ✅ Mostly |
| 3D: characters, props, levels from simple shapes | Godot primitive meshes + palette materials | ✅ Yes |
| 3D: detailed models | — | ❌ Use Kenney CC0 3D kits (glTF) |
| Retro sound effects (jump, coin, hit, click) | Python script that writes WAV files | ✅ Mostly |
| Detailed pixel-art characters with animation | PNG script | ⚠️ Sometimes |
| Music | Python script (simple chiptune loop) | ⚠️ Simple loops only |
| Voices, real-world sounds, painted art | — | ❌ No → go to step 2 |

#### What Claude needs
- **SVG:** nothing. Godot opens SVG files directly.
- **PNG and WAV scripts:** Python on the PC (`winget install Python.Python.3.12`). For PNG: `pip install pillow`.

#### Rules for Claude-made assets
- Scripts go in `tools/` (for example `tools/make_sfx.py`). Run them again to change the asset.
- Output goes in `assets/art/` and `assets/audio/`.
- Use only colors from the palette in `DESIGN.md`.
- Use one pixel size for all characters (16×16 or 32×32).

#### Prompts
> Make the player character as an SVG, 32×32, using the palette in DESIGN.md. A small round robot with big eyes. Set it up as the player sprite.

> Write tools/make_sfx.py that makes jump.wav, coin.wav, hit.wav, and click.wav as retro 8-bit sounds. Run it and hook the sounds up to the game.

> Make a 4-frame run animation for the player as a PNG sprite sheet with a script in tools/. Set up an AnimatedSprite2D with idle and run.

> Make a 16-second chiptune loop for the menu with a script in tools/. Loop it in the main menu.

### Step 2 — Stock assets

| Site | What | Licenses |
|---|---|---|
| **kenney.nl** | Art, UI, sounds, fonts | CC0 for everything. **Try this first.** |
| opengameart.org | Art, music, sounds | Mixed. Check each item. |
| itch.io → game assets → free | Art and sound packs | Mixed. Read each page. |
| freesound.org | Sound effects | Mixed. Filter by license. |
| fonts.google.com | Fonts | OFL |

| License | OK? |
|---|---|
| CC0 | ✅ |
| CC-BY | ✅ Put the creator's name in `CREDITS.md` and in the game credits |
| OFL (fonts) | ✅ |
| CC-BY-SA | ⚠️ Ask the parent |
| CC-BY-NC, "personal use only", no license, art from other games | ❌ Never |

Write every stock asset in `CREDITS.md`. Then ask Claude to recolor it to the palette, if needed.

### Step 3 — Make it yourself (free tools)

| Tool | What for | Get it |
|---|---|---|
| **Pixelorama** | Pixel art + animation | pixelorama.org |
| Piskel | Pixel art in the browser | piskelapp.com |
| Krita | Drawing and painting | krita.org |
| **jsfxr** | Retro sound effects | sfxr.me |
| **BeepBox** | Simple music | beepbox.co |
| Audacity | Record and edit sounds | audacityteam.org |
