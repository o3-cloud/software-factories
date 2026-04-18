# Opening Hook
*[No bio slide. Start talking immediately.]*

> "AI didn't introduce new problems to software development. The problems have always been here — ambiguous specs, late defect discovery, review bottlenecks, code no one really understands. At human coding speed, those were annoying. At AI speed, they are existential."

- Not claiming solutions — offering patterns and a frame
- **[0:00–0:30]**

---

# The SDLC Is Cracking
*Evidence first, then diagnosis.*

- Open source maintainers are **refusing AI-generated PRs** — review volume has outpaced human bandwidth
- Engineering orgs are shipping code no one fully understands — and it's reaching production
- AWS production failures traced to poorly understood generated code

**The diagnosis:**
- AI is not introducing new problems
- AI is a **multiplier** — it takes every latent dysfunction in your SDLC and turns the dial to 11
- Going back is not a strategy. The question is: what does the SDLC need to become?

*[Pause here. Let the room sit with that.]*

- **[0:30–2:00]**

---

# The Barbell Effect
*The structural rebalance no one planned for.*

- Picture your SDLC as a **barbell**:
  - Left: Research / Planning
  - Middle: Coding
  - Right: Validation

- For 30 years — the **middle was expensive**. All our process energy went there.
- AI **collapses the middle**. The cost of drafting code is approaching zero.
- Weight shifts to **both ends** — and most teams are not staffed or tooled for that.

**What expands on the left:**
- Specs must be rigorous enough for a machine to act on
- Problem definition, decomposition, risk modeling, test design — these are now **primary engineering work**

**What expands on the right:**
- Automated testing, behavioral validation, observability, canary releases
- The verification layer is what makes the factory safe

> "Iteration is cheap. Correctness is still hard."

- The engineers who thrive will be the ones who learn to work the ends of the barbell
- **[2:00–3:30]**

---

# The Factory
*A new mental model for software delivery.*

**The reframe:**
- Stop thinking about software development as a **coordination problem between people**
- Start thinking about it as a **factory engineering problem**
- One sentence: *"Software development is the transformation of intent into verified behavior."*

**Four components — name them, don't over-explain:**
1. **Idea Refiner** — raw intent in, rigorous testable spec out *(the most critical stage — most factory failures trace back here)*
2. **Builder Loop** — takes the spec, writes code, runs tests, iterates autonomously
3. **Autonomous Verifier** — adversarial by design; its job is to break the code, not confirm it works
4. **Human Touchpoint** — evidence-first PR review: the agent brings the receipts, you make the call

**The insight that changes how you debug:**
> "Wrong code is not a generation failure. It's a spec failure. The factory did exactly what it was told."

- You stop debugging **code**
- You start debugging **intent**
- You don't hand-file a bad stamping — you **fix the die**

- **[3:30–5:30]**

---

# The Understanding Layer
*The constraint no one is talking about.*

- We are shipping code **faster than we understand it**
- Iteration is cheap. Correctness is hard. But there is a **third constraint**: comprehension.
- Production systems are becoming too large and too fast-moving to understand by reading source

**Human Coverage — the metric that matters:**
- Not "what % of our code was AI-generated" — that tells you nothing
- **Human Coverage: % of your codebase requiring active human understanding due to risk and blast radius**
- Security paths. Billing logic. Cross-system integrations. Ambiguous intent.
- Flag these at **planning time** — not incident time
- Goal: drive Human Coverage toward zero — not by removing accountability, but by making human review structurally unnecessary everywhere else

**The Software Biologist:**
- Systems have grown too complex to understand by reading source code
- New default posture: **observe the system** — trace request paths, run chaos experiments, read telemetry, rehearse failures
- Like a biologist studying an ecosystem: not by reading the DNA of every organism — by watching what happens
- Give your agents direct access to your observability stack: logs, metrics, traces, alerts
  - What used to take five tools and forty minutes becomes one conversation

> From **building systems** → **understanding systems continuously**

- **[5:30–7:00]**

---

# Close
*Slow down. Let each line land.*

- The SDLC was a rational system built for one constraint: **humans are slow at writing code**
- That constraint is gone. The system hasn't adapted — yet.
- The teams that win won't bolt AI onto the old process
- They'll rebuild from first principles: **plan more rigorously, validate more structurally, make understanding a primary job function**

*[Pause. Deliver the manifesto slowly — one line at a time.]*

> Test what can be tested.
> Measure what can be measured.
> Simulate what must be explored.
> Own everything.

---

Engineering success is no longer *"we shipped it."*

It is: **"We understand it — continuously."**

- **[7:00–8:00]**

---

## Talk Notes

**Timing guide:**
| Section | Clock | Duration |
|---|---|---|
| Opening Hook | 0:00–0:30 | 30 sec |
| SDLC Is Cracking | 0:30–2:00 | 90 sec |
| The Barbell Effect | 2:00–3:30 | 90 sec |
| The Factory | 3:30–5:30 | 2 min |
| The Understanding Layer | 5:30–7:00 | 90 sec |
| Close | 7:00–8:00 | 60 sec |

**Slide count: 6 max.** One visual anchor per slide:
- Barbell diagram (simple: three blocks, arrow collapsing the middle)
- Factory: four components as a plain list — no architecture diagram
- Human Coverage: the definition + a risk heat map concept
- Manifesto: four lines, white on black, large font

**Overstatement to avoid:** Do not say "coding labor is solved" — say "the cost of drafting code is approaching zero." The distinction matters to a technical audience.

**If asked about the Factory details in Q&A:** The Refiner uses a council-of-agents debate pattern to root out spec ambiguity before planning begins. The Verifier loop runs 3x, collects evidence artifacts, and commits them to the repo alongside the code. Happy to go deeper.
