# Truman World

> **Can an AI become different because of what it has lived through?**

Truman World is an experimental research and engineering platform for studying **developmental artificial agents**—or, more cautiously, artificial individuals whose behavior may be shaped by a continuous personal history.

The project does not assume that an agent is conscious, autonomous, or already an open-ended individual. It asks a narrower, testable question:

> **Same Initial Mind + Different Life → Different Mind?**

This is an experimental hypothesis and a design target, not an established conclusion.

The goal is not to tell an agent who it is, but to study whether who it becomes can depend on what it has experienced. **The unit of study is not a task. It is a lifetime.**

## What We Are Building

Most agent systems are evaluated as sequences of isolated tasks. Truman World instead provides a persistent, instrumented environment in which an agent can act, observe consequences, remember episodes, update predictions, and carry internal state across days.

The system is intended to be:

- **observable**: decisions, predictions, confidence, state, memory retrieval, and learning events can be inspected;
- **reproducible**: worlds, initial conditions, model versions, seeds, and life histories can be replayed;
- **causally testable**: memory, state, experience, and learning components can be altered in controlled interventions;
- **developmental**: change is measured across a life history, not inferred from a single prompt.

The research target is whether long-term experience can produce stable differences in behavior, goals, internal representations, and fast intuition—even when two agents begin from the same configuration.

## Why This Is Different From Plan–Execute Agents

A conventional plan–execute agent receives a task, reasons, uses tools, and returns an answer. Its identity may effectively reset at the next task, with memory added as retrieval around an otherwise unchanged reasoner.

Truman World treats continuity as part of the agent:

- outcomes can change its world model and future expectations;
- repeated, validated choices can become faster behavioral tendencies;
- episodic memory forms a queryable life history;
- persistent latent state can carry information beyond a text summary;
- identical initial systems can experience different causal histories and later be compared under matched conditions.

The experiment is not simply whether a model can produce a good plan. It is whether a closed learning loop can develop differently because it encountered a different life.

## The V2 Dual-System Architecture

V2 is the current architectural direction. It places fast learned behavior, deliberate reasoning, a trainable world model, memory, and persistent state inside one causal loop.

```text
                         Observation
                              │
                              ▼
                ┌─────────────────────────┐
                │ Persistent Latent State │
                └─────────────┬───────────┘
                              ▼
                ┌─────────────────────────┐
                │ System 0                │
                │ Viability / Reflex /    │
                │ Safety                  │
                └─────────────┬───────────┘
                              ▼
                ┌─────────────────────────┐
                │ System 1: Laya          │
                │ Intuition / habits /    │
                │ action probabilities    │
                └─────────────┬───────────┘
                              │
             familiar and confident enough?
                     ┌────────┴────────┐
                    yes                no / surprise
                     │                  │
                     │                  ▼
                     │    ┌─────────────────────────┐
                     │    │ System 2: Qwen          │
                     │    │ Hypothesis / goal /     │
                     │    │ plan / reflection       │
                     │    └─────────────┬───────────┘
                     └──────────┬───────┘
                                ▼
                              Action
                                │
                                ▼
                              World
                                │
                                ▼
                    Outcome / Prediction Error
                                │
             ┌──────────────────┼──────────────────┐
             ▼                  ▼                  ▼
       World Model       Episodic Memory    Experience Replay
                                                  / Sleep
                                              Consolidation
                                                  │
                                                  ▼
                                            Laya Learning
```

### System 0 — viability, reflex, and safety

System 0 handles the lowest-level constraints and reflexes needed to keep an experiment within defined operational boundaries. It is intentionally limited and inspectable, not a personality layer or source of high-level goals.

### System 1 — Laya

Laya is the fast path: learned intuition, habits, familiar responses, and probability distributions over frequent actions. It should handle situations that have become predictable without invoking expensive deliberation at every step.

### System 2 — Qwen

Qwen is the deliberative path. It is invoked selectively for unfamiliar situations, low confidence, high prediction error, conflicting goals, hypothesis generation, planning, or reflection. It proposes interpretations and strategies; it is not an unquestionable teacher.

### World Model

The world model continually learns to predict future observations and outcomes from state, context, and action. Prediction error is both an evaluation signal and a possible trigger for deeper reasoning.

### Persistent Latent State

Persistent latent state carries continuous internal context across steps and days. Its contribution must be measured rather than assumed, including through probes, resets, swaps, and ablations.

### Episodic Memory

Episodic memory stores the agent's life history: what happened, what was attempted, what was expected, and what outcome followed. Retrieval should be traceable so memory-dependent behavior can be audited.

### Experience Replay and Sleep Consolidation

During replay or scheduled consolidation, experiences with real outcomes can update the world model and, where justified, Laya. The purpose is to let validated deliberation gradually become faster intuition while preserving the evidence chain behind the update.

Qwen is not “the whole person.” Laya is not “the whole person.” The experimental subject is the persistent closed-loop system: models, state, memories, learning processes, actions, and world feedback together.

## How Learning Happens

The proposed learning loop is:

```text
Experience → Surprise → Qwen Deliberation → Action → World Feedback
           → Laya Learning → Future Intuition
```

This is deliberately not simple “Qwen distillation into Laya.” Qwen may generate a plausible explanation, goal, or strategy and still be wrong. The world outcome—not the language model's confidence—is the final feedback. Only experience linked to observed consequences should become training evidence, with provenance, uncertainty, and failures preserved.

