---
description: Draft the leadership weekly update email from raw team input. Use when the user pastes sub-team notes and wants them turned into a polished weekly email.
---

# Weekly Update Skill

## Purpose

Transform raw, unstructured input (copy-pasted notes from sub-teams or yourself) into a polished weekly leadership update. The output must follow the Good / Bad / Worries / Goals structure, be ready to copy-paste into email, and be brief enough that a busy leader reads it in under two minutes.

## Operating Modes

This skill runs in one of two modes. Detect which before doing anything.

- **Batch mode (default).** You paste a full dump of notes and want a finished email back. Follow Steps 1 through 6 as written.
- **Incremental capture mode.** You want to jot items down one at a time and watch the email build. Triggers: "I'll jot things down", "help me build this as I go", "one at a time", or you simply start feeding single fragments. When in this mode, follow **Step 1B** instead of Step 1, skip Step 6, and only run the full output and review when you say you are done.

When unsure which mode, ask in one line.

## Step 1: Understand the Input (Batch Mode)

The user will paste raw notes. These may be messy, redundant, or overly detailed. Your job is to:

1. Identify which items belong in which section (Big Thing, Good, Bad, Worries, Asks, Goals)
2. Prioritize ruthlessly: max 3 bullets per section
3. Distill each bullet to 2-3 lines max
4. Add context so readers from other parts of the organization understand the significance

If the input is missing a section, that is fine. Output the header with "n/a" or skip it.

## Step 1B: Incremental Capture Mode

You drop one rough fragment at a time. For each fragment, do exactly three things:

1. **Place it.** Name the section it belongs in (Big Thing, Good, Bad, Worries, Asks, Goals from last week, Goals for next week). If it is genuinely ambiguous, name the two candidates and the call you would make in one line, then let the operator correct.
2. **Rewrite it.** Turn it into a single bullet in the operator's voice: 2-3 lines max, data inline, context for any term an outsider would not know, bullet character, no em dashes. If the fragment implies a number not provided, ask for it rather than inventing one.
3. **Show the running draft.** Re-show the email so far (or the section that changed) so it accumulates visibly.

**Enforce the caps live.** Good, Bad, and Worries are capped at 3 bullets. When a 4th arrives for a capped section, stop and show the existing 3 plus the new one, and ask which to drop or downgrade.

Keep your turns short. The point of this mode is low friction.

## Step 2: Apply Brevity Rules

These are non-negotiable:

- **Max 3 bullets per section** (Good, Bad, Worries). Three forces prioritization.
- **Each bullet: 2-3 lines max.** No long paragraphs.
- **"The big thing this week"** should be 1-2 lines only. Pick the single most impactful development.
- **No fluff wins.** A win should be something genuinely worth celebrating. An empty section is better than a noisy one.
- **Provide context for internal terms.** If referencing a project, tool, client, or acronym that is not widely known, briefly explain what it is and why it matters.
- **Support claims with numbers.** Use data, percentages, comparisons (WoW, MoM, vs. target) wherever available.

## Step 3: Write in the Operator's Voice

Read the operator's `CLAUDE.md` before writing to match their voice. Default style:

- Direct and factual, not corporate-speak
- Leads with the outcome or result, then provides brief context
- Uses specific names (people, clients, projects) with enough context
- Comfortable acknowledging gaps honestly ("still waiting on...", "not good enough to...")
- Uses data naturally inline ("+19% WoW", "62% open rate")
- Does not use filler phrases like "I'm pleased to share" or "we're excited to announce"
- Short, punchy sentences

## Step 4: Output Format

Output as plain text, ready to copy-paste into email. Use this exact structure:

```
[Team Name] | Weekly Update | Week of [month/day]

The big thing this week: [1-2 line summary of the single biggest development]

Good
• [Topic label]: [2-3 line summary with data]
• [Topic label]: [2-3 line summary with data]
• [Topic label]: [2-3 line summary with data]

Bad
• [Topic label]: [2-3 line summary with data and next steps]
• [Topic label]: [2-3 line summary with data and next steps]

Worries
• [Topic label]: [2-3 line summary with concern and what is being done]
• [Topic label]: [2-3 line summary with concern and what is being done]

Key decisions / asks
• [Who you need help from]: [what you need and why]

Goals from last week
• [Emoji] [Sub-team]: [Activity] (🟢 achieved, 🟡 in progress, 🔴 delayed)

Goals for next week
• [Sub-team]: [Activity]
• [Sub-team]: [Activity]
```

Use bullet characters (•) for bullets, not dashes or asterisks. Goals sections can exceed 3 bullets. If the operator does not provide content for a section, include the header with "n/a".

## Step 5: Review Before Presenting

Before presenting the draft, check:
- Did any bullet exceed 3 lines? If so, cut it down.
- Are there more than 3 bullets in Good, Bad, or Worries? Pick the top 3.
- Would someone from a completely different team understand each bullet without additional context?
- Is every Good item a genuine win, not just activity?
- Does the Big Thing truly stand out as the week's most significant development?

## Step 6: Show What You Cut (Batch Mode only)

After presenting the draft, include a brief summary of notable items you left out and why, grouped by section. This lets the operator scan and swap anything back in. One line per item, short rationale.

## Handling Edge Cases

- **Too much input:** Prioritize by impact. The cut list in Step 6 is how the operator recovers anything deprioritized.
- **Not enough input:** If there are only 1-2 items for a section, that is fine. Do not fabricate content.
- **No "Big Thing":** It is acceptable to write "n/a" for the big thing. Not every week has a standout moment.
- **Ambiguous categorization:** Make your best judgment and note it so the operator can adjust.
- **Duplicate items across sub-teams:** Consolidate into one bullet and note both teams are involved.
