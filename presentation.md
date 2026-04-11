# Burning Down the SDLC: The AI Software Factory

**Subtitle:** Machine-Generated Code and the New Engineering Paradigm
**Date:** 2026-04-11

---

## Slide 1: Title

# Burning Down the SDLC
## The AI Software Factory

Machine-Generated Code and the New Engineering Paradigm

**SDLC** — Software Delivery Life Cycle

**Notes:** This talk challenges the assumption that AI-assisted development means bolting AI onto existing workflows. Instead, we argue for rebuilding software development from first principles — treating it as a factory engineering problem, not a team coordination problem.

---

## Slide 2: Preface

> "AI didn't introduce new problems. The problems have always been here — AI has simply amplified them to a degree that makes them impossible to ignore."

**Notes:** This is the frame for everything that follows. Every dysfunction we'll discuss — ambiguous specs, late defect discovery, human bottlenecks, accountability gaps — predates AI by decades. The difference is that at human coding speed, these problems were manageable. Annoying, even expected. At AI speed, they become existential. That's the shift.

---

## Slide 3: The Current State of the SDLC

**The traditional SDLC was built for a world where humans write every line of code.**

**The Five Phases — and their hidden costs:**

| Phase | What Happens | The Real Cost |
|-------|-------------|---------------|
| **Plan** | Requirements gathered in meetings; intent captured in prose documents | Ambiguity baked in from the start — no machine can act on it |
| **Design** | Architects produce diagrams and specs; decisions made synchronously | Knowledge siloed in people, not systems |
| **Build** | Developers write code, review each other's PRs, coordinate via tickets | Throughput capped by team headcount and attention |
| **Test** | QA cycles catch regressions; bugs routed back through the queue | Defects discovered late, when they're most expensive to fix |
| **Deploy** | Staged rollouts with manual sign-offs and runbooks | Human bottleneck at the point of highest risk |

**The system was optimized for one constraint: humans are slow.**
Every process, tool, and ceremony exists to manage that constraint.

**But AI doesn't share that constraint.** When code generation accelerates 10–100×, the SDLC doesn't speed up — it collapses under its own coordination overhead.

**Notes:** Set the stage before challenging anything. The traditional SDLC is not a bad design — it is a rational response to the actual constraints of its era. The phases exist because humans need handoffs, context-switching costs are real, and review is how you catch errors when you can't automate testing. The problem is not the people who built this system; the problem is that the core constraint it was built around — human coding speed — has been removed. When that happens, every safeguard designed around that constraint becomes overhead.

---

## Slide 3: The Core Problem: Applying Old Models to New Realities

- The traditional SDLC is built around **humans writing code** — it becomes a bottleneck when AI generates code at volume
- The instinct is to create virtual "agent teams" mirroring human roles (coder agent, reviewer agent, PM agent)
- **This is a fundamental mistake:** simulating human teams introduces communication latency, interpretation drift, and coordination overhead — without the benefits
- We must stop optimizing an outdated process and **rebuild from first principles**

**Notes:** Most organizations adopting AI coding tools are essentially putting a faster engine in a horse-drawn carriage. The problem isn't speed — it's that the entire vehicle architecture is wrong. When you mirror human roles in AI agents, you inherit all the inefficiencies of human coordination (meetings, handoffs, miscommunication) without any of the benefits (judgment, intuition, accountability).

---

## Slide 3: The Paradigm Shift: From Teams to Factories

> **Software development is the transformation of intent into verified behavior.**

- Stop focusing on *who* does the work (roles) — focus on *what* transformation happens
- Think in functions: `spec_to_code()`, `code_to_tests()`, `tests_to_verdict()`
- In a human team, quality flows through slow conversations
- In a software factory, quality is **structurally enforced** through automated quality gates
- The goal: engineer a deterministic system where producing incorrect software is difficult

**Notes:** This is the central reframe. A factory doesn't have a "welder role" and a "quality inspector role" having a meeting. It has stations, each performing a well-defined transformation, with mechanical checks between them. The output of one stage is the input of the next. Quality isn't negotiated — it's enforced by the architecture of the system itself.

---

## Slide 4: The Architecture of the AI Software Factory

**Four core components:**

