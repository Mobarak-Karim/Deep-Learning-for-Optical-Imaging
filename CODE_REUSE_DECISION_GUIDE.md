# Authors' Code: Reuse, Adapt, Reimplement, or Reject?

## Step 1 — Ask whether the method matches the problem

Do not evaluate code quality before asking whether the scientific problem itself matches.

```text
same input modality?
same target definition?
similar sampling/resolution?
similar population/tissue?
similar acquisition physics?
same intended use: visualization vs quantitative analysis?
```

## Step 2 — Check legal/usage constraints

Public GitHub code is not automatically free to reuse. Check code, weights, data, and assets separately.

## Step 3 — Audit reproducibility

Strong evidence:
- pinned/clear environment;
- full training + inference code;
- explicit preprocessing;
- configs;
- released weights;
- metric implementation;
- reproducible example.

Weak evidence:
- only model class;
- no dataloader;
- no license;
- hidden preprocessing;
- README contradicts code;
- unknown split.

## Step 4 — Make one of four decisions

### REUSE

Use the code as a reference/baseline when:
- task/data fit is close;
- license permits use;
- code/paper match;
- reference result can be reproduced;
- dependencies are manageable.

### ADAPT

Reuse selected components when:
- architecture or utilities are useful;
- your data/target/preprocessing differ;
- the code is modular enough to change safely.

Keep authors' reference environment separate from your adapted environment.

### REIMPLEMENT

Write a clean implementation when:
- concept is useful but code is absent/incomplete;
- license prevents reuse;
- dependencies are too fragile;
- code is tightly coupled to unrelated infrastructure;
- paper/code discrepancies are large.

Use a paper specification + unit tests + tiny-set overfit.

### REJECT

Do not use the method when:
- scientific assumptions do not match your data;
- validation is fundamentally weak for your intended use;
- reported performance depends on leakage/confounding;
- the method cannot be validated adequately for the risk level.

## Evidence scorecard

Score 0–2 and write evidence, not just a number.

| Category | 0 | 1 | 2 |
|---|---|---|---|
| scientific task match | poor | partial | close |
| modality/data match | poor | moderate | close |
| license | unusable/unclear | restricted | compatible |
| preprocessing clarity | hidden | partial | explicit |
| paper/code agreement | poor | mixed | strong |
| environment | broken | recoverable | reproducible |
| pretrained weights | none/unusable | partial | usable |
| metric verification | unclear | partial | verified |
| split validity | concerning | uncertain | strong |
| external validation | none | limited | strong |

The score supports reasoning; it does not replace it.
