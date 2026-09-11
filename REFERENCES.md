# References

Use these as primary technical references while working through the course.

## PyTorch

- PyTorch documentation: https://docs.pytorch.org/docs/stable/
- Tensors: https://docs.pytorch.org/docs/stable/tensors.html
- Autograd: https://docs.pytorch.org/docs/stable/autograd.html
- `torch.nn`: https://docs.pytorch.org/docs/stable/nn.html
- Data loading: https://docs.pytorch.org/docs/stable/data.html
- AMP: https://docs.pytorch.org/docs/stable/amp.html
- Profiler: https://docs.pytorch.org/docs/stable/profiler.html
- `torch.compile`: https://docs.pytorch.org/docs/stable/generated/torch.compile.html
- Reproducibility notes: https://docs.pytorch.org/docs/stable/notes/randomness.html

## Core architectures / concepts

- U-Net: Ronneberger et al., *U-Net: Convolutional Networks for Biomedical Image Segmentation*.
- ResNet: He et al., *Deep Residual Learning for Image Recognition*.

## Scientific image restoration caution

For restoration/reconstruction/virtual-staining research, consult peer-reviewed literature on deep-learning reconstruction artifacts/hallucinations and validate using modality-specific physical/biological tests rather than image similarity metrics alone.

## General rule

For any paper you reproduce, cite the original paper, its code repository, dataset, and pretrained weights according to their respective licenses/citation instructions.

## Paper-to-code case-study references

### CARE / CSBDeep

- Weigert M, Schmidt U, Boothe T, et al. **Content-aware image restoration: pushing the limits of fluorescence microscopy.** *Nature Methods* 15, 1090–1097 (2018). DOI: 10.1038/s41592-018-0216-7
- Official repository: https://github.com/CSBDeep/CSBDeep
- CSBDeep documentation: https://csbdeep.bioimagecomputing.com/doc/
- The current repository identifies CSBDeep as a Keras/TensorFlow toolbox for CARE and uses a BSD 3-Clause license.

### Noise2Void

- Krull A, Buchholz T-O, Jug F. **Noise2Void — Learning Denoising from Single Noisy Images.** CVPR (2019), 2129–2137.
- Paper: https://openaccess.thecvf.com/content_CVPR_2019/html/Krull_Noise2Void_-_Learning_Denoising_From_Single_Noisy_Images_CVPR_2019_paper.html
- Official repository: https://github.com/juglab/n2v
- The official repository currently warns that the legacy package is not compatible with TensorFlow 2.16 and is being superseded by newer maintained tooling such as CAREamics.
- Public fluorescence teaching dataset example: ZeroCostDL4Mic Noise2Void 2-D dataset, Zenodo DOI 10.5281/zenodo.3713315.

### Important interpretation

The case-study notebooks separate:
1. reproduction of authors' software/reference behavior;
2. modern reimplementation for understanding or long-term maintenance;
3. adaptation to a new optical modality.

Those are different scientific claims and should be reported separately.
