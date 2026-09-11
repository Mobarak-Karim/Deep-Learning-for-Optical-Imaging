# Optical Imaging Deep-Learning Cheat Sheet

This sheet gives **starting points**, not automatic prescriptions. Build a simple validated baseline before moving to a more complex architecture.

## Task → baseline → loss → validation

| Optical-imaging task | Sensible first baseline | Typical first loss | Important validation |
|---|---|---|---|
| Binary segmentation | 2-D U-Net | BCE-with-logits + Dice | Dice, IoU, sensitivity, specimen-level split |
| Multi-class segmentation | U-Net / residual U-Net | Cross-entropy + Dice | per-class Dice, confusion matrix |
| Image classification | ResNet-18/34 transfer learning | Cross-entropy | AUROC, F1, sensitivity/specificity, external set |
| Fluorescence denoising | residual CNN or U-Net | L1 / Charbonnier | PSNR/SSIM + structure/intensity preservation |
| OCT denoising/speckle reduction | residual CNN/U-Net | L1/Charbonnier + optional structural term | CNR/SNR, SSIM, layer/feature preservation |
| Super-resolution | residual encoder-decoder first | L1 | PSNR/SSIM + measured resolution/structure |
| MUSE → virtual H&E | paired U-Net/ResUNet baseline | L1 + structural/color term | morphology, color consistency, pathology review |
| Label-free → fluorescence | paired encoder-decoder | L1/L2 + structural term | correlation/SSIM + biological feature validation |
| Reconstruction/inverse problem | data-consistent baseline | image loss + measurement consistency | fidelity to measured signal + task metric |
| 3-D segmentation | 3-D U-Net only if justified | Dice + CE/BCE | volume-level metrics and memory feasibility |

## Model choice hierarchy

```text
Linear/logistic baseline when applicable
        ↓
Small CNN
        ↓
U-Net or ResNet baseline
        ↓
Residual/attention modifications
        ↓
Transformer/diffusion/large model only when evidence justifies it
```

A complicated model is not automatically a better scientific model.

## Paper audit in 60 seconds

```text
TASK
□ What is input?
□ What is target?
□ Paired or unpaired?
□ 2-D / 2.5-D / 3-D?
□ Pixel size / resolution?

TRAINING
□ Normalization?
□ Augmentation?
□ Loss equation?
□ Optimizer / LR?
□ Batch size / epochs?
□ Checkpoint selection?

VALIDATION
□ Patient/specimen-level split?
□ Metric definition?
□ External test set?
□ Biological/physical validation?

CODE
□ License?
□ Environment?
□ Pretrained weights?
□ Training script?
□ Inference script?
□ Paper and code agree?
```

## Authors' code decision

| Situation | Preferred action |
|---|---|
| Code is complete, licensed, reproducible, and matches task | reuse as baseline |
| Core model useful but pipeline mismatched | reuse selected components |
| Code incomplete/outdated but paper clear | reimplement minimum faithful model |
| License unclear/incompatible | do not copy code; implement from paper concepts where legally appropriate |
| Cannot reproduce or understand result | do not build your research conclusion on it yet |

## Debugging order

```text
1. Check one sample manually
2. Check tensor shapes
3. Check dtype/range
4. Check target alignment
5. Visualize augmentation
6. Overfit 4–16 samples
7. Inspect loss curve
8. Inspect predictions
9. Only then run full training
```

## Optimization order

```text
Correctness → baseline → benchmark → DataLoader → AMP → batch strategy → profiler → compile → multi-GPU
```

### Current PyTorch patterns

```python
# AMP
scaler = torch.amp.GradScaler("cuda")
with torch.autocast(device_type="cuda", dtype=torch.float16):
    pred = model(x)
    loss = loss_fn(pred, y)

# Optional compilation after a working baseline
model = torch.compile(model)
```

Profile before guessing where time is spent.

## Optical-imaging red flags

- random patch split lets patches from one specimen appear in train and test;
- normalization differs between training and inference;
- virtual staining evaluated only by color similarity;
- denoising evaluated only by visual smoothness;
- super-resolution produces structures without measurement-domain support;
- segmentation threshold tuned on the test set;
- test data repeatedly inspected during model design;
- only the best-looking image is shown;
- no analysis across acquisition days/instruments/specimens.

## Minimum experiment record

```text
paper/method:
git commit:
Python/PyTorch/CUDA:
GPU:
data version:
train/val/test specimen IDs:
normalization:
augmentation:
model:
loss:
optimizer:
learning rate:
batch size:
epochs:
seed:
checkpoint rule:
metrics:
known limitations:
```
