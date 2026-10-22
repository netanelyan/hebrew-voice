# hebrew-voice

The Hebrew copywriting voice I use across Toran, Teder and Tiyul+: websites, pitch pages, posts, captions, DMs and AI agent replies.

## What's here

- `voice.md` is the source of truth. It covers who's talking, the everyday and serious registers, what to borrow from each brand, the rules, the banned patterns and the rewrite pass. It stands on its own, so it can be loaded as-is into the Toran and Teder system prompts.
- `SKILL.md` is the Claude Code skill wrapper. It tells the model to follow `voice.md` and run the rewrite pass before returning any Hebrew.
- `references/` has one file per source, with short examples (URL and date for each) and a breakdown of what to borrow and what to avoid:
  - everyday: Wolt, IKEA, mako, walla, @push.il
  - serious: Kan News, Kol Zchut, morning (Green Invoice)
- `samples/` is for my own writing. Empty for now.
- `tests/` is empty for now.

## Install as a Claude Code skill

Link the repo into the skills folder.

macOS / Linux:

```sh
ln -s "$(pwd)" ~/.claude/skills/hebrew-voice
```

Windows (no admin needed):

```powershell
New-Item -ItemType Junction -Path "$env:USERPROFILE\.claude\skills\hebrew-voice" -Target (Get-Location)
```

Then ask for any Hebrew copy, or call it directly with `/hebrew-voice`.

## Open TODOs

- Add my own samples to `samples/` and section 2 of `voice.md`.
- Paste real Wolt app push notifications into `references/wolt.md`.
- Add IKEA TV and print campaign lines to `references/ikea.md` if I want them.

## Note

The reference files quote short lines of copy from other brands and news sites for study. Keep this repo private.
