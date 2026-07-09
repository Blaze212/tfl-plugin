---
name: tfl-setup
description: First-run setup. Creates the-fractional-life/ in the folder the member's in, builds the scaffold inside it, interviews them, and fills their about files. Use when a member says "set me up," "get me started," when about/ is missing, or when any about file still says "needs input." Also handles updates like "redo my ICP" or "update my offer."
risk: low
---

# tfl-setup

## Summary

Get a member from "just added the connector" to "profile filled, first company named" in about 10 minutes, without a blank page or a technical step. This member already has a fractional offer and is actively prospecting, so this is capture, not creation.

## Problem Solved

Every other skill in this repo depends on the member's profile: their function, ICP, sprint length, wins, and voice. Left to fill templates alone, members stall at the blank page or abandon anything that looks technical. This skill captures the profile in one short conversation so the rest of the chain never runs on empty files.

## When to Use

- "Set me up," "get me started," first run in an empty folder.
- Any skill finds `about/` missing or a file still saying "needs input."
- "Update my offer," "redo my ICP," "change my voice notes" (rerun just that part).

## When NOT to Use

- The files exist and are filled. Don't re-interview; ask what changed and update only that.
- The member doesn't have a fractional offer yet. This skill captures an existing offer, it doesn't create one.
- The member names a company to pursue and their profile is already complete. Go straight to the prospecting skills.

## Inputs

- A short conversation. One question at a time, never a form.
- `templates/about-templates/` and `templates/start-here-template.md` from this repo.

## Outputs

- The folder scaffold at `the-fractional-life/`: `about/`, `templates/`, `outputs/company-lists/`, `outputs/company-profiles/`, `outputs/value-adds/`, `outputs/messages/`.
- All templates installed word-for-word into `templates/` (keeping `about-templates/` intact), so the value-add skill can read `templates/value-add-template.md`.
- Filled about files in `about/`, with "needs input" marking any blank the member couldn't fill.
- `START-HERE.md` in their folder, personalized with their name.

## Process

1. **Create `the-fractional-life/`** in the folder you're in, then build the scaffold inside it if it doesn't exist:
   `about/`, `templates/`, `outputs/company-lists/`, `outputs/company-profiles/`, `outputs/value-adds/`, `outputs/messages/`. Install all templates word-for-word into `templates/` (keeping the `about-templates/` folder intact). Then copy the about templates into `about/` as their starting files. Say one line about what you made, no tech talk.
2. **Interview, one question at a time.** Tell them they can paste from an existing offer doc instead of retyping. The questions:
   1. What's your fractional function, and in one sentence, what do you fix? (function + one-liner)
   2. How long does a first engagement usually run for you? (sprint length, expect 3-6 weeks)
   3. Who's your ideal client? Size, stage, industry, geography. And what signals tell you a company is a fit?
   4. Your name and LinkedIn URL.
   5. At least 3 career wins, each with a real number. (More is good: the value-add uses the 3 that fit each company best.)
   6. Anything about how you write? Formality, phrases you use, anything you'd never say. (Fine to skip; house rules cover them.)
   7. Do you have AI Ark connected yet? (It's a 3rd party MCP server that lives outside the TFL plugin) (If not: point them to where to get it, note "not yet" in the offer file, and reassure them everything still works, they'll just confirm more org facts by hand.)
3. **Fill the about files** from their answers. If they don't have a number for a win, write "needs input" in that slot. Never invent one.
4. **Write START-HERE.md** into their folder from the template, personalized with their name.
5. **Read their profile back** in 3-4 lines: function, ICP, sprint length. Ask "anything to fix?"
6. **The handoff:** "You're set. Want to see it work? Give me a company you'd love to land." If they name one, kick off the tfl-build-value-add workflow.

## Rules

- One question at a time. A wall of 7 questions is a form, and forms get abandoned.
- Never invent a number, a win, or an ICP detail. Marked blanks beat guesses.
- Nothing technical on screen: no file paths in conversation unless they ask, no JSON, no jargon. "I saved your profile" beats "I wrote about/tfl-about-me.md."
- If they've clearly done this before (files exist and are filled), don't re-interview. Ask what changed.

## Quality Checklist

- [ ] Every about file is filled or has a clearly marked "needs input."
- [ ] Sprint length captured (the value-add skill needs it).
- [ ] AI Ark status recorded.
- [ ] All templates are installed word-for-word in `templates/` (esp. `value-add-template.md`, which the value-add skill reads).
- [ ] START-HERE.md exists with their name in it.
- [ ] You ended by asking for a company they'd love to land.
