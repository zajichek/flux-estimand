# ModelBundle Implementations

This directory contains one or more Flux `ModelBundle` implementations of the estimand defined in the project root [`ESTIMAND.md`](../ESTIMAND.md).

Bundles should not redefine the decision or the estimand. They may differ in assumptions, complexity, fidelity, parameterization, or computational strategy while targeting the same decision specification.

Every Flux Estimand project should generally begin with `bundles/init/`.

The `init` bundle is the minimal working estimand implementation: the simplest `ModelBundle` capable of estimating the target quantities with explicit assumptions.

Expected minimum bundle structure:

```text
bundle-name/
├── README.md
├── bundle.yml
└── <Flux implementation files>
```
