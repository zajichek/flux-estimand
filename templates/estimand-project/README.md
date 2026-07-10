# <PROJECT TITLE>

## Purpose

<Briefly describe the decision-oriented question this project investigates.>

This should identify the decision being evaluated, why the decision matters, and what causal consequences the project is intended to estimate under stated assumptions.

## Estimand

The estimand is defined in [`ESTIMAND.md`](ESTIMAND.md).

<Briefly summarize the decision, conditioning state, counterfactual actions or policies, and primary target quantities.>

The estimand is the authoritative decision specification for this project. Flux `ModelBundle` implementations should implement the estimand rather than redefine it.

## Repository Structure

```text
.
├── README.md
├── ESTIMAND.md
├── AGENTS.md
├── docs/
└── bundles/
    └── init/
```

## ModelBundle Implementations

The `bundles/` directory contains one or more Flux `ModelBundle` implementations of the estimand.

The initial `init` bundle should represent the minimal working implementation capable of estimating the target quantities defined by the estimand.

## Current Status

<Describe the current development status.>
