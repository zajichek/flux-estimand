# Flux Estimand Framework

## tl;dr

A `ModelBundle` is one implementation of an estimand: a model built to estimate the causal consequences of a particular decision, not the implementation of an entire domain.

Flux Estimand provides a structured methodology for building decision-oriented Flux simulations under stated assumptions.

This repository is the Flux Estimand framework repository. It contains methodology, conceptual documentation, reusable agent skills, and a project template. It is not itself an estimand project and does not contain its own root-level `ESTIMAND.md`.

---

## Motivation

Simulation projects often begin with a broad goal:

> "Simulate the system."

That framing can make model scope unbounded. Every omitted mechanism, entity, and interaction can be argued to make the simulation more realistic.

Flux Estimand starts from a different question:

> What decision are we evaluating, and what counterfactual worlds need to be compared?

The framework is intended for decision-oriented Flux projects where the goal is to estimate the causal consequences of alternative decisions, actions, or policies. It is not a requirement for every possible Flux simulation.

Flux remains the simulation engine. Flux Estimand is a layer above Flux that structures the scientific and decision question before a `ModelBundle` implementation is built.

---

## Framework vs Project

This repository provides the reusable framework:

```text
flux-estimand/
├── README.md
├── docs/
├── skills/
└── templates/
```

A downstream Flux Estimand project contains the completed decision specification and implementations:

```text
downstream-estimand-project/
├── README.md
├── ESTIMAND.md
├── AGENTS.md
├── docs/
└── bundles/
    └── init/
```

Every downstream Flux Estimand project contains a root-level `ESTIMAND.md` that serves as its authoritative decision specification. The framework repository describes that artifact and provides a reusable template, but does not contain its own estimand.

The `AGENTS.md` provided under the project template is intended to be copied and customized within downstream estimand projects. It is not guidance for maintaining the Flux Estimand framework repository itself.

Start a new project from [`templates/estimand-project/`](templates/estimand-project/). The generic estimand template lives at [`templates/estimand-project/ESTIMAND.md`](templates/estimand-project/ESTIMAND.md).

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

## Repository Contents

| Path | Purpose |
|------|---------|
| [`docs/motivation.md`](docs/motivation.md) | Why Flux Estimand starts from decisions rather than domains |
| [`docs/potential-outcomes.md`](docs/potential-outcomes.md) | How counterfactual reasoning motivates the framework |
| [`docs/modelbundle.md`](docs/modelbundle.md) | Interpreting ModelBundles as estimand implementations |
| [`docs/model-sufficiency.md`](docs/model-sufficiency.md) | Defining sufficiency relative to the target decision estimand |
| [`docs/workflow.md`](docs/workflow.md) | Practical workflow for decision-oriented Flux Estimand projects |
| [`docs/future-directions.md`](docs/future-directions.md) | Exploratory ideas for tooling, endpoints, policy spaces, and execution |
| [`skills/`](skills/) | Reusable guidance for agents creating, reviewing, and designing Flux Estimand projects |
| [`templates/estimand-project/`](templates/estimand-project/) | Copyable scaffold for a downstream Flux Estimand project |

---

## Agent Guidance

Reusable task guidance lives in [`skills/`](skills/). These files are optional support for AI/coding agents and are not required to use Flux Estimand.

Project-level agent guidance belongs inside downstream estimand projects. The template version is [`templates/estimand-project/AGENTS.md`](templates/estimand-project/AGENTS.md).

---

## Status

Flux Estimand is experimental methodology for decision-oriented Flux modeling. Tooling may emerge later, but the current focus is a clear specification layer for building simulations around causal comparisons under stated assumptions.

**Build the simplest ModelBundle implementation capable of estimating the consequences of the decision.**
