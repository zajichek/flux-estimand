# Model Sufficiency

Model sufficiency is defined relative to a decision-oriented estimand.

A Flux `ModelBundle` implementation is sufficient when it contains enough state and process structure to estimate the causal consequences of the decision with appropriate credibility under stated assumptions.

Additional realism should be justified by whether it improves estimation of the target quantities, not by whether it makes the simulation more complete in general.

## State Sufficiency

State sufficiency asks:

> What information must be available at and after the conditioning state for the counterfactual comparison to be meaningful?

The estimand specifies what information must be recoverable. It does not require a particular internal representation.

For a goalie-pull decision, required state might include score, time remaining, goalie status, team identities, and team strength parameters. A more complex implementation might add possession, manpower, fatigue, or timeout availability if those additions materially affect the target quantities.

## Process Sufficiency

Process sufficiency asks:

> Given the required state, what dynamic processes must be represented to estimate the consequences of the decision?

Processes should be included when they materially affect the comparison among counterfactual actions or policies.

For a goalie-pull decision, required processes might include scoring, empty-net scoring dynamics, goalie-pull policy execution, period transitions, and game termination. Line changes or player-level fatigue may be unnecessary unless they change the estimated policy contrast in a meaningful way.

## The `init` Bundle

Every decision-oriented Flux Estimand project should begin with a single `init` bundle.

The `init` bundle is the minimum viable `ModelBundle` implementation capable of estimating the target quantities with explicit assumptions. Later bundles should justify their existence by changing assumptions, increasing fidelity, improving validation, or using a different computational strategy while continuing to target the same estimand.
