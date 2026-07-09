# Workflow

Flux Estimand is intended for decision-oriented Flux projects where the purpose of simulation is to compare counterfactual actions or policies under stated assumptions.

## Practical Steps

1. Identify the decision.

   State the concrete decision, action, or policy choice the project is meant to inform.

2. Define the conditioning state.

   Specify the point at which counterfactual worlds diverge. Treat history before this point as observed and shared across scenarios.

3. Specify counterfactual actions or policies.

   Define the alternatives to compare. These may be fixed actions, dynamic policies, or a structured policy set.

4. Define outcomes and target quantities.

   State what will be estimated from the simulations, such as event probabilities, expected outcomes, risks, or distributions.

5. Define contrasts.

   Specify how target quantities will be compared across counterfactual actions or policies.

6. Determine required state and processes.

   Identify the information and dynamics that must be represented for the comparison to be credible. The estimand specifies what must be recoverable, not the implementation details of how Flux stores it.

7. Build the minimal `init` ModelBundle.

   Start with `bundles/init/`, the simplest Flux `ModelBundle` implementation capable of estimating the target quantities under explicit assumptions.

8. Validate.

   Validate the ModelBundle implementation against quantities relevant to the estimand. Validation should focus on what affects the decision comparison, not on general realism.

9. Estimate.

   Run the counterfactual simulations and estimate the target quantities and contrasts.

10. Inform decision rules.

    Use the estimates, uncertainty, assumptions, and validation results to support a recommendation or identify when no practical preference is established.

## Recommended Project Structure

```text
estimand-project/
├── README.md
├── ESTIMAND.md
├── docs/
└── bundles/
    ├── init/
    └── alternative_bundle/
```

The root `ESTIMAND.md` is the scientific and decision specification. Each directory under `bundles/` is a Flux `ModelBundle` implementation of that estimand.
