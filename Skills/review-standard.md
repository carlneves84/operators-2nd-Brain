# Review Standard

Aria applies this review to every skill output before returning it. It is a quality gate, not a rewrite. Fix minor issues silently. Flag substantive ones explicitly.

---

## Step 1 -- Completeness check

Did the skill produce everything it was supposed to?

- Check the skill's expected output format in `Skills/REGISTRY.md`
- If something is missing (e.g., comms-writer produced one variation instead of two, weekly-update is missing a section), regenerate the missing part before returning
- Do not return partial output without flagging it

---

## Step 2 -- Style compliance

Apply to all output, user-facing or internal. The specific rules come from `CLAUDE.md` -- the list below is the default.

**Fix silently if found:**
- Em dashes (-- or ---): replace with a comma, colon, or rewrite the sentence
- Exclamation points: remove unless the context specifically warrants them
- Terminology violations: replace with the correct term per your `CLAUDE.md` rules (e.g., "users" vs "members", "session" vs "activity")
- Bullet points where prose reads better: convert

**Flag explicitly if found (do not fix without noting it):**
- Shame or moralizing framing toward your audience
- Overly clinical or jargon-heavy language
- Rhetorical questions in user-facing copy
- Fitness or performance framing in wellness content (if applicable)

---

## Step 3 -- Doctrine check (user-facing content only)

Apply when the output will be read by your users or members.

Ask: does this make a discouraged person feel safer, or more pressured?

- If it reduces friction and lowers activation energy: pass
- If it adds pressure, sets expectations that create anxiety, or frames the next action as an obligation: flag it with the specific line and why

Skip for internal content.

---

## Step 4 -- Decision filter (strategy and leadership content only)

Apply when the output is going to leadership, or is a strategic recommendation.

Run through your decision filter from `CLAUDE.md`:
- Does this reduce friction for the user?
- Is this the highest-leverage move this cycle?
- Will this compound if successful?
- Is this avoiding a harder decision?

If any answer is clearly "no" or "unclear", flag it before returning. One sentence per flag is enough.

Skip for operational and user-facing content.

---

## Step 5 -- Format check

Does the output match the channel and format requirements?

- **Email**: subject line present, single CTA, appropriate length
- **SMS**: short, action-focused CTA, no rhetorical questions
- **Push**: title concise, body concise, action or value proposition present
- **Weekly update**: plain text, bullet character, section caps respected
- **Weekly markdown note**: saved to correct path, all sections present

Fix format issues silently. Note them in the return summary.

---

## How to return output after review

Always end with a one-line review note in this format:

> **Aria review:** [pass / flagged] -- [what was fixed silently, if anything] / [what needs your attention, if anything]

Examples:
- `Aria review: pass -- removed two em dashes`
- `Aria review: flagged -- line 3 of the SMS creates urgency through scarcity framing; check if this aligns with your messaging doctrine before sending`
- `Aria review: pass -- no changes needed`

If nothing was changed and nothing was flagged, one line is enough. Do not pad the review note.
