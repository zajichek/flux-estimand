# ModelBundle Implementations

A Flux `ModelBundle` is one implementation of an estimand.

It is not the estimand itself, and it is not a model of an entire domain. It is an executable realization designed to estimate the target quantities defined by a decision-oriented estimand.

## From Domain Models to Decision Implementations

A domain-first interpretation might define one broad model:

```text
Hockey
```

Flux Estimand instead organizes work around decisions:

```text
Hockey
├── GoaliePullPolicyBundle
├── PenaltyKillDecisionBundle
├── OvertimeStrategyBundle
└── DraftLotteryPolicyBundle
```

Each bundle may use hockey concepts, but each is scoped by a different estimand. The relevant question is not "Does this simulate hockey?" but "Does this implementation credibly estimate the consequences of the decision defined by the estimand?"

## Multiple Implementations

Multiple `ModelBundle` implementations may target the same estimand while differing in:

- assumptions
- state representation
- process detail
- parameterization
- fidelity
- computational strategy

This separation lets the estimand remain stable while implementations evolve, improve, or compete.

```text
Decision-Oriented Estimand
        │
        ├── init ModelBundle
        ├── higher_fidelity ModelBundle
        └── alternative_assumptions ModelBundle
```

All implementations should estimate the same target quantities and contrasts, even if they represent the system differently.

## Output Contracts

A ModelBundle implementation should produce enough output to evaluate the estimand's target quantities and contrasts.

For example, a goalie-pull estimand might require simulation output such as:

```text
policy_id
matchup_id
simulation_id
team_won
reached_overtime
empty_net_goal_allowed
```

Those fields are not the estimand. They are part of an implementation contract that allows the estimand-level target quantities to be calculated consistently across bundles.

Endpoint functions and formal output contracts are future tooling ideas; see `docs/future-directions.md`.
