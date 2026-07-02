# Potential Outcomes

Modern causal inference emphasizes explicit definition of the quantity of interest before selecting an estimation strategy.

Within the potential outcomes framework, an individual possesses multiple potential outcomes corresponding to different interventions or exposures. Only one of these outcomes is observed, requiring assumptions and study designs to estimate the missing counterfactual.

`flux` changes this relationship.

Rather than estimating unobserved counterfactuals from observational data alone, it allows explicit simulation of multiple realizations of the same underlying system under alternative policies, interventions, or assumptions.

This does not eliminate uncertainty.

Instead, uncertainty shifts from statistical identification toward model specification and validation.

The estimand remains central, but the mechanism used to estimate it changes.

That's where the **Flux Estimand** framework comes in.