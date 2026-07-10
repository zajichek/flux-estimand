# Agent Guidance

This repository is a Flux Estimand project.

`ESTIMAND.md` is the authoritative decision specification. Begin with the decision and conditioning state, not with a general-purpose model of the domain.

A Flux `ModelBundle` is one implementation of the estimand. Implementation-specific assumptions, mechanics, runtime inputs, and schemas belong within bundle documentation.

The first implementation should normally be `bundles/init/`. Additional realism must be justified by whether it improves estimation of the target quantities. Do not change the estimand merely to fit an implementation.

## Project Context

- Estimand ID: `<ESTIMAND_ID>`
- Decision: `<DECISION>`
- Conditioning state: `<CONDITIONING_STATE>`
- Primary outcome: `<PRIMARY_OUTCOME>`
- Active bundles:
  - `init`
- Current status: `<STATUS>`

## Flux Estimand Methodology

This project follows the Flux Estimand framework:

https://github.com/zajichek/flux-estimand

Relevant reusable skills include:

- `skills/create-estimand-project.md`
- `skills/review-estimand.md`
- `skills/design-init-bundle.md`

Because remote references may not always be automatically read by coding assistants, keep the most important guardrails directly in this local `AGENTS.md`.

## Guardrails

- Treat the estimand as the authoritative specification.
- Keep the conditioning state fixed for a given estimand.
- Ensure counterfactual worlds differ only in the decision, action, or policy being evaluated.
- Keep bundle implementation details out of `ESTIMAND.md`.
- Document bundle-specific assumptions inside the relevant bundle.
- Prefer the simplest `ModelBundle` capable of estimating the target quantities credibly.
- Add state, processes, entities, or realism only when justified by the estimand.
