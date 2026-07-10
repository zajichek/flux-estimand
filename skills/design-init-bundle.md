# Design Init Bundle

## Purpose

Guide an agent from a downstream Flux Estimand project's root `ESTIMAND.md` to a minimal `bundles/init/` design.

The `init` bundle is the first executable `ModelBundle` implementation of the estimand. It should estimate the target quantities with the least complexity needed under explicit assumptions.

## Inputs

- `ESTIMAND.md`
- optional project `README.md`
- optional template reference at `templates/estimand-project/bundles/init/`

## Required Output

Produce proposed contents or design notes for:

- `bundles/init/README.md`
- `bundles/init/bundle.yml`
- minimal required state schema
- minimal processes
- required simulation outputs / endpoint fields
- exclusions

## Philosophy

`init` is the minimal working estimand implementation.

It should estimate the target quantities with the least complexity needed. Additional realism belongs in later bundles only if justified by the estimand.

The bundle should preserve the estimand's decision, conditioning state, counterfactual actions or policies, outcomes, contrasts, assumptions, and target quantities.

## Reasoning Steps

1. Read the estimand before proposing bundle structure.
2. Extract the decision, conditioning state, counterfactual actions or policies, target quantities, and contrasts.
3. Identify the minimal state needed to make those quantities recoverable.
4. Identify the minimal processes needed to evolve from the conditioning state to the time horizon.
5. Define the simulation outputs needed to calculate the target quantities.
6. State bundle-specific assumptions separately from estimand assumptions.
7. List exclusions so omitted realism is intentional.

## Guardrails

- Do not add players, agents, detailed event systems, or rich realism unless required by the estimand.
- Do not change the estimand to fit the bundle.
- The bundle declares the `estimand_id` it implements.
- The bundle should document its assumptions separately from the estimand assumptions.
- Keep execution inputs and internal schemas in bundle documentation, not in `ESTIMAND.md`.
