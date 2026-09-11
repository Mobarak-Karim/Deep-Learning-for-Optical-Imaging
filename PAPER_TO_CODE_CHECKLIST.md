# Paper → Code Checklist

Copy this file for every paper you seriously consider implementing.

## 1. Scientific question

- **Paper:**
- **DOI / URL:**
- **Modality:** OCT / fluorescence / LSFM / MUSE / histology / other
- **Task:** segmentation / denoising / restoration / classification / translation / reconstruction / other
- **What exact problem does the paper claim to solve?**
- **Is that actually the same as my problem?**

## 2. Data specification

- Input tensor/image:
- Target:
- Paired or unpaired:
- 2-D / 2.5-D / 3-D:
- Channels:
- Spatial resolution / pixel size:
- Training data size:
- Biological unit (patient/specimen/animal):
- Train/validation/test splitting rule:
- External dataset:

## 3. Preprocessing

- Intensity normalization:
- Cropping/resizing:
- Registration/alignment:
- Background correction:
- Augmentation:
- Patch extraction:
- Anything described only in supplement/code:

## 4. Model specification

- Architecture:
- Encoder/backbone:
- Input shape:
- Output shape:
- Activation:
- Normalization layers:
- Skip connections:
- Pretrained weights:
- Parameter count if reported:

## 5. Loss / optimization

Write the original equation before translating it.

- Loss equation:
- Meaning of every term:
- Weights/lambdas:
- Optimizer:
- Learning rate:
- Scheduler:
- Batch size:
- Epochs/iterations:
- Weight decay:
- Gradient clipping:
- Checkpoint selection:

## 6. Reported metrics

- Primary metric:
- Exact definition/implementation:
- Averaged per image, specimen, or pixel?:
- Confidence intervals?:
- Statistical test?:
- Best reported result:

## 7. Repository audit

- GitHub/repository URL:
- License:
- Commit/tag used:
- Environment file:
- Python version:
- PyTorch version:
- CUDA version:
- Training code:
- Inference code:
- Pretrained weights:
- Data loader:
- Metric code:
- Random seed:
- Paper/code discrepancy:

## 8. Reproduction result

- Can one provided example run?: YES / NO
- Can pretrained inference reproduce a plausible result?: YES / NO
- Can a reported metric/result be approximately reproduced?: YES / NO
- What failed?:

## 9. Decision

Choose one:

- [ ] Use authors' code as baseline
- [ ] Reuse selected components only
- [ ] Adapt the full implementation
- [ ] Reimplement from paper
- [ ] Do not use this method

### Reason

Write the scientific and engineering reason, not just "code works" or "code is old."

## 10. Validation plan for my data

- Biological-unit split:
- Domain-shift tests:
- Quantitative metric:
- Optical/physical validation:
- Biological/pathology validation:
- Failure cases to inspect:
- What result would make me reject the method?:
