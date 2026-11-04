# QBR Slide Writer

A skill that turns a slide's raw numbers and the point you want to make into
executive QBR slide copy you can paste straight into your deck:

- **Headline:** ten words or fewer, one clear claim
- **Subhead:** one sentence with the number, the date, and the reason
- **Visual:** which chart, table, or metric boxes should carry the numbers
- **Recommendation:** one next step, naming who or what it depends on
- **Flags:** anything that cannot be backed up yet, so nothing gets made up

It writes the words only. Your deck template still owns the layout.

Owner: Will Mather (Marketing)

## How to use it (for now)

Until this skill is added to the shared skills library, use it by pasting:

1. Open [`skills/qbr-slide-writer/SKILL.md`](skills/qbr-slide-writer/SKILL.md)
   and copy everything in it (the copy icon at the top right of the file
   works).
2. Start a new chat with your AI assistant and paste it in.
3. Underneath, write: **"Use this skill for the slide below."** Then add:
   - What happened (a launch, a test, a migration, or something that ended)
   - The numbers, and which ones are final versus still being checked
   - The one thing you want the room to take away
   - Who reviews the deck and who will be in the room
4. Paste the results into your deck. Do one slide at a time.

**Tip:** say which numbers are final and which are still being checked. If
you don't, expect a lot of flags.

## Once it is in the shared library

Nobody will need to paste anything. In any chat, describe what you need, for
example *"Turn these campaign numbers into an executive slide"*, or type
`/qbr-slide-writer`.

## What is in this repo

| Path | What it is |
|------|------------|
| `skills/qbr-slide-writer/SKILL.md` | The skill itself |
| `.opencode/commands/qbr-slide-writer.md` | The `/qbr-slide-writer` command, used once it is in the library |

The folder layout matches the shared skills library, so these files can be
copied over as they are.

## Suggesting changes

Open an issue in this repo, or message Will.
