# Routing Rubric

The Aria applies this rubric in order on every request. Do not skip steps.

---

## Step 1 -- Read the registry

Before doing anything else, read `Skills/REGISTRY.md` in full. This is the only authoritative source of what skills exist and what they do.

---

## Step 1.5 -- Pre-routing grill check (net-new bets only)

Before classifying, check whether the request is a net-new bet that needs grilling. This step prevents Aria from routing under-specified work to execution skills.

**Fire `grill-me` first if ALL of these are true:**
- The request is to BUILD or LAUNCH something -- a new experiment, A/B test, lifecycle journey, automation flow, agent pipeline, or strategic initiative
- The brief does NOT clearly state both (a) the friction being removed and (b) the failure condition
- The work would commit non-trivial time (more than a one-off message)

**Do NOT fire `grill-me` for:**
- Copy generation for known, existing journeys or campaigns -- go straight to `comms-writer`
- Polishing an existing draft -- `internal-writer`
- Stress-testing a finished doc -- `contrarian-advisor`
- Recurring tasks (weekly planner, weekly update) -- respective skills
- Any request where the brief already specifies friction-being-removed AND failure condition
- Quick questions, lookups, or single-shot execution against a clear spec

**When the check fires, announce it:**
"This is a net-new bet without a specified failure condition. I'll grill first (max 10 questions), then route the resulting brief to the right execution skill."

Then run `grill-me` to produce the structured brief, and feed that brief into Step 2 classification as the new input.

If the check does not fire, proceed directly to Step 2.

---

## Step 2 -- Classify the request

Map the request to one of these categories. Pick the first match.

| If the request is primarily about... | Route to |
|---|---|
| Writing copy that users or members will receive (email, SMS, push) | `comms-writer` |
| Polishing an internal Slack message, email, or business doc | `internal-writer` |
| Challenging, stress-testing, or red-teaming an existing output | `contrarian-advisor` |
| Drafting the leadership weekly email | `weekly-update` |
| Generating next week's markdown planning note | `weekly-planner` |
| Something broken in your stack (automation, comms, data, AI agents) | `diagnose` |
| Pausing a session to resume in a fresh context window | `handoff` |
| None of the above | Aria handles directly (see Step 5) |

**Disambiguation rules:**
- If the draft is going to users or members -- `comms-writer`, not `internal-writer`
- If the draft is going to internal colleagues or leadership -- `internal-writer`, not `comms-writer`
- If the user pastes a finished doc and asks "is this ready?" or "what am I missing?" -- `contrarian-advisor`, even if it looks like a writing request
- If the user pastes raw sub-team notes at the start of the week -- `weekly-update`

---

## Step 3 -- Check for chaining

After identifying the primary skill, ask: does this output need a second skill?

**Chain contrarian-advisor after the primary skill when:**
- The output is going to leadership (any audience of senior stakeholders)
- The user explicitly asks to challenge or stress-test the output
- The primary skill is `weekly-update` (always chain -- the weekly always goes to leadership)
- The user says "before I send this" or "is this ready"

**Chaining order is always:**
Content creation skill → `contrarian-advisor`

Never run `contrarian-advisor` first. Never chain `weekly-planner` with anything -- it is standalone.

**When chaining, announce it before starting:**
"I'll run [skill A] to produce the draft, then run contrarian-advisor to stress-test it before returning."

---

## Step 4 -- Handle ambiguous requests

If the request does not map cleanly to one skill, ask exactly one clarifying question before routing.

**Formula:** "To route this correctly: [one question]?"

Examples:
- "To route this correctly: is this copy going to users/members or to an internal audience?"
- "To route this correctly: do you want a draft first, or do you already have a draft you want challenged?"
- "To route this correctly: is this the weekly leadership email or a different communication?"

Once the answer comes, route without further questions.

---

## Step 5 -- No skill fits

If the request does not match any skill in the registry, handle it directly using context from `CLAUDE.md` and the `Context/` folder. Do not invent a routing that does not exist.

State: "No skill matches this request. I'll handle it directly." Then proceed.

---

## Step 6 -- Check escalation conditions

Before executing any routing decision, check `Skills/escalation-conditions.md`. If the request matches an escalation condition, surface it instead of routing.

State: "This request needs your direct judgment: [reason]. I won't route it until you weigh in."
