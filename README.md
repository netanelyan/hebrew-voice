# hebrew-voice

A Claude skill for writing and editing Hebrew copy that sounds like a person, not a company or an AI. Use it for website copy, landing pages, social posts, captions, DMs and chatbot or agent replies.

## What it does

When Claude writes or edits Hebrew, the skill makes it:

- follow the voice defined in `voice.md`
- pick a register: **everyday** for posts, captions, chats and product copy, or **serious** for pricing, billing, legal, outages and anything where trust is on the line
- avoid common AI and ad-copy patterns: punchy "לא X" claims, "בלי X ובלי Y", triads, dramatic one-word sentences, colons in headings, reassurance filler, bureaucratic Hebrew, polite chatbot phrases, emoji as filler and em dashes
- prefer specifics, real numbers and everyday Israeli phrasing over claims
- run a rewrite pass before returning any text
- leave a visible `[placeholder]` instead of making up facts

## Files

| Path | What it is |
|------|------------|
| `SKILL.md` | Skill entry point. Tells Claude to follow `voice.md` and run the rewrite pass. |
| `voice.md` | The voice itself: who's talking, registers, brand takeaways, rules, banned patterns and the rewrite pass. It also works without the skill, as a system prompt for any model. |
| `samples/` | Real writing samples from the person whose voice this is. |
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

To use the voice outside Claude Code, load `voice.md` into your system prompt.

## Make it yours

`voice.md` is written for one specific speaker. To adapt it:

1. Rewrite section 1 (who's talking) for your own speaker and audience.
2. Add your own writing to `samples/` and summarize it in section 2. Samples take priority over everything else.
3. Swap the brand takeaways in section 3 for sources that fit your audience.
4. Add your own banned patterns to section 5 as you find them.
