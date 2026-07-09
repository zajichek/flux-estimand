# Goalie Pull Policy Estimand

This template is a decision-oriented Flux Estimand project for comparing goalie-pull policies in a specified NHL playoff matchup.

The root `ESTIMAND.md` defines the decision context, conditioning state, counterfactual policies, target quantities, assumptions, validation targets, and model sufficiency criteria.

Flux `ModelBundle` implementations live under `bundles/`. Each bundle is an executable realization of this estimand, not a general model of hockey.

Start with `bundles/init/`, the minimal implementation capable of estimating the target quantities under explicit assumptions. Add later bundles only when they introduce a meaningful change in assumptions, fidelity, validation, or computational strategy while targeting the same estimand.
