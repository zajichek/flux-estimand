# Flux Estimand

## tl;dr

A **ModelBundle** is the implementation of an **estimand**—a model built to answer a particular question—not the implementation of an entire domain.

---

## Motivation

Simulation projects often begin with a broad objective:

> "Simulate hockey."

or

> "Simulate heart failure."

Without a clearly defined scientific target, model scope naturally expands as additional mechanisms, entities, and interactions are added to increase realism.

The **Flux Estimand** framework proposes a different workflow.

Rather than beginning with the system being modeled, begin with the question being answered.

The estimand defines the target quantity before implementation begins, allowing every modeling decision to be evaluated relative to that objective.

---

## Core Idea

The unit of modeling is **the question**, not the domain.

An estimand defines:

- the decision being informed
- the research question
- the counterfactual scenarios
- the target outcome
- the required model scope
- the validation targets
- the conditions under which the model is considered sufficient

A Flux `ModelBundle` is then one possible implementation of that estimand.

Multiple ModelBundles may implement the same estimand while differing in assumptions, complexity, or computational approach.

This repository proposes an estimand-first methodology for designing Flux models. Although the ideas may be applicable to other simulation frameworks, they are presented here in the context of Flux.

---

## Repository Structure

A project repository represents an **estimand project**, not a `flux` project.

```text
estimand-project/
│
├── README.md            # Project overview
├── ESTIMAND.md          # Estimand specification
├── docs/                # Supporting documentation
└── bundles/             # Flux ModelBundle implementations
```

The root `ESTIMAND.md` defines the estimand for the project, including the target question, intended outcome, assumptions, validation targets, and model sufficiency criteria.

Each subdirectory within `bundles/` contains a Flux `ModelBundle` implementing that estimand. Multiple bundles may exist for the same estimand, differing in assumptions, complexity, or modeling approach.

---

## Workflow

The recommended workflow is:

```text
Decision
    ↓
Research Question
    ↓
Estimand
    ↓
Model Sufficiency
    ↓
Flux ModelBundle
    ↓
Simulation
    ↓
Estimate
    ↓
Decision
```

---

## Repository Contents

| Document | Purpose |
|----------|---------|
| `ESTIMAND.md` | Defines the estimand specification for a project |
| `docs/motivation.md` | Why an estimand-first workflow is useful |
| `docs/potential-outcomes.md` | Relationship to causal estimands and counterfactual reasoning |
| `docs/modelbundle.md` | Interpreting ModelBundles as estimand implementations |
| `docs/model-sufficiency.md` | Defining "good enough" models |
| `docs/workflow.md` | Recommended development workflow |
| `templates/` | Starting points for new estimand projects |

---

## Status

This repository explores an independent methodology for designing Flux models around explicit scientific questions.

The ideas presented here are experimental and intended to encourage discussion around structured simulation model development.

**Build the simplest model capable of answering the question—not the most realistic model imaginable.**