# hebrew-voice

A Claude skill for writing and editing Hebrew that sounds like a person, not a company or an AI. Use it for any Hebrew text: website copy, landing pages, social posts, captions, DMs, chatbot or agent replies, and Claude's own replies when it answers in Hebrew.

## What it does

When Claude writes or edits Hebrew, the skill makes it:

- follow the voice defined in `voice.md`
- never invent a speaker: no made-up name, role or backstory
- pick a register: **everyday** for posts, captions, chats and product copy, or **serious** for pricing, billing, legal, outages and anything where trust is on the line
- avoid common AI and ad-copy patterns: punchy "לא X" claims, "בלי X ובלי Y", triads, dramatic one-word sentences, colons in headings, reassurance filler, bureaucratic Hebrew, polite chatbot phrases, emoji as filler and em dashes
- prefer specifics, real numbers and everyday Israeli phrasing over claims
- run a rewrite pass before returning any text
- leave a visible `[placeholder]` instead of making up facts

## Files

| Path | What it is |
|------|------------|
| `SKILL.md` | Skill entry point. Tells Claude to read `voice.md`, then run the rewrite pass. |
| `voice.md` | The voice itself: who's talking, registers, what to learn from good Israeli copy, rules, banned patterns and the rewrite pass. It also works without the skill, as a system prompt for any model. |
| `samples/` | Your real writing samples, to share with Claude when you want it to match your voice. |
| `references/` | Optional and gitignored. Raw examples from brands and media, kept locally for study. |
| `tests/` | Reserved for tests. |

## Install

Clone the repo and link it into your Claude skills folder.

macOS / Linux:

```sh
git clone https://github.com/netanelyan/hebrew-voice.git
ln -s "$(pwd)/hebrew-voice" ~/.claude/skills/hebrew-voice
```

Windows (PowerShell, no admin needed):

```powershell
git clone https://github.com/netanelyan/hebrew-voice.git
New-Item -ItemType Junction -Path "$env:USERPROFILE\.claude\skills\hebrew-voice" -Target "$PWD\hebrew-voice"
```

## Use

- Ask for any Hebrew copy and Claude loads the skill on its own.
- Or call it directly: `/hebrew-voice כתוב פוסט קצר על הפיצ'ר החדש`
- To edit existing text, paste it and ask Claude to run it through hebrew-voice.

To use the voice outside Claude Code, put `voice.md` into the system prompt.

## Make it yours

There's no fixed persona. The voice is one human talking, whoever the text speaks for. To push it closer to yours:

1. Add your own writing to `samples/` and share it when you ask for copy. Samples take priority over the general rules.
2. Tell Claude who the text speaks for (you, your business) and it'll use only what you give it.
3. Add your own banned patterns to section 5 of `voice.md` as you find them.