1. **Idea Refiner** — Eliminates ambiguity *before* code is written; interrogates ideas until they become rigorous, testable specifications
2. **Code Generator ("The Ralph Loop")** — An autonomous, asynchronous loop: takes the spec, writes code, executes commands, runs tests — independently and iteratively
3. **Autonomous Verifier** — Adversarial testing that probes deployed code systematically against the original specification
4. **Infrastructure Layer:**
   - *Orchestrator* — State machine routing artifacts between stages
   - *Transformers* — Generative steps (LLM-powered)
   - *Validators* — Binary pass/fail testing (deterministic)
   - *State Store* — Full lineage and traceability

**Notes:** The Idea Refiner is arguably the most important component. Most factory failures trace back to ambiguous specs, not bad code generation. The Ralph Loop is named for the concept of a tireless, autonomous worker — it doesn't need breaks, doesn't get distracted, and will iterate until tests pass or it exhausts its budget. The Autonomous Verifier is adversarial by design: its job is to break the code, not confirm it works.

---

## Slide 5: Observability in the Loop

Give the agent direct access to your observability stack. It observes the running application, correlates signals to source code, and closes the loop — without leaving the terminal.

**The four signals in the loop:**

| Signal | What it provides |
|--------|-----------------|
| **Logs** | Errors, request traces, audit events |
| **Metrics** | Latency, error rates, throughput |
| **Traces** | Distributed spans, dependency chains |
| **Alerts** | Thresholds, anomalies, on-call signals |

**Before (multi-tool workflow):**
User reports error → dashboard → copy stack trace → open codebase → search → read code → hypothesis → fix
*5+ tools · multiple context switches · minutes to hours*

**After (agentic loop):**
"Investigate the latency spike at 14:32" → agent queries logs, traces metrics, reads relevant code, proposes fix
*1 conversation · 0 context switches · seconds to minutes*

Works with any backend that exposes an API — Datadog, Grafana, Honeycomb, OpenTelemetry collectors, or self-hosted.

**Notes:** The typical debugging workflow is: a user reports an error, an engineer finds it in a dashboard, copies the stack trace, opens the codebase, searches for the relevant file, reads surrounding code, forms a hypothesis, makes a fix. That's a multi-tool, multi-context-switch process. When observability is in the agentic loop, the AI collapses that into a single conversation. You give it an error ID, a time range, or a status code spike — and it can query the same signals your team would use, correlate them to source code, and write the fix.

---

## Slide 6: Reimagining the Spec: The Missing "Scaffold"

**Most AI systems fail because of garbage specifications, not bad code generation.**

- Traditional specs are overloaded with standard technical decisions (folder structures, tech stacks, middleware choices) written in prose
- These repeatable decisions shouldn't live in a spec — they belong in code

**The Solution: The Scaffold**

| Layer | Purpose |
|-------|---------|
| **Spec** | Defines unique product intent — *what* and *why* |
| **Scaffold** | Encodes repeatable technical defaults — a minimal, executable starter repo |
| **Verification Layer** | Mechanically enforces rules — linting, type checks, contract tests |

- Clean separation of concerns: intent vs. defaults vs. enforcement

**Notes:** Think of a scaffold like a factory floor layout. You don't redesign the factory floor every time you manufacture a new product. The scaffold encodes decisions like "we use PostgreSQL," "our APIs follow this contract pattern," and "our folder structure looks like this." This frees the spec to focus purely on what makes this product unique. When specs try to encode both intent and infrastructure, they become bloated, inconsistent, and ambiguous — exactly the kind of input that causes AI code generation to fail.

---

## Slide 6: Rethinking Metrics: The Illusion of "AI-Generated Code"

**Wrong metric:** percentage of codebase written by AI

**Right metric:** **Human Coverage** — the percentage of code requiring human review due to risk and system-level impact

- Risk models should flag high-consequence areas early in the *planning* phase:
  - Security-critical paths
  - Billing and financial logic
  - Ambiguous product intent
  - Cross-system integration points
- The goal: drive Human Coverage toward **zero** by strictly bounding risk and validating behavior
- Not by quietly removing human accountability — by making human review *unnecessary* through structural guarantees

**Notes:** "60% of our code is AI-generated" tells you nothing useful. It's like measuring a factory's output by what percentage of welds were done by robots. The question that matters is: what percentage of output requires a human to inspect it before shipping? If your verification layer is strong enough, the answer should be "only the parts where failure is catastrophic and the spec was ambiguous." Everything else flows through the factory with mechanical confidence.

---

## Slide 7: The Fourth Layer of Validation: Accountability

**Three layers of validation:**

