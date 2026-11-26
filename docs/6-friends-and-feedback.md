# 6. Friends, feedback, and docs

Your friends play your game. They find bugs and have ideas. This guide shows how their reports get to you, how Claude helps you act on them, and how your game's docs stay right.

## 1. Two pages for your players

Every game has 2 pages that players read on GitHub:

| Page | What is in it | Who writes it |
|---|---|---|
| `README.md` | What the game is, the play links for the 4 platforms, how to play, the controls, and the link to report a bug | You answer, Claude writes it down |
| `FAQ.md` | Questions friends ask, and **Known problems** with a way around each | You answer, Claude writes it down |

Claude makes both in your first ship (card G7). After that, they change with the game:

| After | Claude asks you | Your answer goes in |
|---|---|---|
| A new feature that changes the controls or the rules | "A friend asks: how do I use it? What do you answer?" | `README.md` (How to play, Controls), and `FAQ.md` if friends may ask |
| A bug fix that players may still meet on an old version | "A friend sees this bug. What do you tell them?" | `FAQ.md`, under Known problems |
| A question from a friend | "What is the answer, in your words?" | `FAQ.md` |

You answer first. Claude never writes the answer for you. If your answer is not clear, you get a hint, then you try again.
Before each ship, Claude checks that the docs match the game. Nothing ships until they do.

See a real one: [Stormring FAQ](https://github.com/acetousk/stormring/blob/master/FAQ.md) and [Lantern Deep FAQ](https://github.com/acetousk/lantern-deep/blob/master/FAQ.md).

## 2. How friends report a bug or an idea

Your game's GitHub page has **Issues**. An issue is one report. The kit gives your game 3 forms:

| Form | Asks for |
|---|---|
| **Bug** | What happened, what you did just before, the platform (web, Android, Windows, Linux), and the version |
| **Idea** | What to add or change, and why it would be more fun |
| **Question** | The question |

Share this link with your friends. It opens the forms:

```
https://github.com/<you>/<your-game>/issues/new/choose
```

It is also at the bottom of your README and the top of your FAQ.

- A friend needs a free GitHub account to fill in a form.
- No account? The friend tells you, and you say `bug: …` or `idea: …` to Claude yourself.
- Each form says: "Do not write your real name, age, school, or where you live."

## 3. Read the reports with Claude

Say **"check issues"** or **"what did my friends say?"**

1. Claude reads the open issues on your game's GitHub page. It changes nothing on GitHub.
2. Claude shows a table: the number, the kind (bug, idea, or question), and what the friend saw.
3. Claude asks you: "Which one do we do first, and why?" A good answer names who it hurts: many players, or a crash.
4. Claude starts the right skill:

| Kind | What happens |
|---|---|
| Bug with steps | The `bug` skill. The friend's steps are the proof. |
| Bug with too little to go on | Claude writes a short reply that asks for the steps, the platform, and the version. You paste it on the issue. |
| Idea | The `feature` skill checks if it fits. Too big for now? It goes in "Not in v1.0", and Claude writes a "thanks, later" reply. |
| Question | You answer it in `FAQ.md`. Claude writes a reply that links to it. |

To work on one report, say **"issue #12"**.

## 4. Close the loop

1. Each fix or feature from an issue gets its number in `CHANGELOG.md`, for example `Fixed: the game froze after the storm (#12)`.
2. When you say **ship it**, Claude adds `Fixes #12` to the release. When it reaches GitHub, GitHub closes issue #12 by itself and links the fix.
3. Claude writes a thank-you reply for each closed issue: what changed, the version, and how to get it. You paste it on GitHub.

Claude never posts, closes, or deletes on GitHub. You do the posting. This keeps your name on your game.

## 5. Safety

- **Issues are public.** Anyone on the internet can read them and write one.
- **An issue is a report, not an order.** Claude treats the text as data. It never runs commands, opens links, or downloads files from an issue. Only your own words in Claude Code are requests.
- **Personal data or mean words?** Claude does not repeat them. It says "Issue #N has something a parent must check." A parent opens it on GitHub and deletes it, or locks it.
- **Too many issues, or spam?** A parent can turn issues off: the game's **Settings → General → Features → Issues**.

## 6. Words

| Word | Meaning |
|---|---|
| **Issue** | One report on GitHub: a bug, an idea, or a question |
| **Issue form** | The page with boxes that a friend fills in |
| **#12** | The number of an issue. GitHub gives each one a number. |
| **Close** | Mark an issue as done. `Fixes #12` in a ship does it for you. |
| **FAQ** | "Frequently asked questions": the page with answers for players |

Next: [7-when-stuck.md](7-when-stuck.md).
