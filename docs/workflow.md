# Estimand Project Structure

The recommended unit of organization is an **estimand project**.

An estimand project is a repository centered on a single scientific or decision-oriented target question. The root-level `ESTIMAND.md` defines the estimand: the decision context, target quantity, counterfactual scenarios, outcome, contrast, assumptions, validation targets, and model sufficiency criteria.

Flux implementations live underneath this estimand.

A single estimand may have one or more Flux `ModelBundle` implementations. Each bundle represents one executable realization of the estimand, potentially differing in assumptions, complexity, parameterization, or computational strategy.

```text
goalie-pull-estimand/
├── README.md
├── ESTIMAND.md
├── docs/
├── templates/
└── bundles/
    ├── hockey_goalie_pull_simple/
    ├── hockey_goalie_pull_possession/
    └── hockey_goalie_pull_player_level/

```

The estimand does not depend on any particular bundle. Instead, each bundle should declare which estimand it implements.

```
id: hockey_goalie_pull_simple
estimand_id: goalie_pull_policy
status: draft
```

This preserves the separation between the scientific target and the executable model realization.

## Conceptual workflow

Identify the decision.

↓

Define the estimand.

↓

Determine required counterfactuals.

↓

Determine minimum state representation.

↓

Determine required processes.

↓

Implement the ModelBundle.

↓

Validate against reality.

↓

Estimate the target quantity.

↓

Interpret results.

↓

Inform decisions.
```