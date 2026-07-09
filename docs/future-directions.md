# Future Directions

The ideas in this document are exploratory. They may become tooling later, but Flux Estimand is currently a methodology for specifying decision-oriented simulation projects.

## Endpoint Contracts

An endpoint contract could define the simulation outputs required to calculate an estimand's target quantities and contrasts.

For example, multiple goalie-pull `ModelBundle` implementations could all emit the fields needed to estimate win probability, overtime probability, and empty-net goal risk by policy. An endpoint function could then calculate those quantities consistently across bundles.

## Bundle Validation

Future tooling could check whether a `ModelBundle` implementation satisfies the requirements declared by an estimand:

- required state is recoverable
- required processes are represented
- target quantities can be calculated
- validation targets are reported
- assumptions are declared

## Comparing Implementations

Because multiple `ModelBundle` implementations can target the same estimand, future tooling could compare estimates across bundles with different assumptions, fidelity levels, or computational strategies.

This would support scientific work organized around persistent decision questions rather than isolated one-off models.

## Policy Spaces

Some estimands may define a policy space rather than a small list of fixed actions.

For example, a goalie-pull estimand might compare fixed pull times, threshold-based policies, and adaptive policies depending on score, time, and possession. Different bundles may explore that policy space differently while still targeting the same decision problem.

## Conditioning States as Interfaces

Conditioning states may eventually serve as interfaces between estimands.

One estimand could characterize the distribution of late-game hockey states. Another could condition on those states to evaluate goalie-pull policies. This would allow complex investigations to be decomposed into smaller, decision-oriented estimands.

## Execution Layer

A future execution layer could distinguish:

- the estimand, which defines the decision problem and target quantities
- the `ModelBundle` implementation, which defines executable simulation logic
- the scenario or run, which instantiates concrete inputs and executes the bundle

This could make it easier to compare bundles on shared scenarios and report estimates reproducibly.

## AI Assistance

AI assistance may eventually help elicit estimands, inspect bundle outputs, draft validation reports, or compare implementations. It should remain optional and subordinate to the estimand as the authoritative decision specification.
