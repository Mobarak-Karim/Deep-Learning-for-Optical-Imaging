# Should I Use the Authors' Code?

Use this guide before copying a research repository into your project.

## Four possible decisions

### 1. Reuse
Choose this when the code is understandable, licensed, close to your task, and reproducible.

### 2. Adapt
Choose this when the repository provides a strong tested foundation but some preprocessing, model outputs, losses, or data handling must change.

### 3. Reimplement
Choose this when the scientific method is useful but the repository is absent, incomplete, outdated, incompatible, legally unclear for reuse, or harder to adapt than to rebuild.

### 4. Reject
Choose this when the method does not match your scientific question, relies on unavailable information, cannot be validated, or adds complexity without evidence of benefit.

## Weighted decision table

Score each item 0–2.

| Criterion | 0 | 1 | 2 |
|---|---|---|---|
| Scientific task match | poor | partial | strong |
| Data/modality match | poor | partial | strong |
| License clarity | unusable/unclear | restrictions | clear/compatible |
| Paper-code agreement | poor | uncertain | strong |
| Reproducibility | fails | partial | reproduced |
| Environment maintainability | very fragile | manageable | clean |
| Training completeness | missing | partial | complete |
| Pretrained weights | no | partial | yes |
| Metric transparency | unclear | partial | clear |
| Validation suitability | poor | partial | strong |

A high score supports reuse/adaptation. A low score is a warning, not a mathematical verdict.

## Never skip the license check

Public GitHub visibility does not automatically grant permission to copy, redistribute, or create derivatives. Check the repository license and the licenses for datasets, model weights, and third-party code separately.

## Minimum reproduction gate

Before adapting the code, try to pass these gates:

1. environment installs;
2. one sample inference runs;
3. tensor preprocessing matches the paper;
4. output shape/range makes sense;
5. one published qualitative or quantitative behavior can be approximated.

If you cannot pass the gates, document why before modifying the code.

## Minimum reimplementation process

```text
Paper figure/table/equation
       ↓
Write specification in plain language
       ↓
Implement preprocessing separately
       ↓
Implement model with shape tests
       ↓
Implement each loss term separately
       ↓
Unit-test equations
       ↓
Overfit 4–16 samples
       ↓
Reproduce expected behavior
       ↓
Only then optimize or extend
```
