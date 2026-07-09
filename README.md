# Flux Estimand Framework

## tl;dr

A `ModelBundle` is one implementation of an estimand: a model built to estimate the causal consequences of a particular decision, not the implementation of an entire domain.

Flux Estimand provides a structured methodology for building decision-oriented Flux simulations under stated assumptions.

---

## Motivation

Simulation projects often begin with a broad goal:

> "Simulate hockey."

or

> "Simulate heart failure."

That framing can make model scope unbounded. Every omitted mechanism, entity, and interaction can be argued to make the simulation more realistic.

Flux Estimand starts from a different question:

> What decision are we evaluating, and what counterfactual worlds need to be compared?

The framework is intended for decision-oriented Flux projects where the goal is to estimate the causal consequences of alternative decisions, actions, or policies. It is not a requirement for every possible Flux simulation.

Flux remains the simulation engine. Flux Estimand is a layer above Flux that structures the scientific and decision question before a `ModelBundle` implementation is built.

---

## Core Idea

Build the simulation around the decision whose consequences are being estimated.

```text
Decision
    ↓
Conditioning State
    ↓
Counterfactual Actions / Policies
    ↓
Outcomes / Target Quantities
    ↓
Model Sufficiency
    ↓
ModelBundle
    ↓
Simulation
    ↓
Estimate
    ↓
Decision
```

An estimand defines the decision problem, the counterfactual actions or policies to compare, the target quantities to estimate, and the assumptions under which those quantities are meaningful.

The conditioning state defines the point at which counterfactual worlds diverge. History before that state is treated as observed and shared; the alternative worlds differ only in the decision, action, or policy being evaluated.

A Flux `ModelBundle` is one executable implementation of the estimand. Multiple `ModelBundle` implementations may target the same estimand while differing in assumptions, fidelity, parameterization, or computational strategy.

---

## What an Estimand Defines

A decision-oriented Flux estimand should specify:

- decision context
- research question
- target population / conditioning state
- counterfactual actions or policies
- outcomes / target quantities
- contrasts
- time horizon
- required state representation
- required processes
- model sufficiency
- validation targets
- actionability / decision rules
- out of scope
- assumptions
- open questions

---

## Repository Structure

An estimand project is organized around a decision-oriented estimand, with one or more Flux `ModelBundle` implementations beneath it.

```text
estimand-project/
├── README.md
├── ESTIMAND.md
├── docs/
└── bundles/
    ├── init/
    └── alternative_bundle/
```

The root `ESTIMAND.md` defines the decision-oriented estimand: the decision context, conditioning state, counterfactual actions or policies, target quantities, assumptions, validation targets, and sufficiency criteria.

The `bundles/` directory contains one or more Flux `ModelBundle` implementations of that estimand. The recommended first bundle is `bundles/init/`, the minimal working implementation capable of estimating the target quantities with explicit assumptions.

---

## Repository Contents

| Document | Purpose |
|----------|---------|
| `ESTIMAND.md` | Template for a decision-oriented estimand specification |
| `docs/motivation.md` | Why Flux Estimand starts from decisions rather than domains |
| `docs/potential-outcomes.md` | How counterfactual reasoning motivates the framework |
| `docs/model-bundle.md` | Interpreting ModelBundles as estimand implementations |
| `docs/model-sufficiency.md` | Defining sufficiency relative to the target decision estimand |
| `docs/workflow.md` | Practical workflow for decision-oriented Flux Estimand projects |
| `docs/future-directions.md` | Exploratory ideas for tooling, endpoints, policy spaces, and execution |
| `templates/` | Starting points for new estimand projects |

---

## Agent Guidance

This repository includes optional guidance for AI/coding agents in [`AGENTS.md`](AGENTS.md) and task-specific skills in [`skills/`](skills/). These files help agents scaffold, review, and design Flux Estimand projects while preserving the methodology-first workflow.

---

## Status

Flux Estimand is experimental methodology for decision-oriented Flux modeling. Tooling may emerge later, but the current focus is a clear specification layer for building simulations around causal comparisons under stated assumptions.

**Build the simplest ModelBundle implementation capable of estimating the consequences of the decision.**
