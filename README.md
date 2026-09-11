# Deep Learning for Optical Imaging

**Author: Md. Mobarak Karim, Ph.D.**

A self-contained, research-practical course for learning deep learning in the context of **optical and biomedical imaging**. The course is designed so that a motivated beginner can move from basic deep-learning concepts to reading a paper, auditing the authors' code, reproducing it, deciding whether to reuse/adapt/reimplement it, validating the method scientifically, and optimizing the implementation.

The course emphasizes OCT, fluorescence microscopy, light-sheet microscopy, MUSE/slide-free histology, virtual staining, segmentation, denoising/restoration, and related optical-imaging workflows.

## What makes this course different

This is not a "copy a PyTorch model and train it" course. Every lesson asks:

1. **What problem am I solving?**
2. **What is the scientific input and target?**
3. **What equation or modeling assumption is being used?**
4. **Why is this architecture/loss/metric reasonable?**
5. **What can go wrong?**
6. **How will I prove the result is valid?**
7. **Should I reuse authors' code, adapt it, reimplement it, or reject it?**
8. **How should I optimize only after correctness?**

## Complete learning map

```mermaid
mindmap
  root((Deep Learning for Optical Imaging))
    Foundations
      Neural networks
        Weighted sums
        Activations
        Forward pass
      Learning
        Loss
        Gradients
        Backpropagation
        Optimizers
      PyTorch
        Tensors
        NCHW
        Autograd
        nn.Module
        Dataset/DataLoader
    Optical imaging data
      Modalities
        OCT
        Fluorescence
        LSFM
        MUSE
        Histology
      Data design
        Specimen-level split
        Patches
        2D 2.5D 3D
        Normalization
        Augmentation
        Registration
    Paper to code
      Read paper
        Scientific claim
        Architecture
        Equations
        Metrics
      Audit GitHub
        License
        Environment
        Dataloader
        Model
        Loss
        Metrics
      Reproduce
      Reimplement
      Reuse adapt reject
    Applications
      Segmentation
        U-Net
        Dice
        BCE
      Restoration
        Denoising
        PSNR
        SSIM
        Hallucination
      Virtual staining
        Paired
        Unpaired
        Morphology fidelity
      Small data
        Transfer learning
        Cross-validation
        Imbalance
    Validation
      Leakage
      External validation
      Domain shift
      Uncertainty
      Calibration
      Failure cases
      Hallucination tests
    Optimization
      Measure first
      AMP
      DataLoader
      Memory
      Profiler
      torch.compile
    Research output
      Reproducible config
      Split manifest
      Paper checklist
      Code audit
      Final report
```

## The central research decision

```mermaid
flowchart TD
    A[Define optical-imaging question] --> B[Read paper deeply]
    B --> C[Build paper specification]
    C --> D{Authors' code available?}
    D -->|No| E[Minimum faithful reimplementation]
    D -->|Yes| F[Audit license + repository]
    F --> G{Can one published result be reproduced?}
    G -->|Yes| H{Does method match your data/problem?}
    G -->|No| I[Debug reproduction and document discrepancy]
    I --> J{Still trustworthy/useful?}
    J -->|No| E
    J -->|Yes| H
    H -->|Strong match| K[Reuse as reference baseline]
    H -->|Partial match| L[Adapt selected components]
    H -->|Poor code fit but useful idea| E
    H -->|Poor scientific fit| M[Reject method]
    K --> N[Build your own baseline]
    L --> N
    E --> N
    N --> O[Validate scientifically]
    O --> P[Optimize only after correctness]
```

## Course order

