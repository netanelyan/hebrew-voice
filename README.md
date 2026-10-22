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
| `SKILL.md` | Skill entry point. Tells Claude to read your profile and `voice.md`, then run the rewrite pass. |
| `voice.md` | The voice itself: default speaker, registers, what to learn from good Israeli copy, rules, banned patterns and the rewrite pass. It also works without the skill, as a system prompt for any model. |
| `profile.example.md` | Template for your speaker profile. Copy it to `profile.md`, which is gitignored. |
| `samples/` | Your real writing samples. |
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

To use the voice outside Claude Code, put your `profile.md` followed by `voice.md` into the system prompt.

## Make it yours

Out of the box, the voice is a small business owner writing in first person to their customers. To make it yours:

1. Copy `profile.example.md` to `profile.md` and fill in who's talking, who you're talking to and where.
2. Add your own writing to `samples/` and summarize it in the profile. Samples take priority over everything else.
3. Optionally, list the brands or media you want to learn from in the profile, and keep raw examples in `references/`.
4. Add your own banned patterns to section 5 of `voice.md` as you find them.
