# Flux Estimand Template

A Flux Estimand defines the decision-oriented scientific contract for a Flux Estimand project.

It documents the decision being evaluated, the conditioning state where counterfactual worlds diverge, the alternative actions or policies to compare, the target quantities to estimate, and the assumptions under which those quantities are meaningful.

Flux Estimand is intended for decision-oriented Flux projects whose purpose is to estimate the causal consequences of alternative decisions under stated assumptions. It is not a requirement for every Flux simulation.

A Flux `ModelBundle` is one executable implementation of an estimand. If the implementation changes but the estimand remains unchanged, the decision question remains stable. If the estimand changes substantially, the project is likely addressing a different decision problem.

## Conditioning State

Whenever possible, define the estimand at the decision point.

The conditioning state is the point at which counterfactual worlds begin to differ. History before the conditioning state is treated as observed and shared across scenarios. The alternative worlds differ only in the decision, action, or policy being evaluated.

This helps isolate the consequences of the decision itself rather than mixing them with unrelated stochastic variation from earlier history.

## Template

Every decision-oriented Flux Estimand project should include an `ESTIMAND.md` file with the following sections.

## 1. Decision Context

What decision, action, or policy choice is this project intended to inform?

## 2. Research Question

What question must be answered to inform that decision?

## 3. Target Population / Conditioning State

Who or what does the estimand apply to?

What is the conditioning state where counterfactual worlds begin to diverge?

## 4. Counterfactual Actions or Policies

What actions, interventions, strategies, or policies are being compared?

## 5. Outcomes / Target Quantities

What quantities will be estimated from the counterfactual simulations?

## 6. Contrasts

How will target quantities be compared across actions or policies?

## 7. Time Horizon

Over what time period are outcomes measured?

## 8. Required State Representation

What information must be recoverable for the estimand to be meaningful?

The estimand specifies what information must be represented, not how a `ModelBundle` implementation stores or computes it.

## 9. Required Processes

What dynamic processes must be represented to estimate the target quantities credibly?

Focus on processes required by the decision comparison, not implementation-specific events.

## 10. Model Sufficiency

What state and process structure is enough to estimate the causal consequences of the decision with appropriate credibility under stated assumptions?

## 11. Validation Targets

Which empirical or decision-relevant quantities should the `ModelBundle` implementation reproduce or satisfy before estimates are considered credible?

## 12. Actionability / Decision Rules

How will the estimated quantities be used to inform a decision or recommendation?

## 13. Out of Scope

Which questions, mechanisms, populations, or decisions are intentionally excluded?

## 14. Assumptions

What assumptions make the counterfactual comparison meaningful?

## 15. Open Questions

What remains unresolved or requires further work?