| Lesson | Topic | Main question |
|---|---|---|
| [`00_setup_reproducibility.ipynb`](00_setup_reproducibility.ipynb) | Setup + reproducibility | Can another researcher reconstruct my experiment? |
| [`01_tensors_autograd_models.ipynb`](01_tensors_autograd_models.ipynb) | Deep-learning foundations | What does a neural network actually compute and learn? |
| [`02_optical_imaging_datasets.ipynb`](02_optical_imaging_datasets.ipynb) | Optical-imaging data | How should images, specimens, patches, normalization, and splits be designed? |
| [`03_cnn_training_baseline.ipynb`](03_cnn_training_baseline.ipynb) | CNN + training baseline | Can I build and debug a simple correct baseline first? |
| [`04_read_a_paper_like_an_engineer.ipynb`](04_read_a_paper_like_an_engineer.ipynb) | Read a paper | How do I convert paper prose/figures/equations into an implementation specification? |
| [`05_audit_authors_code.ipynb`](05_audit_authors_code.ipynb) | Audit authors' code | Should I trust/reuse this GitHub repository? |
| [`06_reproduce_authors_repository.ipynb`](06_reproduce_authors_repository.ipynb) | Reproduction | Can I reproduce one reference result before changing the code? |
| [`07_reimplement_from_paper.ipynb`](07_reimplement_from_paper.ipynb) | Reimplementation | What is the cleanest process when public code is missing, broken, or unsuitable? |
| [`08_segmentation_unet.ipynb`](08_segmentation_unet.ipynb) | Segmentation | How do U-Net, BCE, Dice, thresholds, and optical QC fit together? |
| [`09_denoising_restoration.ipynb`](09_denoising_restoration.ipynb) | Denoising/restoration | How do I improve image quality without deleting or inventing structures? |
| [`10_virtual_staining_translation.ipynb`](10_virtual_staining_translation.ipynb) | Virtual staining | How do pairing, registration, losses, GANs, color, and morphology validation interact? |
| [`11_small_data_transfer_learning.ipynb`](11_small_data_transfer_learning.ipynb) | Small biomedical data | How do I work honestly with few independent specimens? |
| [`12_validation_leakage_hallucination.ipynb`](12_validation_leakage_hallucination.ipynb) | Scientific validation | Is performance real, generalizable, and biologically defensible? |
| [`13_optimization_amp_profiler_compile.ipynb`](13_optimization_amp_profiler_compile.ipynb) | Optimization | How do I make a correct implementation faster and more memory-efficient? |
| [`14_final_paper_to_code_project.ipynb`](14_final_paper_to_code_project.ipynb) | Final project | Can I take one paper from selection to validated implementation? |
| [`15_case_study_CARE_fluorescence_restoration.ipynb`](15_case_study_CARE_fluorescence_restoration.ipynb) | **Case study: CARE / CSBDeep** | How do I reproduce paired fluorescence restoration and decide reuse vs reimplementation? |
| [`16_case_study_Noise2Void_self_supervised_denoising.ipynb`](16_case_study_Noise2Void_self_supervised_denoising.ipynb) | **Case study: Noise2Void** | How do I reproduce a legacy self-supervised denoising method and evaluate its noise assumptions? |
| [`17_case_study_original_UNet_segmentation.ipynb`](17_case_study_original_UNet_segmentation.ipynb) | **Case study: original U-Net** | How do I reproduce the original segmentation logic and adapt it honestly to OCT/MUSE/fluorescence/LSFM? |
| [`18_case_study_MUSE_virtual_HE.ipynb`](18_case_study_MUSE_virtual_HE.ipynb) | **Case study: MUSE → virtual H&E** | When should I use pix2pix, CycleGAN, or a Beer–Lambert/color-mapping baseline for MUSE virtual histology? |

## Full paper-to-code case studies

The final case-study notebooks walk through **real published papers, historical/public implementations where available, and explicit reimplementation strategies when authors-specific code is not released**.

### Case study 1 — CARE / CSBDeep

```text
paper
→ select one fluorescence-restoration experiment
→ audit CSBDeep
→ freeze an exact environment
→ reproduce authors' example first
→ map paper concepts to source code
→ reproduce a small reference result
→ build a transparent teaching baseline
→ decide REUSE / ADAPT / REIMPLEMENT / REJECT
```

### Case study 2 — Noise2Void

```text
paper
→ identify blind-spot assumptions
→ audit the legacy juglab/n2v repository
→ reproduce in a pinned TensorFlow environment
→ understand masking + masked-pixel loss
→ reimplement the core idea transparently
→ test structured-noise failure modes
→ decide whether N2V is statistically suitable for the optical modality
```

### Case study 3 — Original U-Net

