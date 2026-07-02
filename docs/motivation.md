# Motivation

Simulation projects naturally encourage realism.

Developers continually discover additional mechanisms, interactions, and sources of variation that could be incorporated into the model. Without an explicit target, model scope expands indefinitely.

This phenomenon is not unique to `flux`—it is a common challenge in simulation modeling.

The **Flux Estimand** framework attempts to constrain this process by requiring every modeling decision to be justified relative to a predefined target quantity.

The guiding question becomes:

* Does this improve estimation of the estimand?

rather than

* Does this make the simulation more realistic?

This subtle shift changes both the development process and the philosophy of simulation modeling.

## Separating Questions from Implementations

One of the primary goals of the **Flux Estimand** framework is to separate the scientific question from its implementation.

An estimand defines what the model is intended to estimate. It does not prescribe how that quantity must be estimated.

Multiple `flux` **ModelBundles** may satisfy the same estimand while employing different assumptions, levels of abstraction, or computational techniques.

Likewise, a single **ModelBundle** may evolve substantially over time while continuing to satisfy the same estimand.

This separation allows model implementations to improve, be compared, or be replaced without changing the underlying scientific objective.

```
Scientific Question
        │
        ▼
    ESTIMAND
        │
        ▼
Implementation A ───► Estimate

Implementation B ───► Estimate

Implementation C ───► Estimate
```