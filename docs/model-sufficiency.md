# Model Sufficiency

Traditional simulation often evaluates models according to realism.

**Flux Estimands** instead introduce the concept of _model sufficiency_.

A model is _sufficient_ when it contains enough structure to estimate the target estimand with appropriate credibility.

Increasing realism beyond this point may improve fidelity but does not necessarily improve the answer to the scientific question.

Model sufficiency therefore provides an explicit stopping criterion for model development.

Every proposed increase in complexity should be evaluated according to a simple question:

* Does this materially improve estimation of the estimand?

If not, additional complexity may be unnecessary.

## Sufficiency Type

### State sufficiency

* What is the minimal state representation (including the conditioning or entry state) needed to answer the estimand?

### Process sufficiency

Given that state, what dynamic processes must be represented?

# Project setup

Every estimand project should begin with a single `init` bundle.

The `init` bundle represents the minimum viable implementation capable of estimating the target estimand.

Subsequent bundles should justify their existence by introducing alternative assumptions, increased fidelity, or different modeling approaches while continuing to estimate the same target quantity.

# Conditioning States (Concept)

A possible extension of the **Flux Estimand** framework is the concept of a conditioning state.

Rather than requiring every simulation to begin at the start of the real-world process, an estimand may instead define a specific state of the system from which the target question becomes meaningful.

In this view, events occurring prior to the conditioning state are not necessarily irrelevant—they simply serve a different purpose. Their role is to determine the distribution of admissible starting states rather than to directly estimate the target quantity.

This distinction can substantially reduce model scope by allowing simulations to begin at the earliest point necessary to answer the estimand.

## Hockey Example

Consider the estimand:

> What is the optimal time for a team to pull its goalie in a specified NHL playoff matchup?

A traditional simulation might begin at puck drop and simulate an entire game.

However, the estimand is only concerned with decisions made during the final ten minutes of regulation. Therefore, one implementation may define the conditioning state as:

```
Third period
10:00 remaining
Game is not tied
Team identities specified
Current score differential observed
```

The simulation begins from this state rather than from the opening faceoff.

The first fifty minutes of gameplay are not ignored; they are simply outside the scope of the estimand. Their primary role is to determine how frequently particular late-game states occur, not to estimate the effect of alternative goalie-pull policies once those states have been reached.

## Future Possibilities

Conditioning states may provide a mechanism for composing estimands.

For example, one estimand could characterize the distribution of late-game states in NHL playoff games, while another conditions on those states to evaluate goalie-pull strategies. The output of one estimand could therefore serve as the input to another, allowing complex investigations to be decomposed into smaller, independently defined estimands.

This concept is exploratory and is not currently part of the core Flux Estimand framework.