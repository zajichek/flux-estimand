# Create Estimand Project

## Purpose

Guide an agent through scaffolding a new Flux Estimand project around a decision-oriented causal comparison.

The aim is not to create a full simulator. The aim is to define the decision, the counterfactual worlds to compare, and the minimum project structure needed to begin implementing the estimand.

## When to Use

Use this when a user wants to start a new Flux Estimand project, convert a broad simulation idea into an estimand project, or create a template for later `ModelBundle` implementations.

## Recommended Project Structure

```text
estimand-project/
├── README.md
├── ESTIMAND.md
├── docs/
└── bundles/
    └── init/
        ├── README.md
        └── bundle.yml
```

## Steps

1. Define the decision.

   State the decision, action, or policy choice the project is meant to inform.

2. Define the conditioning state.

   Identify where counterfactual worlds begin to diverge. Treat prior history as observed and shared.

3. Define counterfactual actions or policies.

   List the alternatives that will be compared from the same conditioning state.

4. Define outcomes and target quantities.

   Specify what will be estimated, such as probabilities, expected values, risks, or distributions.

5. Define contrasts.

   State how target quantities will be compared across actions or policies.

6. Define required state representation.

   Specify the information that must be recoverable for the estimand to be meaningful. Do not prescribe internal bundle data structures unless they are part of the scientific question.

7. Define required processes.

   Specify the mechanisms needed to estimate the target quantities credibly. Keep this at the process level rather than implementation-specific event mechanics.

8. Define model sufficiency.

   State what would make a `ModelBundle` implementation good enough to estimate the target quantities under stated assumptions.

9. Define validation targets.

   Identify the empirical or decision-relevant quantities a bundle should reproduce or satisfy before its estimates are trusted.

10. Scaffold `bundles/init/`.

    Create a minimal initial bundle directory with a `README.md` and `bundle.yml`. The `init` bundle should declare the `estimand_id` it implements and document its own assumptions separately from the estimand.

## Guardrails

- Do not start by designing a full simulator.
- Do not put bundle implementation details in `ESTIMAND.md`.
- Do not require all future bundles to use the same internal implementation.
- Keep the first bundle minimal.
- Add realism only when it materially improves estimation of the target quantities.
