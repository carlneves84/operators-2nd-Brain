# Skills Registry

The Chief of Staff reads this file first to route any request. Each entry defines what the skill does, when to use it, what input it needs, what it produces, and whether it can chain with another skill.

Customize this file when you add or remove skills, or when a skill's scope changes.

---

## comms-writer

**Command:** `/comms-writer`
**Purpose:** Write user or member-facing lifecycle copy (email, SMS, push notifications).

**Route here when the request involves:**
- Drafting or rewriting any communication sent to users, members, or customers
- Activation, engagement, or retention copy
- A/B test copy variations
- Any funnel stage: awareness, onboarding, first action, milestone, late retention
- Audience-specific copy variations

**Required input:** Channel (email / SMS / push), funnel stage or goal, audience segment if known. A rough brief or angle is enough.

**Output:** Two or more copy variations with a quality checklist applied. Ready to paste into your comms platform.

**Chains with:** `contrarian-advisor` -- if the copy is going to leadership for approval or is a high-stakes campaign, run contrarian-advisor after to stress-test the strategic framing.

---

## contrarian-advisor

**Command:** `/contrarian-advisor`
**Purpose:** Red-team and stress-test any finished output before it goes to leadership or ships.

**Route here when the request involves:**
- Phrases like "challenge this", "stress test", "red team this", "poke holes in this", "what will leadership push back on", "is this ready?", "what am I missing?"
- A strategy doc, experiment proposal, or weekly update shared for a high-stakes audience
- Any output where you are asking for a second opinion before committing

**Required input:** A finished or near-finished document, proposal, or message. The more complete the input, the sharper the objections.

**Output:** 3-5 ranked objections (most likely to land first), each with a counter-argument. One "biggest blind spot" line.

**Chains with:** Any skill -- contrarian-advisor is a post-processing step that can follow comms-writer, internal-writer, or weekly-update when the output is high-stakes.

---

## internal-writer

**Command:** `/internal-writer`
**Purpose:** Polish Slack messages, emails, and internal business docs using Amazon writing principles (short sentences, data over adjectives, no weasel words, active voice).

**Route here when the request involves:**
- "Polish this", "rewrite this", "make this cleaner", "sharpen this"
- A draft Slack message or email the user wants improved
- Internal comms going to colleagues or leadership (not user-facing -- use comms-writer for that)
- Removing corporate fog, hedging, or vague language

**Required input:** A draft message or email (can be rough). Channel (Slack or email) helps but the skill will infer it.

**Output:** Two versions -- Tight (minimum viable, every word earns its place) and Warm (same principles, human tone preserved). Plus a brief edit log.

**Chains with:** `contrarian-advisor` -- if the polished message is going to leadership or is a high-stakes ask, run contrarian-advisor after.

---

## weekly-update

**Command:** `/weekly-update`
**Purpose:** Draft the leadership weekly update email from raw sub-team notes.

**Route here when the request involves:**
- "Draft my weekly update", "write the weekly email", "weekly leadership email"
- You paste raw or messy notes from sub-teams and want them synthesized into the official format
- Synthesizing Good / Bad / Worries / Goals into a leadership-ready format

**Required input:** Raw notes from sub-teams (can be unstructured). The skill handles prioritization and formatting.

**Output:** Plain text email ready to copy-paste, following the Good / Bad / Worries / Goals structure. Includes a cut list of items deprioritized and why.

**Chains with:** `contrarian-advisor` -- always recommended to stress-test the weekly update before sending to leadership.

---

## grill-me

**Command:** `/grill-me`
**Purpose:** Interrogate you on a net-new bet (experiment, journey, agent pipeline, strategic decision) until the friction-being-removed, failure condition, and kill condition are all specified. Produces a structured brief that downstream skills run against.

**Route here when the request involves:**
- "Grill me on this", "stress-test before I build", "help me think this through", "I want to launch [new thing]"
- Net-new experiments, A/B tests, lifecycle journeys, automation flows, agent pipelines
- Strategic decisions (kill, pivot, scale) where the friction or failure condition is not specified
- Any request to BUILD something new where the brief does not include both (a) friction being removed and (b) failure condition

