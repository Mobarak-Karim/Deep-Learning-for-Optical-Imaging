# Optical-Imaging Deep-Learning Cheat Sheet

## Start with the scientific task, not the architecture

| Problem | First baseline | Typical loss | Primary validation |
|---|---|---|---|
| binary segmentation | U-Net | BCE + Dice | Dice + sensitivity + overlays |
| multi-class segmentation | U-Net/ResUNet | CE + Dice | per-class Dice/IoU |
| image classification | small ResNet | cross-entropy | AUROC/F1 + calibration |
| fluorescence denoising | residual CNN/U-Net | L1 first | PSNR/SSIM + dim-structure preservation |
| OCT denoising/restoration | residual CNN/U-Net | L1/Charbonnier + structural term | structure, profiles, downstream metrics |
| super-resolution | residual U-Net/RCAN-style baseline | L1 first | resolution target + PSNR/SSIM + hallucination tests |
| MUSE → virtual H&E | paired U-Net/ResUNet first | L1 + structural/color term | morphology + color + blinded review |
| label-free → fluorescence | encoder-decoder | L1/L2 + structural | correlation/SSIM + biological measurements |
| quantitative regression | small CNN/MLP baseline | MSE/L1 | error, bias, calibration, physical plausibility |

## Modality-specific questions

### OCT

```text
□ B-scan or volume?
□ linear intensity or log-compressed display image?
□ axial/lateral sampling?
□ scanner/vendor?
□ reconstruction settings?
□ speckle statistics relevant?
□ quantitative attenuation/intensity preserved?
□ pathology/domain shift?
```

### Fluorescence microscopy

```text
□ photon-limited regime?
□ detector/read noise?
□ exposure/power variation?
□ bleaching?
□ channel crosstalk?
□ absolute intensity biologically meaningful?
□ dim puncta/small structures preserved?
```

### LSFM / volumetric microscopy

```text
□ 2-D, 2.5-D, or 3-D model?
□ anisotropic z spacing?
□ tile/stitch artifacts?
□ attenuation with depth?
□ motion/time-series correlation?
□ animal/embryo-level split?
```

### MUSE / virtual staining / histology

```text
□ paired or unpaired?
□ registration accuracy?
□ tissue preparation differences?
□ color calibration/batch effect?
□ nuclei/gland/vessel morphology preserved?
□ model can invent/delete diagnostic structures?
□ patient-level split?
```

## Segmentation checklist

```text
Input -> logits -> loss -> probability -> threshold -> mask -> QC
```

Never use thresholded masks inside a differentiable training loss.

Validate:
- Dice/IoU;
- sensitivity/specificity;
- thin/small structure performance;
- boundary quality;
- per-specimen distribution;
- worst-case overlays.

## Restoration / denoising checklist

```text
□ What is the clean target?
□ Is it truly aligned?
□ Does simulated noise match the instrument?
□ Is intensity quantitative?
□ PSNR/SSIM computed with correct data range?
□ Are dim structures erased?
□ Are structures hallucinated in blank/low-SNR regions?
□ Does downstream measurement change?
```

## Virtual-staining checklist

```text
□ pairing/registration documented
□ deterministic baseline tested before GAN
□ pixel/structural/adversarial loss roles separated
□ color measured
□ morphology measured
□ false insertion/deletion tested
□ rare pathology represented
□ external tissue/site/instrument tested
```

## Data split rule

```text
independent specimen first
↓
train / validation / test
↓
then patches / slices / frames within each split
```

Never random-split patches first when patches share a patient/animal/tissue source.

## Metric selection

| Task | Useful metrics | What they do not prove |
|---|---|---|
| segmentation | Dice, IoU, sensitivity, specificity | biological importance of each error |
| restoration | PSNR, SSIM | absence of hallucination |
| classification | AUROC, PR-AUC, sensitivity/specificity | calibration/generalization |
| regression | MAE, RMSE, bias, correlation | causal/physical validity |
| virtual staining | SSIM/color difference/morphology | diagnostic safety by themselves |

## Hallucination stress tests

```text
blank field
low-SNR field
rare morphology
synthetic inserted structure
synthetic removed structure
phantom/resolution target
new instrument/site
new acquisition parameters
```

Always inspect input, target, output, and error map.

## Model-selection rule

```text
Start simple.
Prove the data pipeline.
Prove the split.
Prove the metric.
Prove tiny-set overfit.
Then increase architecture complexity.
```

Do not start with a transformer/diffusion model only because the paper is newer.
