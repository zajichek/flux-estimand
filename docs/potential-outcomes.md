# Potential Outcomes

[Flux Estimand](https://github.com/zajichek/flux-estimand) is inspired by counterfactual reasoning in causal inference, including the [potential outcomes framework](https://en.wikipedia.org/wiki/Rubin_causal_model).

[Potential outcomes](https://en.wikipedia.org/wiki/Rubin_causal_model) make the target comparison explicit: what would happen under one action versus another? In observed data, only one realized world is usually seen for a given unit or situation. The counterfactual worlds are unobserved and must be addressed through study design, assumptions, and estimation strategy.

[Flux](https://github.com/jarrod-dalton/flux) changes the mechanics of the comparison, but it does not remove the need for assumptions.

A [Flux](https://github.com/jarrod-dalton/flux) `ModelBundle` can simulate alternative worlds under different actions or policies. [Flux Estimand](https://github.com/zajichek/flux-estimand) structures those simulations so the comparison is tied to a clear decision problem, conditioning state, target quantities, and validation requirements.

## Core Principle

Counterfactual worlds should differ only at the decision, action, or policy being evaluated.

History before the conditioning state is treated as observed and shared. From that shared state, the simulation branches into alternative worlds. This helps attribute differences in outcomes to the decision being studied rather than to unrelated variation introduced before the decision point.

## What Simulation Does and Does Not Solve

Simulation can make counterfactual worlds executable under stated assumptions. It does not guarantee that those assumptions are correct, that the state representation is sufficient, or that the processes are valid.

[Flux Estimand](https://github.com/zajichek/flux-estimand) therefore shifts attention from simply running simulations to specifying:

- what decision is being evaluated
- where the counterfactual worlds diverge
- which target quantities matter
- what assumptions make the comparison meaningful
- how the `ModelBundle` implementation should be validated

The framework complements causal inference ideas; it is not a replacement for established causal inference methods.
