# Review Estimand

## Purpose

Guide an agent reviewing an existing `ESTIMAND.md` for conceptual clarity and consistency with the Flux Estimand methodology.

The review should test whether the document defines a decision-oriented causal comparison before judging implementation details.

## Checklist

- Is the decision clear?
- Is the conditioning state defined?
- Do counterfactual worlds diverge only at the decision, action, or policy?
- Are outcomes close to the decision being evaluated?
- Are contrasts clearly stated?
- Does Required State specify information, not entities?
- Does Required Processes specify mechanisms, not implementation-specific events?
- Does Model Sufficiency define "good enough" relative to target quantities?
- Are validation targets separate from estimand outputs?
- Are assumptions separated from bundle-specific assumptions?
- Is out-of-scope explicit?

## Common Issues

- Starting too early in the system.
- Simulating the whole domain rather than the decision.
- Treating a `ModelBundle` as the estimand.
- Mixing implementation details into the estimand.
- Defining a vague outcome like "win" when a closer decision-relevant outcome exists.
- Letting each bundle redefine the conditioning state for the same estimand.
- Adding state or process detail because it feels realistic rather than because it improves estimation.

## Output Format

Use this structure for review responses:

```text
Summary
Critical issues
Suggested revisions
Open questions
```

Lead with conceptual issues that would change the estimand. Then address clarity, duplication, and wording. Keep implementation suggestions separate from estimand revisions.
