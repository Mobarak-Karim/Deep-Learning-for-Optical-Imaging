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
