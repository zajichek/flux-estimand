# Rethinking the ModelBundle

A traditional interpretation of a `flux` **ModelBundle** is that it represents a realization of a particular domain.

Examples might include:

* Hockey
* Heart Failure
* Diabetes
* Emergency Department Operations

The **Flux Estimand** framework proposes a different interpretation.

A **ModelBundle** is not intended to represent an entire domain.

Instead, a **ModelBundle** represents the implementation required to answer a specific _estimand_.

This distinction has important consequences.

Multiple **ModelBundles** may exist for the same domain.

For example:

```
Hockey

├── ThreeGoalLeadBundle
├── GoaliePullBundle
├── PenaltyKillBundle
├── OvertimeBundle
└── DraftLotteryBundle
```

We're not just trying to create a model to simulate a hockey game with infinite complexity.

Each bundle may reuse common components while differing in scope, assumptions, required processes, and validation criteria.

The estimand—not the domain—defines the bundle.

## Key Points:

* A **ModelBundle** is one possible implementation of an estimand.

* Different **ModelBundles** may implement the same estimand while differing in fidelity, assumptions, algorithms, or computational efficiency.

* Therefore, **ModelBundles** should not be interpreted as the estimands themselves, but as executable realizations designed to estimate them.

```
Decision

↓

Question

↓

Estimand
      │
      ├── defines scope
      ├── defines validation
      ├── defines sufficiency
      └── defines actionability

↓

ModelBundle
      │
      ├── entities
      ├── events
      ├── decisions
      ├── transitions
      └── observations

↓

Simulation

↓

Estimate

↓

Decision
```