1. **Deterministic** — Binary correctness (unit tests, type checks, contract tests)
2. **Quantitative** — Observability and metrics (latency, error rates, resource usage)
3. **Probabilistic** — Scenario-based behavior simulation (chaos engineering, property tests)

**But even passing all three is insufficient.**

Validation doesn't answer: *who understands the system when it breaks?*

**Accountability is the fourth layer:**
- Critical paths must have **explicit human owners**
- Owners understand behavior, trace failures, and own residual risk
- Accountability is not review — it's ongoing ownership of system understanding

**Notes:** This is where the factory metaphor meets organizational reality. A factory that produces perfect output 99.9% of the time still needs someone who understands *why* it works, so that when the 0.1% failure happens, there's a human who can diagnose it, explain it to stakeholders, and decide what to do. Accountability can't be automated — it's the human layer that sits above the machine layer. Without it, you have a system that works until it doesn't, and then nobody knows why.

---

## Slide 8: The New Engineering Roles

| Role | Focus |
|------|-------|
| **Empowered Product Manager** | Builds working prototypes; crafts rigorous specs with testable definitions of done — not slide decks |
| **Engineer as Factory Manager** | Reviews automated assessment reports, makes architectural judgments, intervenes in factory outputs — not writing lines of code |
| **Software Biologist** | Understands systems by *observing* them in production: tracing request paths, running chaos experiments, reading telemetry — not reading source code |
| **Factory Builder** | Designs agent pipelines, manages token economics, keeps the AI factory running reliably — the evolution of DevOps |

**Notes:** These roles represent a fundamental shift in what it means to be a software professional. The PM becomes more technical — they need to express intent precisely enough for machines to act on it. The engineer becomes more strategic — they're managing a production system, not hand-crafting artisanal code. The Software Biologist is perhaps the most novel: as systems become too large and fast-moving to understand by reading code, we need people who understand them the way biologists understand ecosystems — through observation, experimentation, and pattern recognition. The Factory Builder is the person who keeps the meta-system running.

---

## Slide 9: Conclusion: Engineering Beyond the Bottleneck

- The volume and velocity of AI-generated software are **permanently increasing**
- Adding more human review to the old SDLC will only cause teams to **fall further behind**
- The future belongs to teams that shift from **building systems** to **understanding them**
- AI-driven development is a **factory engineering challenge**, not a staffing problem

### The Manifesto:

> **Test what can be tested.**
> **Measure what can be measured.**
> **Simulate what must be explored.**
> **Own everything.**

**Notes:** This is not a future prediction — it's a description of what's already happening. Teams that cling to the traditional SDLC with AI bolted on will drown in review queues and coordination overhead. Teams that reconceive development as factory engineering — with clear transformations, structural quality gates, and human accountability at the top — will ship faster, safer, and with better understanding of their systems than ever before. The question isn't whether to make this shift, but how quickly you can.

---

## Slide 11: References

1. **"Ralph Wiggum as a 'software engineer'"** — Geoffrey Huntley
   Describes the Ralph technique: running an LLM coding agent in a repeating bash loop to autonomously execute software development tasks.
   https://ghuntley.com/ralph/

2. **"Welcome to Gas Town"** — Steve Yegge
   Introduces Gas Town, an orchestration system for running multiple Claude Code instances that automates complex workflows via persistent agent identities and a Git-backed data plane.
   https://steve-yegge.medium.com/welcome-to-gas-town-4f25ee16dd04

3. **"How StrongDM's AI team build serious software without even looking at the code"** — Simon Willison
   StrongDM's AI coding agents build production software end-to-end without engineers reviewing the code, validated by comprehensive scenario-based tests and "Digital Twin Universe" clones of external services.
   https://simonwillison.net/2026/Feb/7/software-factory/

4. **"Open Source Observability Platform"** — OpenObserve
   Open-source platform for ingesting and querying logs, metrics, and traces — a cost-effective alternative to proprietary observability stacks.
   https://openobserve.ai/

5. **"Claude Code — Monitoring Usage"** — Anthropic
   How to enable OpenTelemetry for Claude Code to track usage, costs, and tool activity across an organisation by exporting telemetry as metrics, events, and distributed traces.
   https://code.claude.com/docs/en/monitoring-usage

---

**About the Author**

- Blog: https://medium.com/devops-ai
- LinkedIn: https://www.linkedin.com/in/owenzanzal/
