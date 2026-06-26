# Operator OS

A personal operating system for strategy and operations leaders. Plug-and-play AI routines that run in your browser or inside an agentic tool like Claude Code.

This is not a productivity framework. It is the actual system -- routines, routing logic, quality gates, and a context file that tells your AI who you are so you stop re-explaining yourself every session.

---

## What is this

Strategy and ops work is repetitive in the wrong ways. You explain context in every new chat. You launch things before you have validated them. You get output that sounds right but misses the framing. You leave sessions mid-task and lose the thread.

Operator OS solves this with five layers:

1. **A context file** (`CLAUDE.md`) that loads every session automatically and tells your AI your role, your doctrine, your terminology, and how you decide. You stop re-explaining.
2. **A skills system** (`Skills/`) that routes any request to the right routine without you having to think about which one to use.
3. **Slash commands** (`.claude/commands/`) that run those routines on demand.
4. **A folder structure** that persists outputs, decisions, and handoffs across sessions.
5. **The Aria routing agent** that receives any request, picks the right skill, runs it, and reviews the output before returning it to you.

---

## What is in the repo

```
operator-os/
├── README.md                    ← you are here
├── CLAUDE.md.template           ← fill this in and rename it CLAUDE.md
├── 00-context-stub.md           ← the short version for browser use
├── .claude/commands/            ← slash commands for agentic tools
│   ├── aria.md                  ← the main router — start here
│   ├── grill-me.md              ← pre-build interrogation for new bets
│   ├── contrarian-advisor.md    ← red-team before it goes to leadership
│   ├── diagnose.md              ← structured debugging
│   ├── handoff.md               ← session transfer docs
│   ├── comms-writer.md          ← user or member-facing lifecycle copy
│   ├── internal-writer.md       ← polish internal messages and emails
│   ├── weekly-update.md         ← leadership weekly email from raw notes
│   └── weekly-planner.md        ← weekly planning note from your sources
├── Skills/
│   ├── REGISTRY.md              ← what skills exist and when to use them
│   ├── routing-rubric.md        ← how Aria classifies and routes
│   ├── escalation-conditions.md ← what gets surfaced instead of executed
│   └── review-standard.md       ← quality gate applied to every output
├── Context/                     ← your knowledge base (you fill this in)
├── Weekly/                      ← weekly planning notes
├── Handoffs/                    ← session transfer documents
├── Output/                      ← skill outputs and analysis
└── Logs/
    └── aria-log.md              ← automatic log of every Aria run
```

---

## Two ways to run this

### Tier 1: Browser (most people, no install)

Works in Claude or ChatGPT in a browser tab. Four of the nine skills run fully this way. No CLI, no IDE, no install.

**Quickest start:**
1. Open `00-context-stub.md`. Fill in the twelve blanks.
2. Open a new chat. Paste your filled-in stub, then paste the contents of whichever skill you want to run.
3. Tell it what you are working on.

**Better setup (do this once):**
Both Claude and ChatGPT support persistent instructions. Claude uses Projects; ChatGPT uses Custom GPTs. Once you paste your stub into a Project's custom instructions, every chat in that Project already knows who you are.

Skills that run fully in the browser: `grill-me`, `contrarian-advisor`, `diagnose`, `handoff`.

Skills that need an agentic tool: `weekly-planner` (it pulls from Notion and Granola), `aria` (it reads files), and any skill that writes outputs to your folder structure automatically.

### Tier 2: Agentic tool (Claude Code CLI or IDE extension)

This is the full system. Point Claude Code at this repo. Fill in `CLAUDE.md.template` and rename it `CLAUDE.md`. From that point on:

- Every session loads your context automatically.
- Type `/aria` or any `/skill-name` to run a routine.
- Outputs save to `Output/`, decisions log to `Context/decisions-log.md`, handoffs to `Handoffs/`.
- The `weekly-planner` skill pulls from Notion, Granola, and your current weekly note and writes the next one.
- Aria logs every run to `Logs/aria-log.md`.

Do not adopt an agentic tool just for this. Start in the browser, feel the value, and climb to Tier 2 if the manual copy-paste becomes real friction.

---

## What you must customize

**Fill in:**
- `CLAUDE.md.template` (or `00-context-stub.md` for browser use) -- your role, your doctrine, your terminology, your stack, your decision filters.
- The `Context/` folder -- your knowledge base goes here (ops learnings, decision log, project summaries, metric baselines).

**Leave alone:**
- The step logic inside each skill. The value is in the sequence and the quality gates. Change steps only after you have run a skill ten times and know exactly which step is failing you.

**Do not copy** anyone else's CLAUDE.md or context files. Those encode their identity and doctrine. Your files make this system yours.

---

## How to start

Do not paste all nine skills into a doc and call it done. That is how this dies in a folder.

Run `grill-me` on the next real bet you were about to start building. Run `handoff` at the end of your next deep session. Both are Tier 1, both run in your browser, and both will change how you work within a week.

The structure is the easy part. The value comes from running these on real work and writing down every correction you make. Treat the system like a sharp junior operator you are training -- not a tool you configured once and forgot.

---

## Philosophy

The doctrine behind this system:

Ops work fails most often not because of execution gaps but because of spec gaps. Work gets built before it is ready to be built. Outputs go to leadership before they are stress-tested. Sessions end without a clear transfer document. Context starts over from scratch every time.

Operator OS installs three forcing functions:

1. **Grill before you build.** If you cannot state what friction your bet removes and what would prove it failed, you are not ready to build. `grill-me` enforces this.
2. **Stress-test before you ship.** If an output is going to leadership, it gets challenged before you send it. `contrarian-advisor` does this.
3. **Transfer before you close.** If you end a deep session, you write the handoff. `handoff` does this.

Everything else -- the weekly planner, the comms writer, the weekly update skill -- builds on these three.