Over time, a successful deliberate response may require less explicit reasoning. A failed response should update expectations rather than become a habit merely because it was eloquently proposed.

## Truman World as a Developmental Environment

Truman World is intended to provide controlled lives rather than disconnected tasks. A run consists of a persistent environment, an agent configuration, a sequence of experiences, and a complete intervention-ready trace.

The environment should support:

- long-running free interaction and scripted experimental conditions;
- matched worlds with controlled differences in life events;
- versioned world dynamics and scenarios;
- checkpoints for models, memories, latent state, and environment state;
- counterfactual replay from shared checkpoints;
- behavioral, representational, and learning-process measurements.

This makes the world a laboratory for developmental questions while keeping the mechanisms available for ordinary engineering inspection.

## Core Experiments

### 1. Deliberation → Intuition

Introduce a novel problem that initially requires System 2. After repeated outcome-validated experience and consolidation, test whether System 1 responds faster and with fewer deliberative calls while retaining or improving performance.

### 2. Free-Life Run

Let an agent live for an extended period without prescribing every task. Track behavior, prediction, recurring goals, memory use, action entropy, and representations—without assuming that any change constitutes agency or identity.

### 3. Same Mind, Different Life

Fork identical initial agents into controlled but different life histories. Later place them in matched evaluation worlds and test for reproducible differences.

```text
Same Initial Mind + Different Life → Different Mind?
```

The question mark matters. The experiment must accommodate null results and alternative explanations.

### 4. Memory Removal and Ablation

Remove, reset, mask, or swap episodic memory, persistent latent state, System 1 learning, System 2 access, or world-model updates. Measure which observed differences survive and which components were causal.

### 5. Latent Probe

Probe persistent and model-internal representations for information about history, expectations, goals, and future behavior. Probes are diagnostic evidence, not automatic proof that a human-like concept exists inside the system.

## V0 → V1 → V2 Roadmap

### V0 — Explicit Plastic State Machine

V0 explores the basic experimental shape using explicit, interpretable state and plasticity rules. Its value is causal clarity: researchers can see why a state changed and develop tracing, checkpointing, and intervention infrastructure.

### V1 — De-semanticized Predictor

V1 moves from hand-labelled internal concepts toward a predictor trained on observation, action, and outcome. The aim is to reduce semantic assumptions and ask what structure can be learned from interaction. V0 and V1 remain historical baselines rather than being erased by V2.

### V2 — Dual-System Causal Loop

V2 is the planned integration of Laya, Qwen, a trainable world model, persistent latent state, episodic memory, and outcome-grounded consolidation. It is designed to test whether deliberate reasoning can become learned intuition and whether different histories create measurable, causal, persistent differences.

## Current Status and Historical Baselines

This repository currently documents the research direction and version lineage. The public repository does not yet contain enough implementation material to claim a reproducible V2 result or provide verified installation and run commands.

As code and artifacts are added, results should be linked to versioned configurations, seeds, traces, checkpoints, and evaluation procedures. V0/V1 evidence should remain available as historical baselines; measured V2 results should be clearly separated from proposed experiments.

## What This Project Does Not Claim

Truman World does **not** currently claim:

- that consciousness has been implemented or detected;
- that the system has open-ended subjectivity or human-like personhood;
- that persistent state or memory alone creates an individual;
- that all high-level concepts, goals, or values will emerge naturally;
- that model probes provide direct access to subjective experience;
- that a Qwen-generated explanation is correct without world-grounded evidence;
- that developmental differences necessarily imply consciousness.

These are boundaries that keep the project empirically useful. The work focuses on measurable developmental change, causal mechanisms, and reproducible interventions.

## Long-Term Research Direction

The long-term direction is a general runtime for agents that can alternate between reflex, intuition, and deliberation; learn predictions from ongoing experience; preserve a continuous but inspectable history; and be studied across an entire developmental trajectory.

Questions include:

- When should deliberation be invoked, and when has a skill become intuitive?
- Which experiences produce durable changes rather than short-term context effects?
- Can learned goals remain stable, revisable, and traceable to their histories?
- How much behavioral difference comes from memory, latent state, model updates, or environment feedback?
- Can initially identical systems develop reproducibly different strategies without researchers pre-labelling the difference?
- Which null results reveal that an apparent “individual difference” was only prompt sensitivity or noise?

The preferred outcome is not a dramatic claim. It is a body of careful experiments that makes these questions easier to test.

## Getting Started

Verified public installation and launch instructions will be added alongside the corresponding implementation. Until then, this README intentionally does not invent commands, dependencies, checkpoints, or performance results.

When runnable releases are published, each getting-started path should identify:

1. the exact V0, V1, or V2 configuration;
2. required local model checkpoints and execution backend;
3. reproducible seeds and scenario versions;
4. trace, checkpoint, and evaluation output locations;
5. the boundary between implemented components and planned research.

## Research Principles

- Prefer causal interventions over anthropomorphic interpretation.
- Preserve failures, null results, and historical baselines.
- Distinguish proposed architecture from implemented and measured behavior.
- Ground learning in world outcomes, not the authority of a language model.
- Make long-running experiments recoverable, inspectable, and reproducible.
- Treat “mind,” “intuition,” and “individual” as operational research terms whose measurements must be stated.

---

**Can an AI become different because of what it has lived through?** Truman World is an attempt to turn that question into a careful experimental program.
