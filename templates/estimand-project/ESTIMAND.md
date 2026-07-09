---
id: goalie_pull_policy
title: Goalie Pull Timing for a Specified NHL Playoff Matchup
question: >
  Which goalie-pull policy maximizes the probability of winning or reaching
  overtime in a specified NHL playoff matchup?
domain: Hockey
version: 0.1.0
status: Draft
---

# Flux Estimand

This estimand defines a decision-oriented causal comparison: the consequences of alternative goalie-pull policies under stated assumptions.

The Flux `ModelBundle` implementations beneath this project are executable realizations of this estimand. They are not models of all hockey; they are models built to estimate the target quantities defined here.

## 1. Decision Context

NHL coaches must decide when to remove their goaltender for an extra attacker when trailing late in a playoff game.

Pulling the goalie earlier may increase offensive pressure, but it can also increase the risk of conceding an empty-net goal. The decision is matchup dependent and may depend on score, time remaining, team strengths, game context, and the assumptions encoded in the simulation.

This estimand is intended to inform that coaching decision for a specified playoff matchup.

## 2. Research Question

For a specified NHL playoff matchup and conditioning state, which goalie-pull policy produces the most favorable target quantities?

The objective is not to determine a universal pull time. The objective is to compare counterfactual goalie-pull policies for the teams and game context being modeled.

## 3. Target Population / Conditioning State

The target population consists of playoff game states involving the specified teams under the conditions declared for the analysis.

### Conditioning State

The conditioning state is the point at which counterfactual worlds begin to diverge. History before this state is treated as observed and shared across policy scenarios.

Example conditioning state:

```text
Third period
6:00 remaining
Trailing by one goal
Specified home and away teams
Goalie currently in net
Current manpower situation observed
```

All `ModelBundle` implementations for this estimand should preserve this conditioning state. A different conditioning state would generally define a different estimand.

## 4. Counterfactual Actions or Policies

The same conditioning state is simulated under alternative goalie-pull policies.

Examples include:

- pull goalie at exactly 4:00 remaining
- pull goalie at exactly 3:00 remaining
- pull goalie at exactly 2:00 remaining
- pull goalie when win probability falls below a specified threshold
- pull goalie according to a dynamic policy based on score, possession, and remaining time

All other aspects of the conditioning state should remain shared across counterfactual policy comparisons except for downstream consequences of the policy.

## 5. Outcomes / Target Quantities

Primary target quantity:

- probability of winning the game

Secondary target quantities:

- probability of reaching overtime
- probability of scoring while the goalie is pulled
- probability of allowing an empty-net goal
- expected goal differential
- distribution of final game outcomes

## 6. Contrasts

Compare estimated target quantities across goalie-pull policies.

Primary contrast:

- difference in win probability between competing policies

Secondary contrasts may include differences in overtime probability, empty-net goal risk, and expected goal differential.

## 7. Time Horizon

The time horizon begins at the conditioning state and ends when the game reaches a declared terminal state for the estimand.

For this template, the terminal state should be chosen before comparing policies, such as the conclusion of regulation or the conclusion of overtime. Changing the terminal state may change the target quantities and should be treated as an estimand-level change.

## 8. Required State Representation

The estimand specifies what information must be recoverable, not how that information is represented internally.

Minimum required information includes:

- game clock
- period
- score
- goalie status
- team identities
- home/away designation
- team strength parameters

Potential future additions include:

- possession
- offensive zone possession
- manpower situation
- timeout availability
- fatigue or player availability

Additional state should be included when it materially improves estimation of the target quantities.

## 9. Required Processes

Required processes include:

- goal scoring
- goalie-pull policy execution
- scoring dynamics with and without an empty net
- period or terminal-state transitions
- game termination

Processes should be included when they materially influence the counterfactual policy comparison.

## 10. Model Sufficiency

A `ModelBundle` implementation is sufficient when it contains enough state and process structure to estimate the consequences of goalie-pull policies with appropriate credibility under stated assumptions.

Additional realism should be justified by whether it improves estimation of the target quantities or changes the policy contrast in a meaningful way.

## 11. Validation Targets

Before comparing policies, a `ModelBundle` implementation should reasonably reproduce or satisfy quantities relevant to the estimand, such as:

- goal scoring rates
- goal timing distributions
- empty-net goal frequency
- team-specific offensive and defensive performance
- home ice advantage
- late-game win probability patterns

Validation should focus on quantities that affect the decision comparison.

## 12. Actionability / Decision Rules

The estimand is intended to support goalie-pull policy recommendations for the specified matchup and conditioning state.

If one policy consistently produces a higher estimated win probability across simulation uncertainty and sensitivity analyses, it becomes the preferred recommendation.

If multiple policies produce similar estimates, no practical preference is established.

## 13. Out of Scope

This estimand is not intended to answer questions about:

- individual player value
- line combinations
- trade decisions
- draft strategy
- season-long roster construction
- injury risk
- referee performance

The estimand addresses goalie-pull policy for a specified matchup and conditioning state.

## 14. Assumptions

The simulation assumes that the represented state and processes adequately capture the aspects of gameplay relevant to the goalie-pull decision.

Parameter estimates are assumed to represent the specified teams under playoff conditions.

Unmodeled processes are assumed either to have negligible influence on the target quantities or to contribute similarly across policies being compared.

## 15. Open Questions

- Should goalie-pull decisions depend on puck possession?
- Should team-specific coaching tendencies be represented?
- Should player fatigue influence late-game scoring rates?
- How should overtime strategy be incorporated?
- How should uncertainty in model parameters propagate into policy recommendations?
- Can adaptive policies outperform fixed pull times?
