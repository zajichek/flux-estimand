# Flux Estimand

Every `flux` project should begin by defining its estimand.

The estimand serves as the _scientific contract_ for the project. It documents the decision being informed, the quantities to be estimated, the assumptions under which that quantities are meaningful, and the level of model complexity required to estimate them.

If the implementation changes but the estimand remains unchanged, the purpose of the project remains constant.

If the estimand changes substantially, the project is likely addressing a different scientific question and should be considered a different model.

An estimand should represent a single coherent decision problem. It may require estimating multiple related quantities or contrasts, provided they collectively inform the same decision. If a quantity serves a fundamentally different decision context, it should generally be defined in a separate estimand project.

# Item Template

You should add an `ESTIMAND.md` file at the root of your `flux` project directory with the following sections:

## 1. Decision Context
## 2. Research Question
## 3. Target Population / Initial Conditions
## 4. Counterfactual Scenarios / Policies
## 5. Outcome
## 6. Contrast
## 7. Time Horizon
## 8. Required State Representation

_What information must be represented for the estimand to be identifiable?_

## 9. Required Processes
## 10. Model Sufficiency
## 11. Validation Targets
## 12. Actionability / Decision Rules
## 13. Out of Scope
## 14. Assumptions
## 15. Open Questions
