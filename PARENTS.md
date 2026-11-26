# Your Kid Is Making a Video Game

A short guide for parents. You do not need to know anything about computers or code.

## In one minute

- **What:** your kid designs their own video game. Friends can play it in a web browser, on an Android phone, or on a PC.
- **How:** an AI helper called Claude writes the code. Your kid makes every choice: the idea, the look, and the rules.
- **The catch:** Claude only builds what your kid understands. Before each change, it asks your kid questions about the plan. If an answer is wrong, Claude gives a hint, not the answer.
- **Time:** the first playable game takes about 2 hours. After that, your kid makes it better week by week.
- **Cost:** one paid Claude plan on an adult's account. Everything else is free.
- **Your part:** about 10 minutes a week. Play the game and ask your kid to explain one new thing.

## What your kid learns

| Skill | How the game teaches it |
|---|---|
| **Planning** | Each change starts as a short plan: what goes in, what comes out, and how to test it. |
| **Problem solving** | When something breaks, your kid finds the cause with Claude. Claude does not just fix it. |
| **Explaining** | Your kid must explain each new part before it goes out to friends. |
| **Design** | Your kid decides what is fun, then tests it and changes it. |
| **Taking feedback** | Friends report bugs and ideas. Your kid decides what to do first, and why. |
| **Finishing** | Small steps, each one playable. Your kid ships real versions that friends use. |

## Is the AI doing the work for them?

It writes the code. It does not do the thinking. The kit holds Claude to fixed rules:

1. Your kid says what they want, for example "add an enemy that chases me".
2. Claude explains the idea in plain words and shows a short plan.
3. Claude asks 1–3 questions. Example: "If the enemy is faster than you, what happens when you run?"
4. **Nothing is built until your kid answers well and says yes.** A wrong answer gets a hint and a new try.
5. Claude builds one small step. Your kid plays it and says what to change.
6. Nothing goes out to friends until your kid can explain what is new.

If your kid says "skip the quiz", Claude asks an easier question. It does not skip it.

**The best test is simple: ask your kid how something in their game works.** If they can tell you, it is working.

## Is it safe?

**The game:**
- The game has **no chat**, no player accounts, and collects no personal data.
- Friends play together with a 4-digit room code. Only people who get the code can join.
- Do not put real names, photos, or your home town in the game.

**The AI helper:**
- It works only on the game's files, on your kid's computer.
- It never asks for a password, and it never downloads files from the internet.
- It cannot change its own rules. Only the adult who set it up can change them.
- It cannot copy other games. It makes your kid's own version.

**Public pages:**
- The game and its code are on a public website (GitHub), so friends can play it. Anyone with the link can see it.
- Friends can send bug reports and ideas there. Anyone with a free account can write one, so a stranger could too.
- Claude reads each report as a report only. If a report has personal details or mean words, Claude does not repeat it. It tells your kid to get a parent. Sit with your kid, open it, and click **Delete**. Or ask the adult who set it up.

**Your Claude account and AI training:**
Claude Pro is on an adult's account. By default, Anthropic may use its chats and coding sessions to train new AI models. Your kid's game chats go through this account, so turn training off once:

1. Sign in at claude.ai with the account Claude Code uses.
2. Open [claude.ai/settings/data-privacy-controls](https://claude.ai/settings/data-privacy-controls). (Or: your name → **Settings** → **Privacy**.)
3. Turn off the switch that lets Anthropic use your chats to improve its AI models.

| | Training off | Training on |
|---|---|---|
| New chats and Claude Code sessions | Not used to train models | Used to train models |
| How long Anthropic keeps them | 30 days | 5 years |

- The switch covers claude.ai and Claude Code together. Claude Code has no second switch.
- It works from now on. Chats from before you turned it off can already be in training.
- **The kit turns off feedback uploads.** The `/feedback`, `/bug`, and `/share` commands would send a copy of the chat and the game code to Anthropic, kept for 5 years. The kit's settings turn them off, and turn off the "How is Claude doing?" survey. Claude cannot change these settings.

**Passwords:** each account password is kept in a free password manager (Bitwarden). It is never in a note or in the chat with Claude.

## Who does what

| Who | Does |
|---|---|
| **Your kid** | Every idea and every choice. Answers Claude's questions. Plays and tests each step. Decides when a version is ready. |
| **Claude** | Explains, plans, asks questions, and writes the code. Sends each new version out when your kid says so. |
| **The setup adult** | Someone who is comfortable with computers. Sets up the computer and the accounts once, and fixes setup problems. The steps are in [docs/1-setup.md](docs/1-setup.md). This does not have to be you. |
| **You** | Play the game. Ask questions. Step in if something feels wrong. |

## Your 10 minutes a week

Play the newest version with your kid. Then ask one or two of these:

- "What is new since last week?"
- "How does that part work?"
- "What did you change after you tested it?"
- "What did your friends say? What will you do about it?"
- "What is next, and why?"

You do not need to understand the answer in detail. Listen for whether your kid can explain it in their own words.

## When to step in

| You see | Do this |
|---|---|
| A box on screen asks to "Allow" something, and nobody knows what it is | Click **No**. Your kid asks Claude "what was that?" |
| Your kid says Claude asked for a password or a code | Say no. Tell the setup adult. |
| A friend's report has personal details or mean words | Delete it with your kid (see "Is it safe?"). |
| Your kid is stuck on the same problem 3 times | Suggest a break. Ask the setup adult to sit in for one session. |
| Something does not work and nobody knows why | Your kid says **"check my setup"** to Claude. Claude lists what is wrong and who fixes it. |

## What it costs

| What | Cost |
|---|---|
| Claude Pro (the AI helper) | A monthly plan, on an adult's account, because Claude needs users to be 18+ |
| Godot (the game maker), GitHub (the website), the room service, and the password manager | Free |

## Try a game made with this kit

- [Stormring](https://github.com/acetousk/stormring): a 3D food fight in a giant school lunchroom (tomatoes, no guns), played solo or online with up to 4 players.
- [Lantern Deep](https://github.com/acetousk/lantern-deep): a 2D cave game, played solo or with friends.

Each page has a "Play" section with the link for the web, phone, and PC.

## A few words you may hear

| Word | Meaning |
|---|---|
| **Godot** | The free program that makes the game |
| **Claude** | The AI helper |
| **GitHub** | The website where the game is kept and where friends get it |
| **Ship** | Send a new version out to friends |
| **Skill** | A fixed set of steps Claude follows for one kind of job, like "fix a bug" |
| **Issue** | A bug report or idea from a friend, on GitHub |
