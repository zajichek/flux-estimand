# Motivation

Simulation projects naturally encourage realism.

If a project begins with "simulate hockey," "simulate heart failure," or "simulate an emergency department," there is no obvious stopping point. More mechanisms, entities, interactions, and edge cases can always be added.

Flux Estimand narrows the starting point:

> What decision are we evaluating?

The goal is not to simulate an entire domain. The goal is to construct a decision-oriented Flux `ModelBundle` capable of estimating the causal consequences of alternative actions or policies under stated assumptions.

## Decisions Before Domains

A domain-first workflow asks:

> What does the system contain?

A Flux Estimand workflow asks:

> What counterfactual worlds must be compared to inform this decision?

That shift changes the role of the simulation. The simulation is no longer judged mainly by how much of the real system it includes. It is judged by whether its state, processes, and assumptions are sufficient to estimate the target quantities defined by the estimand.

## Conditioning State

The conditioning state is the point at which counterfactual worlds begin to differ.

History before the conditioning state is treated as observed and shared across scenarios. The alternative worlds differ only in the decision, action, or policy being evaluated.

For example, a goalie-pull estimand might condition on:

```text
Third period
6:00 remaining
Trailing by one goal
Specific teams
Observed game context
```

From that shared state, the simulation compares alternative goalie-pull policies. This focuses the estimate on the consequences of the decision itself rather than on unrelated stochastic events that occurred earlier.

## Scope Control

Flux Estimand does help control scope, but scope control is not the main goal. The main goal is to make the causal comparison explicit.

Every proposed increase in complexity should be evaluated against one question:

> Does this improve estimation of the target quantities for this decision?

If not, the added realism may be unnecessary for the estimand, even if it would make the simulation feel more complete.
