# 5. Ship it and play with friends

## 1. Ship a new version

1. In Claude Code, say **"ship it"**.
2. Claude checks the game. Then it asks you 3 questions: what is new, how one change works, and who gets it and where. Wrong? You get a hint, not the answer.
3. Claude asks: "only fixes, or something new?" Your answer picks the version number.
4. Say **go**.
5. Click **Allow** on the pop-ups for `git tag` and `git push`. Claude does every git step. You never type a command.
6. Wait about 10 minutes. GitHub builds the game for 4 platforms.
7. Claude checks that the build is green and that the 3 release files are there.

### Version numbers

| Change | Example | New version |
|---|---|---|
| Only fixes | The jump bug is gone | v0.2.1 → **v0.2.2** |
| Something new | A new enemy | v0.2.2 → **v0.3.0** |
| Done and ready for everyone | Your launch | **v1.0.0** |

## 2. The 4 platforms

| Platform | How friends play | How they get updates |
|---|---|---|
| **Web** | Open `https://<your-github-name>.github.io/<your-game>/` in Chrome, Firefox, or Edge | Automatic. Old version? Press **Ctrl + Shift + R**. |
| **Android** | Install **Obtainium**. Tap **Add app** and paste your game's GitHub link. | Obtainium shows the update. Tap **Update**. |
| **Windows** | On your game's GitHub page: **Releases** → `…-windows.zip`. Unzip it, run the game. | Download the new zip |
| **Linux** | **Releases** → `…-linux-x86_64.tar.gz`. Unpack it, run the game. | Download the new file |

Mac and iPhone are not supported. Mac and iPhone players use the web version.

Windows can warn about an unknown app. Click **More info → Run anyway**.

## 3. Online rooms

Up to 4 players. One player hosts, and the others join with a code.

1. Player 1 clicks **Host**. The game shows a 4-digit code.
2. Player 1 sends the code to friends.
3. Each friend types the code and clicks **Join**.

### Before rooms work in the builds

Rooms work inside Godot from card G5 on. For the web, phone, and PC builds, the game needs 2 GD-Sync keys. Say **"play with friends"** to Claude. Claude guides you, one step at a time:

1. Log in to the GD-Sync website **in a normal browser** (Chrome, Firefox, or Edge). The robot check can fail in other windows.
2. Make your game there, and make its API keys.
3. Save both keys in Bitwarden.
4. Put the keys in Godot: **Project → Tools → GD-Sync**.
5. Put the keys in GitHub: your game → **Settings → Secrets and variables → Actions**. Add `GDSYNC_PUBLIC_KEY` and `GDSYNC_PRIVATE_KEY`.
6. Say **"ship it"**.
7. Test a room: the web version on one device, and the PC or phone version on another.

**Never paste a key in the chat with Claude.** Claude never needs to see it. If you paste one by mistake, delete it on the GD-Sync website and make a new one.

Next: [6-when-stuck.md](6-when-stuck.md).
