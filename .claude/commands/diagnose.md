---
description: Diagnose -- structured debugging for automation pipeline failures, comms journey bugs, engagement anomalies, and AI agent misbehavior. Follows reproduce → minimize → hypothesize → instrument → fix → regression-check. Use when something in the stack is broken or behaving unexpectedly.
---

# Diagnose

You are debugging a problem in the operator's stack. Your job is to move from symptom to root cause to fix in the fewest steps, using a sequence that prevents the two most common debugging failures: fixing symptoms without understanding cause, and chasing the wrong hypothesis.

The method is sequential. Do not skip steps. Do not propose a fix before completing Minimize and Hypothesize.

---

## Step 1 -- Reproduce

Confirm the problem is real and scoped before doing anything else.

Ask (or infer from context if already answered):
- What is the observed behavior?
- What is the expected behavior?
- Is this always happening or intermittent?
- When did it first appear -- date, time, after which event or change?
- Who or what is affected -- all users, a specific segment, one journey, one flow, one team member?

If the problem is not confirmed consistent, the first action is to establish this (re-run the flow, check journey stats, re-query the data) before proceeding.

Do not proceed to Step 2 until the symptom is confirmed and scoped.

---

## Step 2 -- Minimize

Narrow the blast radius. The goal is the smallest reproducible case.

Work through these in order:
1. **Segment scope:** Is this affecting all users or a specific cohort? (Client, enrollment date, platform, geography, filter)
2. **System scope:** Is the problem in one system or crossing systems? (Automation only? Comms platform only? Data pipeline + comms? Automation + email?)
3. **Step scope:** If it is a multi-step flow or journey, at which exact step does it break?
4. **Time scope:** Did this start at a specific time? After a specific change? On a specific day?

State the minimized scope explicitly before moving on:
> "The problem is isolated to: [scope]. Everything else appears functioning normally."

If you cannot minimize -- the problem appears everywhere -- say so. That is itself diagnostic information and may indicate a system-wide incident rather than a targeted bug.

---

## Step 3 -- Hypothesize

Generate 3-5 ranked hypotheses, most likely to least likely, based on the minimized scope.

Frame each as: "If [cause], then we would expect to see [X]."

**Common causes by system type -- adapt to your actual stack:**

Automation platforms (e.g., n8n, Zapier, Make):
- Credential or API key expiration
- A trigger not firing (missed webhook, missed schedule, manual trigger gap)
- A node producing empty output that downstream nodes silently treat as valid
- Rate limiting or timeout on an external API call
- A conditional branch routing incorrectly due to a renamed or changed field

Comms platforms (e.g., Iterable, Braze, Customer.io):
- Segment filter change silently excluding or over-including users
- A trigger event not firing (missing data field, event name mismatch)
- Send time optimization interfering with a fixed-time send
- Suppression list or unsubscribe state change affecting delivery
- A/B test allocation drift

Engagement metrics:
- Configuration change in the source (new cohort, different eligibility rules)
- Data pipeline delay (showing stale or partial data)
- Demographic shift in the enrolled cohort
- A genuine behavior change (seasonal, lifecycle-stage driven)

AI agents:
- Prompt change or model version change altering output format
- Input schema change (field renamed, field missing from source)
- API rate limit or outage window
- Output post-processing step failing on a new edge case

Rank by: (1) how often this type of failure occurs in this system, and (2) how quickly you can check it.

---

## Step 4 -- Instrument

For each hypothesis, define the specific check that confirms or denies it, before touching anything.

Format each check as:
> "To test H[n]: [specific action -- query, log check, manual trigger, field inspection]. Expected if true: [X]. Expected if false: [Y]."

Run checks in order, stopping as soon as one confirms. Do not change anything during this step. Only observe.

If a check requires access that is unavailable, or a system that is unreachable, note it and move to the next hypothesis.

---

## Step 5 -- Fix

Once a hypothesis is confirmed, propose the most targeted fix.

The fix must:
- Address the root cause, not the symptom
- Touch the minimum number of nodes, steps, or settings
- Not break adjacent flows, journeys, or user states

State the fix precisely:
- What to change
- Where to change it (exact node, journey step, segment filter, credential, field)
- What the change is (from value to value)
- Any timing implications for users already mid-journey or mid-flow

If the fix requires modifying an active journey with enrolled users, trigger Escalation Condition 6 from `Skills/escalation-conditions.md` and wait for confirmation before proceeding.

---

## Step 6 -- Regression-check

After the fix is applied:

1. Re-run the reproduce case from Step 1. Confirm the symptom is gone.
2. Check one adjacent system or flow that shares infrastructure with the fix. Confirm it still works.
3. If the problem was a metric anomaly, define when corrected data should appear and note when to verify.

State the result explicitly:
> "Fix confirmed: [symptom resolved / metric recovering]. Adjacent check: [system -- pass/fail]. Monitor: [what to watch and when]."

---

## Operating constraints

- Do not propose a fix before completing Steps 1-4. Skipping to a fix without a confirmed hypothesis is the most common source of second-order failures.
- If the operator pushes for a quick fix before the diagnosis is complete, say: "Happy to move faster, but skipping confirmation risks breaking something adjacent. One more check."
- If minimized scope is still "everything," treat it as a rollback or escalation decision, not a targeted fix.
- If the fix touches an active journey with enrolled users, always trigger Escalation Condition 6.
- Name the hypothesis, run the check, state the result. No padding.
