---
id: goalie_pull_policy
title: Optimal Goalie Pull Timing for a Specified NHL Playoff Matchup
question: >
  When should a team pull its goalie to maximize the probability of winning
  a specified NHL playoff matchup?
domain: Hockey
version: 0.1.0
status: Draft
---

# Flux Estimand

## 1. Decision Context

NHL coaches must decide when to remove their goaltender for an extra attacker when trailing late in a playoff game. Pulling the goalie earlier increases offensive pressure but also increases the risk of conceding an empty-net goal. The decision is inherently matchup dependent, depending on team strengths, scoring rates, defensive ability, and game state.

This model aims to inform that coaching decision for a specific playoff matchup.

## 2. Research Question

For a specified NHL playoff matchup, what goalie-pull strategy maximizes the probability of advancing to overtime or winning the game?

The objective is not to determine a universal pull time, but rather to identify the optimal policy for the particular teams being modeled.

## 3. Target Population / Initial Conditions

The target population consists of games between the specified home and away teams under playoff conditions.

Each simulation begins at puck drop and evolves according to the defined game processes.

Alternative initial states may later be considered (e.g., beginning with six minutes remaining while trailing by one goal), but the primary estimand is based on full-game simulation.

## 4. Counterfactual Scenarios / Policies

The same matchup is simulated repeatedly under alternative goalie-pull policies.

Examples include:

Pull goalie at exactly 4:00 remaining.
Pull goalie at exactly 3:00 remaining.
Pull goalie at exactly 2:00 remaining.
Pull goalie when win probability falls below a specified threshold.
Pull goalie according to a dynamic policy based on score, possession, and remaining time.

All other aspects of the simulation remain unchanged.

## 5. Outcome

Primary outcome:

Probability of winning the game.

Secondary outcomes:

Probability of reaching overtime.
Probability of scoring while the goalie is pulled.
Probability of allowing an empty-net goal.
Expected goal differential.
Distribution of final game outcomes.

## 6. Contrast

Compare the estimated outcome distributions across goalie-pull policies.

Primary contrast:

Difference in win probability between competing policies.

Secondary contrasts may include expected overtime probability and expected goal differential.

## 7. Time Horizon

The simulation begins at puck drop and ends when the game reaches its terminal state.

Initially this includes regulation only.

Future versions may extend through overtime and shootouts.

## 8. Required State

The model must represent sufficient game state to evaluate goalie-pull decisions.

Minimum required state includes:

Game clock
Period
Score
Goalie status
Team identities
Home/away designation
Team strength parameters

Potential future additions include:

Possession
Offensive zone possession
Manpower situation
Timeout availability

## 9. Required Processes

Required processes include:

Goal scoring
Period transitions
Goalie pull decision
Empty-net scoring dynamics
Game termination

Processes should only be included if they materially influence estimation of the target estimand.

## 10. Model Sufficiency

The model is considered sufficient when it can estimate matchup-specific differences between goalie-pull policies while reproducing the aspects of NHL playoff hockey that materially influence those estimates.

Additional realism should only be introduced when it meaningfully changes the estimated policy comparison.

Processes that do not materially affect the estimand are intentionally excluded.

## 11. Validation Targets

Before comparing policies, the model should reasonably reproduce observed playoff hockey characteristics, including:

Goal scoring rates
Goal timing distributions
Empty-net goal frequency
Team-specific offensive and defensive performance
Home ice advantage
Historical win probabilities

Validation focuses on quantities relevant to the estimand rather than overall realism.

## 12. Actionability / Decision Rules

The model is intended to recommend goalie-pull policies for the specified matchup.

If one policy consistently produces a higher probability of winning across repeated simulations, it becomes the preferred recommendation.

If multiple policies produce similar results within simulation uncertainty, no practical preference is established.

The model should support both policy comparison and sensitivity analyses to understand how recommendations change under alternative assumptions.

## 13. Out of Scope

This model is not intended to answer questions regarding:

Individual player value
Line combinations
Trade decisions
Draft strategy
Season-long roster construction
Injury risk
Referee performance

The model addresses only goalie-pull strategy for a specified matchup.

## 14. Assumptions

The simulation assumes that the modeled processes adequately capture the aspects of gameplay relevant to goalie-pull decisions.

Parameter estimates are assumed to represent the specified teams under playoff conditions.

Unmodeled processes are assumed either to have negligible influence on the estimand or to contribute similarly across the policies being compared.

## 15. Open Questions

Potential areas for future refinement include:

Should goalie-pull decisions depend on puck possession?
Should team-specific coaching tendencies be represented?
Should player fatigue influence late-game scoring rates?
How should overtime strategy be incorporated?
How should uncertainty in model parameters propagate into policy recommendations?
Can adaptive policies outperform fixed pull times?