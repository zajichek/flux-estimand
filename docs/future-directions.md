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

## Decision Estimands and Policy Estimands

Flux Estimands may eventually distinguish more explicitly between different levels of intervention.

A decision estimand evaluates the causal consequences of a specific action taken at a defined conditioning state. The counterfactual worlds share the same history up to that state and diverge only at the immediate decision.

```text
5:00 remaining
Team trailing by one
Goalie currently in net

Decision:
Pull goalie now
versus
Do not pull goalie now
```

This asks: what is the causal consequence of the action taken at this decision point?

A policy estimand evaluates the causal consequences of adopting a decision policy at an earlier point in time. The policy may govern one or more future decisions as the system evolves. A policy is itself a type of decision: the decision to adopt a rule governing future actions.

```text
10:00 remaining
Team trailing

Adopt policy:
Pull at 5:00 if still trailing
versus
Follow an alternative goalie-pull policy
```

This asks: what is the causal consequence of adopting this policy from the current state onward?

These are not the same intervention. Deciding at exactly 5:00 whether to pull the goalie now is localized to an immediate action from a conditioning state. Deciding at 10:00 to follow a policy that may pull the goalie at 5:00 compares complete future decision rules from an earlier state and includes all downstream consequences of adopting those policies.

Both are valid uses of the Flux Estimand framework, but they may require different simulation designs. The distinction depends on where the counterfactual worlds begin to diverge.

This classification is exploratory and should not yet alter the required `ESTIMAND.md` template. The framework should avoid accumulating classifications prematurely until repeated applications show that the distinction is consistently useful.

Principle: the intervention should be defined at the level of the real decision being evaluated. If the decision is whether to act now, the conditioning state should occur immediately before that action. If the decision is whether to adopt a rule governing future actions, the intervention is the policy itself.

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
