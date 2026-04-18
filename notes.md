# Notes

## Building a C compiler with a team of parallel Claudes
**Author:** Nicholas Carlini (Anthropic)
**Date:** February 5, 2026
**URL:** https://www.anthropic.com/engineering/building-c-compiler

~16 parallel Claude Code agents collaboratively built a Rust-based C compiler capable of compiling the Linux kernel — ~2,000 sessions over two weeks at ~$20,000 in API costs. Agents coordinated via a simple git-based locking system using text files to claim tasks and avoid duplicating work. The result was a ~100,000-line compiler supporting x86, ARM, and RISC-V that successfully compiles Linux 6.9, QEMU, and FFmpeg.

Key design lessons for multi-agent systems:
- High-quality tests are critical for autonomous orientation
- Context pollution must be minimized
- Feedback loops should be tight
- Tasks should be decomposed into independent parallel subtasks

---

## Scaling Long-Running Autonomous Coding
**Author:** Wilson Lin (Cursor)
**Date:** January 14, 2026
**URL:** https://cursor.com/blog/scaling-agents

Cursor's research into running hundreds of concurrent coding agents over extended periods. Flat agent structures with shared file locks failed — agents held locks too long or forgot to release them. The winning architecture separates agents into distinct roles: **planners** (explore codebases, recursively create tasks) and **workers** (execute assigned tasks), with a **judge** agent deciding whether to iterate further.

Real-world results: a browser built from scratch at 1M+ lines of code, a large-scale Solid-to-React migration, and a 25× performance improvement via a Rust rewrite.

Key takeaways:
- Model choice matters significantly for long-horizon work
- Prompting quality outweighs architectural complexity
- Simplifying, not adding complexity, was the primary driver of improvement

---

## Harness Engineering: Leveraging Codex in an Agent-First World
**Author:** OpenAI Engineering
**Date:** February 11, 2026
**URL:** https://openai.com/index/harness-engineering/

OpenAI describes "harness engineering" as a methodology where engineers shift from writing code to designing environments, specifying intent, and building feedback loops that enable Codex agents to do reliable work. In a five-month internal experiment, a small team shipped ~1 million lines of production code with no manually written source — interacting with Codex entirely through prompts that resulted in agent-opened PRs.

Key principles:
- **Strict architectural layering** (Types → Config → Repo → Service → Runtime → UI) enforced via structural tests, keeping agents within well-defined dependency boundaries
- **Context lives in the repo** — versioned local artifacts (code, markdown, schemas, executable plans) rather than long instruction manuals, so agents reason directly from source
- **Continuous background tasks** — Codex scans for deviations, updates quality grades, and opens targeted refactoring PRs; automated garbage collection for the codebase

---

## Welcome to Gas Town
**Author:** Steve Yegge
**Date:** January 1, 2026
**URL:** https://steve-yegge.medium.com/welcome-to-gas-town-4f25ee16dd04

An orchestration system for managing 20-30 Claude Code instances simultaneously, built on the MEOW stack (Beads, Epics, Molecules, Protomolecules, Formulas). Uses tmux-based interfaces and a Git-backed data plane to run persistent, crash-resilient workflows across specialized worker roles — enabling one developer to coordinate AI agents at scale.

---

## Ship Production Software in Minutes, Not Months — Eno Reyes (Factory)
**URL:** https://www.youtube.com/watch?v=iheWKg2Tkrk

Talk by Eno Reyes of Factory on dramatically accelerating software delivery — moving applications into production in minutes rather than months through agentic development methodologies and tooling.

---

## NotebookLM — AI Software Factory Reference
**URL:** https://notebooklm.google.com/notebook/cce75b57-6ff8-45dd-9421-9288627a4984

NotebookLM notebook collecting references and research related to the AI Software Factory / SDLC Factories project.

---

## Everything is a Ralph Loop
**Author:** Geoffrey Huntley
**Date:** January 17, 2026
**URL:** https://ghuntley.com/loop/

Argues that software development has fundamentally shifted from manual construction to loop-based automation powered by LLMs. Engineers should now focus on programming autonomous agents that iterate continuously toward goals rather than writing code themselves. The future role of a software engineer is to architect and oversee self-improving systems.

---

## The Five Levels: From Spicy Autocomplete to the Dark Factory
**Author:** Dan Shapiro
**Date:** January 23, 2026
**URL:** https://www.danshapiro.com/blog/2026/01/the-five-levels-from-spicy-autocomplete-to-the-software-factory/

Maps five levels of AI-assisted software development, paralleling NHTSA's driving automation framework. Most developers plateau at Level 3 (code review management), while elite teams reach Level 5 — a "Dark Factory" where specs automatically transform into functioning software with minimal human intervention.

---

## Software Factories and the Agentic Moment
**Author:** Justin McCarthy (StrongDM)
**Date:** February 6, 2026
**URL:** https://factory.strongdm.ai/

StrongDM's approach to building a Software Factory where AI agents autonomously write, test, and refine code from specs with no human intervention. Introduces "non-interactive development" enabled by improved LLMs and a **Digital Twin Universe** — behavioral replicas of third-party services used for testing at scale.

---

## The 5 Levels of AI Coding (Why Most of You Won't Make It Past Level 2)
**URL:** https://www.youtube.com/watch?v=bDcgHzCBgmQ

Video covering the five levels of AI coding proficiency and why most developers stall before reaching the most capable tiers of AI-assisted development.

---

## Wilson Lin on FastRender: A Browser Built by Thousands of Parallel Agents
**Author:** Simon Willison
**Date:** January 23, 2026
**URL:** https://simonwillison.net/2026/Jan/23/fastrender/

FastRender is an experimental web browser built by Cursor using coordinated agent swarms — up to 2,000 concurrent agents making thousands of commits per hour, producing ~30,000 total commits and over 1M lines of Rust in weeks. Planning agents decompose work into non-overlapping streams for worker agents, demonstrating how a single engineer plus an AI swarm can tackle extraordinarily ambitious projects.

---

## Effective Harnesses for Long-Running Agents
**Author:** Justin Young (Anthropic)
**Date:** November 26, 2025
**URL:** https://www.anthropic.com/engineering/effective-harnesses-for-long-running-agents

Addresses how agents can maintain progress across multiple context windows without losing state. The solution uses an **initializer agent** to set up scaffolding (feature list, progress tracking) and subsequent **coding agents** that work incrementally on single features, keeping code clean and testable — drawing from human software engineering practices to avoid common failure modes.

---

## Harness Design for Long-Running Application Development
**Author:** Prithvi Rajasekaran (Anthropic Labs)
**Date:** March 24, 2026
**URL:** https://www.anthropic.com/engineering/harness-design-long-running-apps

Explores multi-agent architectures inspired by GANs — separating generation from evaluation to create feedback loops that drive higher quality outputs than single-agent approaches. Key innovations include structured grading criteria for subjective work and **sprint contracts** between agents to bridge high-level specs and testable implementations, resulting in dramatically more capable applications despite higher compute cost.

---
