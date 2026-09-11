# Paper-to-Code Checklist

Copy this file for every paper you seriously consider implementing.

## A. Paper identity

```text
Paper title:
Authors:
Year:
DOI/URL:
Repository:
Repository commit/tag:
Code license:
Weights license:
Dataset license:
```

## B. Scientific question

```text
Problem:
Input modality:
Input dimensions/channels:
Target:
Independent biological unit:
Population/specimens:
Claimed improvement:
Comparison baseline:
Critical scientific failure mode:
```

## C. Data pipeline

```text
Train subjects:
Validation subjects:
Test subjects:
Split unit:
Patch extraction:
Resize/crop:
Normalization:
Clipping/log transform:
Augmentation:
Registration:
Target generation:
Blank/artifact rejection:
```

## D. Architecture

```text
Architecture family:
Input shape:
Encoder stages:
Decoder stages:
Channels:
Kernel sizes:
Downsampling:
Upsampling:
Skip connections:
Normalization layers:
Activations:
Dropout:
Attention/residual blocks:
Output channels:
Output activation:
Parameter count if reported:
```

## E. Loss / equations

For every loss term record:

```text
Name:
Equation:
Input:
Reduction:
Coefficient:
Smoothing constants:
Class weights:
Implementation file/function:
```

## F. Training

```text
Optimizer:
Learning rate:
Weight decay:
Scheduler:
Warmup:
Batch size:
Epochs:
Gradient clipping:
AMP:
Checkpoint rule:
Early stopping:
Seed:
Hardware:
Software versions:
```

## G. Evaluation

```text
Primary metric:
Exact definition:
Threshold:
Aggregation level:
Postprocessing:
Confidence intervals:
External validation:
Main reported number:
```

## H. Paper/code discrepancy log

| Item | Paper | Code | Decision | Evidence |
|---|---|---|---|---|
| | | | | |

## I. Reproduction outcome

```text
Inference example runs: YES/NO
Released checkpoint runs: YES/NO
Reference metric reproduced: YES/NO/PARTIAL
Training reproduced: YES/NO/NOT ATTEMPTED
Observed result:
Expected result:
Differences:
Fixes made:
```

## J. Final decision

```text
[ ] REUSE
[ ] ADAPT
[ ] REIMPLEMENT
[ ] REJECT

Reason:
Scientific risk:
Technical risk:
Next experiment:
```
