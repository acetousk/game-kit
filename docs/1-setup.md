# 1. Full setup plan (one time, parent + kid)

Start with the [README](../README.md): it lists every guide and who reads it.
This guide is for the setup adult (someone who is comfortable with computers), with the kid next to you. "Parent" in this guide means that adult. The non-technical guide for parents is [PARENTS.md](../PARENTS.md).

### Kid files vs agent files

| | Kid guides (`docs/`) | Agent files (`starter/AGENTS.md`, `starter/.claude/skills/`) |
|---|---|---|
| Who reads them | People | Claude, automatically, in every session |
| They say | What to click, what to type, what you will see | What Claude must do, and what it must never do |
| Written as | A guide with steps and examples | Short rules |
| Where they live | This kit | Inside the game repo |
| Who changes them | Parent or kid | Only the parent. Claude cannot edit `.claude/`. |

The kid never has to read the agent files. The kid only has to know the answers Claude expects: `ok`, a tweak, `bug: …`, `idea: …`, `?`, `undo`.
Claude makes the other repo files (`DESIGN.md`, `PLAN.md`, `PLAYTEST.md`, …) with the kid in the first session.

## The stack

| Part | Choice |
|---|---|
| Engine | Godot 4.7.2 (GDScript, Compatibility renderer) |
| AI | Claude (Claude.ai + Claude Code), on the parent's account |
| Multiplayer | GD-Sync (hosted, free up to 4 players per lobby) |
| Code + builds | GitHub + GitHub Actions |
| Platforms | Windows, Linux, Android, Web |
| Passwords | Bitwarden: one free vault for each person |
| Distribution | GitHub Releases (Windows, Linux, Android via Obtainium), GitHub Pages (Web) |

**Order of setup (about 4 hours for one kid; parts B–E again for each extra kid):**

| Part | Who | Time |
|---|---|---|
| A. Rules and services | Parent | 15 min to read |
| B. Accounts | Kid + parent | 45 min |
| C. Repo, signing, and GitHub settings | Parent + kid | 60 min |
| D. The kid's PC | Kid + parent | 60 min |
| E. The Godot project and a pipeline test | Parent + kid | 60 min |
| F. After setup: the parent's part | Parent | 30 min per week |

---

## A. Rules and services

### Rules

- **Claude needs users who are 18+.** You own the Claude account. The kid uses it on the family PC, with you nearby. Check in on the work each week.
- **The kid owns the game accounts.** The kid signs up with their own email and keeps each password in their own **Bitwarden**. Claude is the one exception: Claude Code uses your account. Never make a Claude account for the kid.
- **2FA only when a site requires it.** If the site offers email codes, use email. If not, use a passkey. Save the recovery codes in Bitwarden.
- **One set per kid.** With two kids, do parts B–E once for each kid. Each kid gets their own accounts and their own repo.
- **You keep:** the Claude account, the money, and a USB copy of the Android keystore.
- **The kid uses a nickname online.** No real name, school, city, or photos in the repo or the game.

### Services

#### Required

