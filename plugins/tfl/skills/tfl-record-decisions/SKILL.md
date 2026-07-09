---
name: tfl-record-decisions
description: Keep about/decisions.md current with what's worth remembering across runs — corrected facts, the recipient choice, voice or offer preferences, and anything the member decided against. Reads the existing file first and updates it in place with targeted edits (not a blind append, not a rewrite from scratch). Run after any TFL workflow, or whenever the member says "remember that" or "don't suggest that again."
risk: low
---

# tfl-record-decisions

## Summary

`about/decisions.md` is the member's standing record of what they have already decided — a corrected fact, who they picked as the recipient, a voice preference, an offer tweak, something they turned down. Every TFL skill and workflow reads it back before it runs, the same way it reads the other `about/` files, so the member never has to repeat themselves. This skill keeps that record accurate and current after each run.

## Problem Solved

Without a kept record, every run starts from zero: the member corrects the same fact twice, re-explains a voice preference a third time, or watches a skill re-suggest something they already said no to. Each is small, but together they make a member stop trusting the tool to remember them. A record that only ever grows is just as bad — once a decision changes, the old line still sits there, and the next run cannot tell which version is current. The fix is to keep one accurate, up-to-date entry per decision.

## When to Use

- After any TFL workflow, once the member has confirmed or rejected things during the run.
- Whenever the member says "remember that," "note that for next time," or "don't suggest that again."

## When NOT to Use

- Mid-run, before the member has actually confirmed or rejected something. Record what happened, not what might happen.
- For facts about the *company* — those belong in the company profile (`outputs/company-profiles/[company].md`), not this file. This file is about the member's own standing preferences and corrections, not one prospect's details.

## Inputs

- `about/decisions.md` if it exists. Read it first, every time — this skill never writes blind.
- Whatever happened in the run worth remembering: a fact the member corrected, the recipient they picked or overrode, a voice or offer preference they stated, or something they explicitly rejected.

## Outputs

One file, `about/decisions.md`, kept current with **targeted edits** — not rewritten from scratch, and not a blind append. Each decision is a short, dated, self-contained entry:

```
## Recipient — updated 2026-07-08
Prefers the VP of Sales over the founder as the value-add recipient: the VP owns the number, so the snapshot reaches the person who acts on it.

## Voice — updated 2026-07-08
Drop "leverage" in any form, even when the banned-word check misses a variant.

## Northwind Robotics — RevOps role — updated 2026-07-08
The RevOps Manager role closed the week of 2026-07-08; do not cite it as open.
```

When a later run changes a decision, **edit that entry in place and bump its date** — do not leave the old version behind as a second, contradicting line. Add a new entry only for something genuinely new.

## Process

1. **Read the existing file.** Open `about/decisions.md`. If it does not exist yet, create it with a one-line header saying what it is — the member's standing decisions, read by every TFL skill.
2. **Gather what is worth keeping from this run.** Any fact the member corrected, the recipient they confirmed or overrode, a voice or style note, an offer tweak, and anything they explicitly said no to.
3. **Match each item against what is already recorded.** A new topic → add an entry. The same topic with a changed decision → update that entry in place and bump its date. The same topic, unchanged → leave it alone.
4. **Make targeted edits only.** Change the entries this run affects; do not rewrite untouched entries and do not restate the whole file.
5. **Write each entry to stand on its own.** A brand-new Claude chat with no other context must be able to read the entry and apply the decision correctly — so include the *why* whenever the decision is not obvious without it. Keep entries short, but accuracy comes first.
6. **Confirm.** Tell the member what you recorded or changed, in one line, so they can correct it if you got it wrong.

## Rules

- **Update in place, do not just append.** When a decision changes, edit the existing entry and re-date it; do not stack a contradicting line on top. Add a new entry only for something new.
- **Never rewrite from scratch.** Make targeted edits to the entries this run touches and leave the rest alone.
- **Date every entry.** Stamp each entry with the date it was last changed, so it is clear how current a decision is.
- **Self-contained and accurate.** Each entry must carry enough context for a fresh Claude chat to convey the decision correctly. Keep it short, but never trade accuracy for brevity.
- **Member preferences only, not company facts.** Company-specific facts stay in that company's profile; this file is the member's own standing decisions and corrections.
- **Keep it readable.** This file is read back at the start of every TFL skill — keep it tight enough to be read in full each time.

## Quality Checklist

- [ ] Read `about/decisions.md` before writing anything.
- [ ] Changed decisions were edited in place and re-dated — not appended as a second, contradicting line.
- [ ] Only the entries this run affects were touched; the rest of the file is unchanged.
- [ ] Each entry is dated and self-contained — a no-context Claude chat could apply it correctly.
- [ ] The member was told what got recorded or changed, in one line.