```text
paper
→ reproduce original shape logic + historical Caffe release
→ identify valid convolutions, cropping, weighted borders, augmentation, overlap-tile inference
→ build a transparent modern PyTorch teaching implementation
→ document every deviation from the original
→ adapt to OCT / MUSE / fluorescence / LSFM segmentation
```

### Case study 4 — MUSE → virtual H&E

```text
MUSE + accurately registered H&E pair?
→ pix2pix candidate

no exact pair, but representative MUSE and H&E domains?
→ CycleGAN candidate

small data / need deterministic auditable baseline?
→ Beer–Lambert / color-mapping baseline
```

The MUSE notebook uses the peer-reviewed Deep-MUSE paper as the main study and connects it to earlier MUSE virtual-H&E color mapping and unpaired MUSE→H&E GAN work. It emphasizes registration, input inversion, specimen-level splitting, morphology preservation, tiled inference, and pathologist-oriented validation.

These notebooks distinguish **exact authors-code reproduction** from a **teaching reimplementation**. A simplified PyTorch example is never presented as a reproduction of the paper's numerical results.

## How each notebook is designed

Each lesson contains:

- a learning mind map;
- concepts explained before code;
- equations translated into programming logic;
- heavily commented examples;
- optical-imaging-specific examples;
- decision rules (when to use / when not to use);
- common failure modes;
- validation questions;
- research checklists;
- worked reasoning examples.

## Companion guides

- [`DEEP_LEARNING_CHEATSHEET.md`](DEEP_LEARNING_CHEATSHEET.md) — neural-network/PyTorch concepts and training workflow.
- [`OPTICAL_IMAGING_CHEATSHEET.md`](OPTICAL_IMAGING_CHEATSHEET.md) — model/loss/metric/validation starting points for OCT, fluorescence, MUSE, virtual staining, segmentation, restoration, and classification.
- [`PAPER_TO_CODE_CHECKLIST.md`](PAPER_TO_CODE_CHECKLIST.md) — complete paper specification template.
- [`CODE_REUSE_DECISION_GUIDE.md`](CODE_REUSE_DECISION_GUIDE.md) — evidence-based reuse/adapt/reimplement/reject decision.
- [`EXPERIMENT_CHECKLIST.md`](EXPERIMENT_CHECKLIST.md) — before/during/after training.
- [`REFERENCES.md`](REFERENCES.md) — official PyTorch and scientific-imaging references.

## Recommended research workflow

```text
scientific question
→ define independent biological unit
→ establish simple baseline
→ read candidate paper
→ extract exact method specification
→ audit code/license
→ reproduce one reference result
→ decide reuse/adapt/reimplement/reject
→ tiny-set overfit test
→ train on valid specimen split
→ validate metrics + failure cases
→ test domain shift / hallucination risk
→ profile time and memory
→ optimize one bottleneck at a time
→ freeze final model and test once
→ report limitations and reproducibility information
```

## Installation

Use a dedicated environment. Install PyTorch from the official selector appropriate for your operating system and GPU, then install the remaining course packages.

```bash
python -m venv .venv

# Windows
.venv\Scripts\activate

# macOS/Linux
source .venv/bin/activate

python -m pip install -r requirements.txt
jupyter lab
```

Check PyTorch:

```python
import torch
print(torch.__version__)
print(torch.cuda.is_available())
if torch.cuda.is_available():
    print(torch.cuda.get_device_name(0))
```

## Data policy

Do not commit private, patient-identifiable, proprietary, or unpublished research data to this public repository. Keep authoritative raw data unchanged. Save split manifests and metadata necessary to reproduce the experiment.

## Scientific rule for generated/restored images

> **A visually attractive deep-learning output is not automatically a scientifically correct output.**

For restoration, super-resolution, reconstruction, virtual staining, or modality translation, explicitly test whether the model removes real structures or creates plausible structures unsupported by the measurement.

## Author

**Md. Mobarak Karim, Ph.D.**  
GitHub: [Mobarak-Karim](https://github.com/Mobarak-Karim)

## License

New course material is released under the MIT License. External repositories, pretrained weights, datasets, and figures retain their own licenses and must be checked independently.