**Do not route here when:**
- The request is copy generation for a known journey -- use `comms-writer`
- The request is polishing an existing draft -- use `internal-writer`
- The request is stress-testing a finished doc -- use `contrarian-advisor`
- The request is recurring (weekly planner, weekly update) -- those are self-contained
- The brief already specifies friction-being-removed AND failure condition

**Required input:** A rough idea, brief, or "I want to build X" prompt.

**Output:** A structured brief: friction removed, audience, smallest shippable version, systems touched, success and failure signals, kill condition, what it compounds into, what it trades against. Hard cap of 10 questions.

**Chains with:** Any execution skill. After grilling, the brief feeds into `comms-writer`, `internal-writer`, or direct handling. Aria runs `grill-me` first when the pre-routing check fires.

---

## weekly-planner

**Command:** `/weekly-planner`
**Purpose:** Generate your structured weekly markdown note for the upcoming week. Pulls automatically from your documentation platform, meeting notes, and the current week's note.

**Route here when the request involves:**
- "Run my weekly planner", "generate my weekly note", "create next week's note", "it's Friday, let's do the weekly"
- Any variation of "prepare / generate / create my weekly"
- Best run on Fridays before end of day

**Required input:** None by default. The skill pulls its own sources (documentation platform, meeting notes, current week's markdown note). You must configure these sources in your `CLAUDE.md`.

**Output:** A saved `.md` file in `Weekly/`, decisions log updated, project stubs created for any new cross-references, stale watch list items flagged. Followed by a short summary.

**Chains with:** None. Standalone and self-contained.

---

## handoff

**Command:** `/handoff`
**Purpose:** Compact the current session into a portable transfer document so work can resume in a fresh context window or with a different agent.

**Route here when the request involves:**
- "I need to continue this later", "save where we are", "handoff this session", "create a transfer doc"
- A session that has run deep on a complex task and needs to pause
- You want to pass current context to a different tool, model, or session

**Required input:** None beyond the current session context.

**Output:** A structured `.md` file saved to `Handoffs/` covering: what was produced, what was decided and why, systems touched, open threads, next step, context a fresh session needs, and known gotchas.

**Chains with:** None. Handoff is always the last skill in a session.

---

## diagnose

**Command:** `/diagnose`
**Purpose:** Structured debugging for automation pipeline failures, journey bugs, engagement anomalies, and AI agent misbehavior. Follows reproduce → minimize → hypothesize → instrument → fix → regression-check.

**Route here when the request involves:**
- "Something is broken", "this flow isn't running", "users are getting the wrong message", "the metric dropped unexpectedly", "the agent is producing wrong output"
- Any failure or anomaly in your stack: automation, comms platform, data source, AI agents
- A specific behavior that does not match what was configured or expected

**Do not route here when:**
- The problem is strategic (what should we do?) rather than technical (why is this not working?) -- handle directly
- The request is a net-new build, not a fix -- that is `grill-me` territory

**Required input:** A description of observed vs. expected behavior.

**Output:** Step-by-step diagnosis: scoped symptom, minimized blast radius, ranked hypotheses, specific checks to run, targeted fix, and regression-check confirmation.

**Chains with:** None by default.

---

## Routing quick-reference

| If the request is about... | Route to |
|---|---|
| Net-new bet without specified friction + failure condition | `grill-me` first, then route the brief |
| Writing copy for users or members | `comms-writer` |
| Polishing an internal message or email | `internal-writer` |
| Stress-testing before leadership | `contrarian-advisor` |
| Drafting the weekly leadership email | `weekly-update` |
| Generating next week's markdown note | `weekly-planner` |
| Something broken in your stack | `diagnose` |
| Session needs to be paused and resumed later | `handoff` |
| High-stakes output from any skill | Chain with `contrarian-advisor` after |
| None of the above | Aria handles directly |
