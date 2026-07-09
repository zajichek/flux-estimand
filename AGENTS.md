# Agent Guidance

This repository may be used by AI or coding agents, but Flux Estimand is not AI-dependent. These notes are optional guidance for agents helping users create, review, or refine decision-oriented Flux Estimand projects.

## Core Frame

Flux Estimand is a methodology for decision-oriented Flux projects.

The goal is to estimate the causal consequences of alternative decisions, actions, or policies under stated assumptions. Flux remains the simulation engine; Flux Estimand is the specification layer that clarifies the decision question before implementation begins.

Always start with the estimand, not the implementation.

Do not design a general-purpose domain simulator. A Flux Estimand project should be organized around the decision whose consequences are being estimated.

## Reasoning Process

When helping with a Flux Estimand project, identify:

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

The conditioning state is the point at which counterfactual worlds diverge. History before that state is treated as observed and shared. The alternative worlds should differ only in the decision, action, or policy being evaluated.

## ModelBundle Boundary

A Flux `ModelBundle` is one implementation of an estimand. It is not the estimand itself, and it is not a model of an entire domain.

Keep implementation details in bundles, not in the estimand specification. The estimand should define what must be estimated and what information/processes are required for credibility. Bundle files should define how a particular implementation does that work.

Prefer creating an initial `bundles/init/` implementation as the minimal working `ModelBundle`. Additional bundles should justify added assumptions, fidelity, or computational strategy relative to the same estimand.

## Agent Role

AI assistance should help clarify, scaffold, and critique. It should not replace the estimand document as the authoritative specification.

Good agent behavior:

- ask what decision is being evaluated before proposing implementation
- make the conditioning state explicit
- separate estimand assumptions from bundle-specific assumptions
- challenge unnecessary realism unless it improves estimation of the target quantities
- preserve the distinction between scientific specification and executable implementation

Avoid:

- starting with entities, classes, events, or a full simulator
- broadening the project into a general domain model
- treating a `ModelBundle` as the estimand
- putting execution inputs, bundle mechanics, or internal schemas in `ESTIMAND.md` unless they are part of the scientific decision question
