# Deep-Learning Experiment Checklist

## Before training

```text
□ Scientific question written
□ Independent biological unit defined
□ Train/val/test split saved as manifest
□ No specimen overlap across splits
□ Input/target shapes verified
□ Dtype/range/normalization verified
□ Augmentations scientifically plausible
□ Simple baseline defined
□ Loss tested on simple known cases
□ Metric tested on simple known cases
□ Tiny-set overfit test planned
□ Seed/config/version recorded
```

## During training

```text
□ Training and validation losses saved
□ Primary validation metric saved
□ LR saved
□ Checkpoint rule fixed in advance
□ NaN/Inf monitored
□ Representative predictions inspected
□ No test-set tuning
```

## Before final test

```text
□ Architecture/hyperparameters frozen
□ Threshold/postprocessing frozen
□ Best checkpoint selected from validation only
□ Test code run once/finally
```

## After test

```text
□ Per-specimen metrics saved
□ Mean/median + variability reported
□ Worst cases reviewed
□ Failure-case library created
□ Domain shift assessed
□ Hallucination/deletion tests performed for generated/restored images
□ External validation attempted when feasible
□ Limitations written
□ Environment/config/commit archived
```
