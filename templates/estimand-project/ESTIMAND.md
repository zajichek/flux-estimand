---
estimand_id: <ESTIMAND_ID>
title: <ESTIMAND TITLE>
description: >
  <ONE- OR TWO-SENTENCE DESCRIPTION>
version: 0.1.0
status: draft
---

# <ESTIMAND TITLE>

This estimand is the authoritative decision specification for this project.

It defines the target question before implementation begins: the decision being evaluated, the conditioning state, the counterfactual actions or policies, the outcomes, the contrasts, the target quantities, and the assumptions under which those quantities are meaningful.

Flux `ModelBundle` implementations are executable realizations of this estimand. Implementation details belong in bundle documentation, not in this estimand specification.

## 1. Decision Context

<Describe the real-world decision being made. Who makes it, when, and why?>

## 2. Research Question

<State the decision-oriented causal question clearly.>

<If multiple target quantities are needed, explain how they jointly inform one coherent decision problem.>

## 3. Target Population

<Define the systems, entities, cases, or situations to which the estimand applies.>

### Conditioning State

<Describe the information available at the moment the decision is made.>

<The conditioning state should define the point at which the counterfactual worlds begin to differ. History before this point is shared between the alternatives.>

## 4. Counterfactual Actions / Policies

<Define the alternative actions or policies being compared.>

<Distinguish immediate actions from future decision policies where relevant.>

## 5. Outcomes

<Define one or more outcomes that collectively inform the decision.>

### Primary

<Define the primary outcome precisely.>

### Secondary

<Optional additional decision-relevant outcomes.>

## 6. Contrast

<Define the comparison between counterfactual outcomes.>

<Specify whether the contrast is a difference, ratio, ranking, curve, policy comparison, or another quantity.>

## 7. Time Horizon

<Define when follow-up begins and ends.>

<For decision-point estimands, the horizon will often begin immediately after the decision and end when the outcome is assessed.>

## 8. Required State Representation

<Describe the minimum information any ModelBundle must be able to represent.>

The estimand specifies what information must be recoverable, not how that information is organized into Flux entities, schemas, or abstractions.

## 9. Required Processes

<Describe the processes by which the required state must be able to evolve.>

<Specify mechanisms conceptually rather than requiring implementation-specific event types or algorithms.>

## 10. Model Sufficiency

<Define what makes a ModelBundle sufficiently detailed to estimate the target quantities credibly.>

<Explain what minimum state and processes are required and what additional realism would need justification.>

## 11. Validation Targets

<Define observable quantities or behaviors against which ModelBundle implementations should be assessed.>

<Validation targets are evidence supporting model credibility; they are not the estimand outcomes themselves.>

## 12. Actionability / Decision Rules

<Describe how the estimated quantities could inform decisions or be synthesized into decision rules.>

<Distinguish evidence produced by the estimand from the final policy or decision rule that consumes that evidence.>

## 13. Out of Scope

<Explicitly list questions, outcomes, mechanisms, or decisions that this estimand is not intended to answer.>

## 14. Assumptions

<List assumptions required for interpreting the counterfactual comparisons.>

<Keep estimand-level assumptions separate from bundle-specific modeling assumptions and execution assumptions.>

## 15. Open Questions

<List unresolved scientific, modeling, or decision questions that may motivate future ModelBundle implementations.>
