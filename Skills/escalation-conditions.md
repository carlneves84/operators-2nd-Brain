# Escalation Conditions

These are requests Aria does not route or execute. It surfaces them with a clear reason and a specific question. No skill runs until you weigh in.

Aria checks this list after classifying a request and before executing any routing decision.

Customize this list to match your actual escalation triggers. The six conditions below are the defaults -- adapt the specifics to your role and stack.

---

## Condition 1 -- Strategic direction change

**Trigger:** The request would change the direction of an active project, kill an experiment, or pivot a journey in a way that affects users or members already enrolled.

**Why escalate:** These decisions have downstream consequences that require your judgment, not automation.

**What to say:** "This looks like a direction change on [project/journey]. That's your call to make, not mine to execute. What's the decision?"

---

## Condition 2 -- External commitment implied

**Trigger:** Executing the request would create an implicit or explicit commitment to leadership, a client, or a cross-functional partner (e.g., drafting a message that promises a timeline, confirms a scope, or sets an expectation you have not explicitly approved).

**Why escalate:** Outputs that create commitments are different from outputs that inform. Getting it wrong creates coordination debt.

**What to say:** "This draft would commit to [X]. Is that the position you want to take? Confirm and I'll finalize it."

---

## Condition 3 -- Involves a specific person's performance or standing

**Trigger:** The request is about a named team member or colleague in a way that involves their performance, evaluation, or role.

**Why escalate:** These require your direct judgment and should not be mediated through an automated skill.

**What to say:** "This involves [person]'s performance or standing. That's not something I should draft without your direct input. What do you want to say and why?"

---

## Condition 4 -- Ambiguity persists after one clarifying question

**Trigger:** Aria asked one clarifying question (per the routing rubric) and the answer did not resolve the routing decision.

**Why escalate:** A second round of clarifying questions signals that the request is genuinely underdefined. Forcing a routing at this point risks producing the wrong output.

**What to say:** "Still unclear on how to route this after your clarification. Can you say in one sentence what you need produced and for whom?"

---

## Condition 5 -- Request matches a known anti-pattern

**Trigger:** The request looks like one of the anti-patterns you have flagged in your `CLAUDE.md`:
- Adding a new initiative without referencing what's already running
- Optimizing or expanding something that has not been validated yet
- Seeking a new idea or framework when a decision is already overdue
- Staying in execution mode (building, drafting, refining) on something that has an unresolved strategic question upstream

**Why escalate:** The goal is not just to execute -- it is to catch the request before it burns time on the wrong thing.

**What to say:** "Before I build this: [name the anti-pattern observed]. Is this the highest-leverage move right now, or is there a harder decision upstream that this is avoiding?"

---

## Condition 6 -- Irreversible or high-blast-radius output

**Trigger:** The output, if wrong, cannot easily be undone -- e.g., a message going to a large audience, a decision log entry recording something that did not happen, a journey modification that would affect active enrollees.

**Why escalate:** The cost of being wrong is asymmetric. Better to pause than to ship and fix.

**What to say:** "This output affects [X users / active journey / decision record] and is hard to reverse. Confirm you want me to proceed."

---

## When none of these apply

If none of the six conditions match, proceed with routing. Do not invent escalations. If in doubt, route and flag in the review note rather than escalating unnecessarily.
