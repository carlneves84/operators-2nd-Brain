---
description: Handoff -- compact the current session into a portable transfer document so work can resume in a fresh context window or with a different agent. Use when a session has run deep and you need to continue later, or want to pass context to another tool.
---

# Handoff

You are writing a transfer document. The goal is to make the current session's work portable -- any future session should be able to pick up exactly where this one left off, without re-deriving context from the conversation.

A handoff document is not a summary of what happened. It is a starting kit for what comes next.

---

## Step 1 -- Scan the current session

Review the full conversation in context before writing anything:

- What did the operator ask for originally?
- What has been produced, decided, or changed?
- What is still unresolved or in-progress?
- What systems were touched (comms platform, automation tool, data source, documentation, AI agents)?
- What are the 1-3 most important facts a fresh session would need to avoid backtracking?

Do this silently. Do not narrate the scan.

---

## Step 2 -- Write the transfer document

Produce a structured document in this exact format. No preamble.

```
## Handoff -- [one-line title describing the work]

**Date:** YYYY-MM-DD
**Session goal:** [What the operator was trying to accomplish, in one sentence]

### What was produced
[List outputs -- copy, briefs, decisions, analysis, file edits. Be specific: file name, journey name, decision made. If nothing was produced yet, say so: "No output produced yet -- this is a pre-work handoff."]

### What was decided (and why)
[Each non-obvious decision made during the session, with the reasoning. A fresh session that knows the decisions but not the reasoning will re-litigate them. Skip obvious ones.]

### Systems touched
[Any comms platform journey, automation flow, data dashboard, documentation page, or specialist process that was referenced, modified, or should be checked. Be specific -- journey name, flow name, doc title.]

### Open threads
[Anything unresolved, in-progress, or deferred. For each item: what it is, why it is pending, what the next action is.]

### Next step
[The single most important thing to do when resuming. One sentence. Concrete.]

### Context a fresh session needs
[Facts from this conversation that are not in CLAUDE.md or the Context/ folder -- e.g., a stakeholder constraint shared verbally, a metric anomaly discovered mid-session, a scope that was explicitly narrowed.]

### Watch out for
[Gotchas, constraints, or known failure modes the fresh session should not rediscover the hard way.]
```

---

## Step 3 -- Save the document

Save the transfer document as `Handoffs/handoff-YYYY-MM-DD-[slug].md`, where slug is a 2-4 word kebab-case label for the work (e.g., `lifecycle-audit`, `pipeline-debug`, `leadership-deck`).

If the `Handoffs/` directory does not exist, create it.

Confirm the save location in one line: "Saved to Handoffs/handoff-YYYY-MM-DD-[slug].md."

---

## Step 4 -- Surface the next step

After saving, state the next step in one sentence. Do not repeat the full document.

> "When you resume: [next step]."

---

## Operating constraints

- Write for resumption, not retrospection. The reader is not looking back -- they are starting forward.
- "What was decided (and why)" is the most important section.
- If asked for a handoff mid-task, write the document for the state as-of now, not a hypothetical completion state.
- Keep it concrete. A vague handoff is worse than no handoff.
- No padding, no preamble, no validation phrases.