| Service | Who signs up | Cost | Why | Sign-up notes |
|---|---|---|---|---|
| **Claude Pro** (claude.com) | Parent | About $20/month (check claude.com/pricing) | Claude.ai chat + Claude Code | Upgrade to Max only if you hit the usage limits often. Turn off AI training at claude.ai/settings/data-privacy-controls (see [PARENTS.md](../PARENTS.md#is-it-safe)). |
| **Email** | Kid | $0 | Used for all the kid's game accounts | Use the nickname, not the real name |
| **Bitwarden** (bitwarden.com) | Kid | $0 (free personal vault) | Passwords, recovery codes, the keystore, and the GD-Sync keys | |
| **GitHub** (github.com) | Kid | $0 | Code, history, automatic builds, releases, web hosting | Nickname username, letters, numbers, and `-` only (no `_`). Turn on "Keep my email address private". |
| **GD-Sync** (gd-sync.com) | Kid | $0 (free plan: 4 players per lobby, 200 MB/day) | Online multiplayer with no server | Read the privacy terms |

#### Optional, now

| Service | Cost | Why |
|---|---|---|
| itch.io | $0 | A second place to post the game and get comments from players |
| Aseprite (on Steam) | About $20 once | The best pixel-art tool. Free choices: Piskel (web) and LibreSprite. |
| A USB gamepad | About $20–40 | To test local co-op and gamepad controls |

#### Later (do not buy now)

| Service | Cost | When |
|---|---|---|
| GD-Sync paid plan | Monthly | When lobbies need more than 4 players, or the game passes 200 MB/day |
| Google Play Developer | $25 once (18+) | Only if you want the Play Store, not Obtainium |
| Apple Developer | $99/year (18+) + a Mac | Only for iOS or signed macOS builds |
| Windows code signing | Varies | Only if the SmartScreen warning becomes a problem |
| Claude API | Pay per use | Only if a later game uses Claude **inside** the game |

#### Monthly total

| Setup | Cost |
|---|---|
| Required only | **About $20/month** (Claude Pro) |
| + Aseprite + gamepad | + about $40–60 once |

---

## B. Accounts (kid + parent, 45 min per kid)

The examples use the nickname `kidname`. Use your kid's own nickname instead.

- [ ] Parent: make or upgrade **your** Claude account to **Pro**. Claude Code on the kid's PC signs in with it.
- [ ] Kid: make your own email address with your nickname, not your real name.
- [ ] Kid: make a free **Bitwarden** account with that email. Install the desktop app, the browser extension, and the phone app.
      Use a long master passphrase (4–5 random words). Write it on paper and give it to the parent in an envelope. **Nobody can reset it.**
- [ ] Kid: with your email, make these accounts. Use Bitwarden's **Generate password** for each, and save each in Bitwarden:
  - [ ] **GitHub**: the nickname as the username (no `_`). Turn on **Keep my email address private** (Settings > Emails).
  - [ ] **GD-Sync**: you need it in card G5. Make a project there, and save its 2 keys in Bitwarden.
  - [ ] Optional: **itch.io** (lowercase name)
- [ ] 2FA: turn it on only when a site requires it. See the rule in part A. GitHub can require 2FA later. Add a **passkey** before its deadline.

**Never** share a password in chat, in the repo, or with Claude.

### Claude.ai Project (10 min)
- [ ] In Claude.ai, click **Projects > New project**. Name it with the game's name. Make one project per kid.
- [ ] Paste this into **Project instructions**:
  ```
  I am helping a 16-year-old make their first game in Godot 4.7.2 (GDScript).
  Multiplayer uses GD-Sync. Platforms: Windows, Linux, Android, Web.
  - Always use Godot 4 syntax. Never Godot 3.
  - Short, simple explanations. One small step at a time.
  - After each answer, give one small change the kid can make alone.
  - Keep the game small. Put big new ideas in the "Not in v1.0" list.
  ```
- [ ] After the first playable, add `DESIGN.md` and `PLAN.md` from the repo to the project files.

---

## C. Repo, signing, and GitHub settings (parent + kid, 60 min per kid)

### Repo (20 min)
The [starter/](../starter) folder has all the repo files: the agent rules, the skills, the settings, the build pipeline, and an empty Godot 4.7.2 project with the 4 export presets.

| Starter file | What it does |
|---|---|
| `AGENTS.md`, `CLAUDE.md` | The rules for Claude. `CLAUDE.md` is one line, `@AGENTS.md`, so Claude Code loads `AGENTS.md`. |
| `SKILLS.md` | The kid's list of what to say to Claude |
| `.claude/skills/` | The kit skills: plan, quiz, build, ship, online, and more |
| `.claude/settings.json` | What Claude may do alone, what needs a pop-up, and what is locked |
| `.gitignore` | Keeps secrets and build files out of the repo |
| `.github/workflows/release.yml` | Builds the 4 platforms when a version tag is pushed |
| `project.godot`, `export_presets.cfg`, `icon.svg`, `scenes/setup_check.tscn` | The empty project (part E) |

- [ ] Sign in to GitHub as the kid. Make a new **empty, public** repo. Name: the kid's game, for example `kidname-game`.
- [ ] Download this kit: on its GitHub page, click **Code > Download ZIP**. Unzip it.
- [ ] Clone the kid's empty repo with GitHub Desktop (part D, "Set up the game folder").
- [ ] Copy **everything inside** `starter/` into the game folder, including the hidden `.claude`, `.github`, and `.gitignore`.
- [ ] In `.github/workflows/release.yml`, change `GAME: my-game` to the repo name.
- [ ] In `export_presets.cfg`, change `package/unique_name="com.nicknamegames.mygame"` to a unique name, for example `com.kidname.game`. Never change it after the first release.
- [ ] In `project.godot`, change `config/name="My Game"` to the game's name (the kid can change it later).
- [ ] In GitHub Desktop, commit with the message `Start from the game kit`, then click **Push origin**.

### Android signing (20 min)
- [ ] Make the release keystore (on any PC with Java 17):
  ```
  keytool -genkeypair -v -keystore release.keystore -alias mygame -keyalg RSA -keysize 2048 -validity 10000
  ```
- [ ] Save the keystore file (as an attachment) and its password in the kid's Bitwarden. The parent keeps a copy on a USB drive.
- [ ] Make a base64 copy: `base64 -w0 release.keystore > release.keystore.b64` (Git Bash on Windows).
- [ ] **Do not** put the keystore in the repo.

### GitHub settings (20 min)
- [ ] **Settings > Secrets and variables > Actions**. Add:
  | Secret | Value |
  |---|---|
  | `ANDROID_KEYSTORE_B64` | Contents of `release.keystore.b64` |
  | `ANDROID_KEY_ALIAS` | `mygame` |
  | `ANDROID_KEY_PASSWORD` | The keystore password |
  | `GDSYNC_PUBLIC_KEY` | The GD-Sync public key. Add it after card G5. |
  | `GDSYNC_PRIVATE_KEY` | The GD-Sync private key. Add it after card G5. |

  With no GD-Sync secrets, the builds work, but they cannot play online. Co-op then works only in Godot (2 windows, local mode).
- [ ] **Settings > Pages**. Set **Source** to **GitHub Actions**.
- [ ] **Settings > Environments > github-pages > Deployment branches and tags**. Add a tag rule `v*`.

---

## D. The kid's PC (kid + parent, 60 min)

### Apps to install

#### Required

| App | What it is for | How to get it | Cost |
|---|---|---|---|
| **Godot 4.7.2** (standard, **not** .NET) | The game engine | godotengine.org/download/windows | Free |
| **Git for Windows** | Saves versions of the game. Claude Code also needs it. | git-scm.com, or `winget install Git.Git` | Free |
| **GitHub Desktop** | Clone the repo, and see each save in History. Claude does the commits and pushes. | desktop.github.com, or `winget install GitHub.GitHubDesktop` | Free |
| **Claude desktop app** | Claude chat + **Claude Code** (the "Code" part) | claude.com/download | Parent's Pro plan |
| **Chrome or Edge** | Test the web build | Already on Windows (Edge) | Free |
| **Bitwarden** (desktop app + browser extension + phone app) | Keeps all your passwords and 2FA recovery codes | bitwarden.com/download, or `winget install Bitwarden.Bitwarden` | Free |
| **Python 3** | Lets Claude make PNG art and WAV sounds with scripts | `winget install Python.Python.3.12`, then `pip install pillow` | Free |

#### For art and sound

| App | What it is for | How to get it | Cost |
|---|---|---|---|
| **Pixelorama** | Pixel art + animation (main art tool) | pixelorama.org | Free, open source |
| **Piskel** | Pixel art in the browser | piskelapp.com | Free |
| **Aseprite** (optional) | Better pixel art and animation | Steam | About $20 |
| **Krita** (optional) | Painted art | krita.org, or `winget install KDE.Krita` | Free |
| **jsfxr** | Retro sound effects in the browser | sfxr.me | Free |
| **BeepBox** | Simple music in the browser | beepbox.co | Free |
| **Audacity** | Cut and edit sounds | audacityteam.org, or `winget install Audacity.Audacity` | Free |

#### Optional

| App | What it is for |
|---|---|
| **VS Code** + the **godot-tools** extension | A bigger code editor. Godot's built-in editor is enough at first. |
| **Obtainium** (on an Android phone) | Install and update the game on the phone |
| A USB gamepad | Test gamepad and local co-op controls |

#### Free assets (use only these, or your own work)

| Site | What | License |
|---|---|---|
| kenney.nl | Art, sounds, fonts | CC0 (free for anything) |
| opengameart.org | Art, music | **Check each item.** Use CC0 or CC-BY only. |

Write every asset you use in `CREDITS.md`. See [4-make-it-better.md](4-make-it-better.md) for the license rules.

### Put Godot on the PATH, so Claude Code can use it

Claude Code checks the game for errors with a `godot` command. Do these steps once:

1. Download Godot **4.7.2**, **Windows 64-bit** zip. Use this exact version, because `release.yml` uses it.
2. Make the folder `C:\Tools\Godot`.
3. Unzip both files into it:
   - `Godot_v4.7.2-stable_win64.exe` (the editor you open)
   - `Godot_v4.7.2-stable_win64_console.exe` (the one that prints errors)
4. Copy the **console** file in the same folder. Name the copy `godot.exe`.
5. Press **Start**, type **"environment variables"**, and open **Edit environment variables for your account**.
6. Select **Path**, click **Edit > New**, and add `C:\Tools\Godot`. Click **OK**.
7. Open a new **Git Bash** window. Type `godot --version`. You must see the version number.
8. Right-click the editor `.exe` and choose **Pin to Start**.

When Godot updates, replace both files and the `godot.exe` copy. Then tell the parent, because `release.yml` must use the same version.

### Set up the game folder

1. Open **GitHub Desktop** and sign in with your GitHub account.
2. Click **File > Clone repository**. Choose your game repo from part C (for example `kidname/kidname-game`).
3. Save it to `C:\Games\my-game`. Do not use OneDrive folders, because they cause sync problems.
4. Open Godot. The first time, do part E to import the project from `C:\Games\my-game`. After that, open it from the project list.
5. Open the **Claude** app. Go to **Code**, and choose the folder `C:\Games\my-game`.
6. In Godot, open **Editor > Editor Settings > Text Editor > Behavior**. Turn on **Auto Reload Scripts on External Change**. Godot then loads Claude's changes with no pop-up.
7. In Claude Code, type `/model` and choose **Opus 5.5**. The first-playable budget is set for this model.
8. Keep the default output style for the first playable. After it, type `/config` and set the **output style** to **Learning**.
9. Do this step after part E. Type: `What do we do first?` Claude must do the first run: a ✅/❌ setup check, then how you work together, then card G1.

### Window layout

Put 2 windows side by side:

```
┌──────────────────────────┬────────────────────────┐
│                          │                        │
│   Godot (left, bigger)   │   Claude Code (right)  │
│   F5 = play the game     │   step → ▶ → answer    │
│                          │                        │
└──────────────────────────┴────────────────────────┘
       GitHub Desktop: see the saves (History). Claude makes them.
```

Press **Win + Left arrow** and **Win + Right arrow** to place the windows.

### Keyboard shortcuts

| Where | Keys | What it does |
|---|---|---|
| Godot | **F5** | Play the game |
| Godot | **F6** | Play the open scene only |
| Godot | **F8** | Stop the game |
| Godot | **Ctrl + S** | Save the scene |
| Godot | **Ctrl + Shift + F** | Search all files |
| Claude Code | **Shift + Tab** | Switch mode. The repo starts in plan mode. |
| Claude Code | **Esc** | Stop Claude |
| Claude Code | `/clear` | Start fresh (do this between features) |
| Windows | **Win + Shift + S** | Screenshot (paste it into Claude to show a problem) |

---

## E. The Godot project and a pipeline test (parent + kid, 60 min)

### Godot project (30 min, with the kid)
The starter files already have the project, the settings, and the 4 export presets. You only check them.

- [ ] In Godot, click **Import**. Choose `C:\Games\my-game\project.godot`. Click **Import & Edit**.
- [ ] Press **F5**. You must see "Setup works!".
- [ ] In **Project > Project Settings** (turn on **Advanced Settings**), check:
  | Setting | Value | Why |
  |---|---|---|
  | Rendering > Renderer > Rendering Method | `gl_compatibility` | Works on web and phones |
  | Display > Window > Stretch > Mode | `canvas_items` | Fills any screen size |
  | Display > Window > Stretch > Aspect | `expand` | No black bars on phones |
  | Rendering > Textures > VRAM Compression > Import ETC2 ASTC | On | Needed for Android |
- [ ] Install the export templates: **Editor > Manage Export Templates > Download and Install**.
- [ ] In **Project > Export**, check the 4 presets: `Android`, `Windows Desktop`, `Linux`, `Web`. `release.yml` uses these exact names.
  - `Windows Desktop` and `Linux`: **Embed PCK** is on. Then each build is one file.
  - `Android`: the **INTERNET** permission is on (for GD-Sync).


### First release (30 min)
- [ ] Check that `GODOT_VERSION` and the `godot-ci` image tag in `release.yml` are `4.7.2`, the same as `godot --version`.
- [ ] Tag `v0.0.1` on the empty project and push it. In GitHub Desktop: **History**, right-click the newest commit, **Create Tag**, then **Push origin**. This tests the pipeline. The kid's real first release is `v0.1.0` at the end of the first playable (card G7).
- [ ] Watch **Actions** until the run is green.
- [ ] Test: install the APK with Obtainium, run the Windows `.exe`, open the Pages URL.

**Setup is done when:** In Claude Code, `What do we do first?` gets the first-run check list, with every line ✅. Claude then explains how you work together and offers card **G1** (design + scope). Then read [2-godot-basics.md](2-godot-basics.md) with the kid, and go to [3-make-the-game.md](3-make-the-game.md).

---

## F. After setup: the parent's part

### Weekly (about 30 minutes per week)

| When | What |
|---|---|
| Weekly planning (15 min) | Sit with the kid. Read `PLAN.md`. Agree on this week's goal. See [4-make-it-better.md](4-make-it-better.md). |
| Mid-week (5 min) | Ask: "Show me what you made." |
| End of week (10 min) | Play the newest version. Check the Claude usage. Check that `git log` has commits. |

### Safety checks (monthly)

- [ ] No real names, school, city, or photos in the repo, the game, or the commits.
- [ ] No free text chat in the game. Room codes only, with no public lobby list.
- [ ] Secrets are only in GitHub Secrets and Bitwarden, not in files.
- [ ] If GitHub asks for 2FA, the kid has a passkey and the recovery codes are in Bitwarden.
- [ ] Keystore backups still exist.
- [ ] GD-Sync usage is under the free limits.

### When to step in

| Sign | What to do |
|---|---|
| The kid cannot explain their own code | Make it a rule: ask Claude to explain each new script before every commit |
| The scope keeps growing | Point to "Not in v1.0" in `DESIGN.md`. Finish v1.0 first. |
| The kid has been stuck for over 2 sessions | Sit with them for one build loop |
| The red X in GitHub Actions stays | Open the log. Paste the error into Claude Code together. |
| Motivation drops | Make the weekly goal smaller. Show the game to friends or family. |

---

## Appendix: the locked files

These files are in [starter/](../starter). Read them there, so you always see the newest version.

| File | What to know |
|---|---|
| [`.claude/settings.json`](../starter/.claude/settings.json) | Claude Code starts in plan mode. It cannot edit the build pipeline, its own rules, the kit skills, or secrets. `git tag` and `git push` always show a pop-up. |
| [`.gitignore`](../starter/.gitignore) | Keeps `.godot/`, builds, keystores, and `addons/GD-Sync/keys.cfg` out of the repo |
| [`.github/workflows/release.yml`](../starter/.github/workflows/release.yml) | On a `v*` tag: builds Android, Windows, Linux, and Web, makes a GitHub Release, and puts the web build on GitHub Pages |
