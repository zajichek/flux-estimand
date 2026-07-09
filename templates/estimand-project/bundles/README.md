# Bundles

This directory contains Flux `ModelBundle` implementations of the `goalie_pull_policy` estimand.

Each bundle should declare the estimand it implements, the assumptions it makes, how it initializes from the estimand's conditioning state, and the target quantities it can estimate.

Recommended first bundle:

```text
init/
```

The `init` bundle should be the minimal working implementation. Additional bundles should justify how they improve or vary the implementation while preserving the same decision comparison.
