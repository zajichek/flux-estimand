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

## Backstory

While developing a hockey simulation in Flux, it became apparent that model complexity naturally grows without bound. Every omitted mechanism—players, line changes, fatigue, coaching decisions, puck possession—can be argued to improve realism. Without an explicit target, there is no principled stopping point.

The Flux Estimand framework emerged from this observation. Rather than asking "How do we simulate hockey?", it asks "What question are we trying to answer about hockey?" The estimand provides the grounding needed to determine what must be modeled, what may be ignored, and when the model is sufficiently complete for its intended purpose.

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

# Scientific Evolution (future consideration)

Traditionally, computational models are often developed as isolated implementations that answer a particular research question at a point in time. As new ideas emerge, entirely new projects are frequently created, making it difficult to compare approaches or accumulate evidence in a structured manner.

The Flux Estimand framework instead proposes organizing work around a persistent question. An estimand project defines the scientific objective, while successive ModelBundles provide alternative implementations, assumptions, and modeling strategies. Because every bundle targets the same estimand, meaningful comparisons between implementations become possible, allowing the body of evidence surrounding a question to evolve over time.

### Community Development

In the future, estimand projects may provide a standardized mechanism for proposing new ModelBundles. Rather than replacing existing implementations, contributors can submit alternative bundles implementing the same estimand under different assumptions or modeling approaches.

This creates a structured process for scientific and methodological improvement while maintaining a stable specification of the underlying question.

### Future Tooling

The Flux Estimand framework is intended to be methodology-first, with tooling emerging only after repeated use across multiple estimand projects.

Over time, common patterns may naturally evolve into software that assists with creating, validating, executing, and comparing estimand projects. Potential capabilities include:

* Validation that a ModelBundle satisfies the requirements of its target estimand.
* Standardized endpoint functions for extracting the target quantities of interest.
* Automated comparison of multiple ModelBundles implementing the same estimand.
* Discovery and registration of ModelBundles associated with an estimand.
* Standardized reporting of assumptions, validation results, and model sufficiency.
* AI-assisted development of ModelBundles while preserving the estimand as the authoritative scientific specification.

The goal of future tooling is not to replace scientific reasoning, but to encode the structure of the framework into reusable infrastructure. As the methodology matures, concepts that are currently expressed as documentation may naturally evolve into executable contracts, validation tools, and project templates.

# Execution Layer (Future Consideration)

A ModelBundle defines how a system evolves, but it does not define the specific entities on which it is executed. Instead, entities are instantiated at runtime to produce an estimate for a particular situation.

This distinction naturally separates three concepts:

* Estimand — Defines the scientific question, target quantities, and admissible state space.
* ModelBundle — Defines one implementation of the estimand, including the processes, events, policies, and required state representation.
* Execution — Instantiates concrete entities and executes them through a selected ModelBundle to estimate the target quantities.

For example, an estimand may specify that inference is restricted to NHL playoff games with 10:00 remaining in regulation and the score not tied. One ModelBundle may begin simulation directly from that state, while another may simulate the entire game from puck drop and condition on reaching that state before evaluating goalie-pull policies. Both remain valid implementations of the same estimand because they estimate the same target quantities under the same scientific specification.

Future tooling may formalize this execution layer by introducing standardized representations for execution scenarios, runtime inputs, and estimation runs. This would enable multiple ModelBundle implementations to be evaluated against comparable situations while preserving the separation between the scientific question, the model implementation, and the execution of the model.