# Deep-Learning Experiment Checklist

## Before training

- [ ] Scientific question is explicit.
- [ ] Biological unit for splitting is defined.
- [ ] Train/validation/test specimen lists are saved.
- [ ] No patches from one specimen cross split boundaries.
- [ ] Input and target are spatially aligned when paired training requires alignment.
- [ ] Intensity normalization is documented.
- [ ] Augmentations are visualized.
- [ ] Model input/output shapes are tested.
- [ ] Loss components are tested independently.
- [ ] A trivial/simple baseline exists.
- [ ] The model can overfit a tiny dataset.

## During training

- [ ] Training and validation losses are logged separately.
- [ ] Learning rate is logged.
- [ ] Predictions are periodically visualized on fixed validation cases.
- [ ] Best checkpoint rule is predetermined.
- [ ] Test set is not used for model selection.
- [ ] NaN/Inf and exploding gradients are monitored when relevant.

## After training

- [ ] Metrics are computed at an appropriate biological level.
- [ ] Failure cases are reviewed, not hidden.
- [ ] Performance is stratified across relevant acquisition/specimen conditions.
- [ ] Restoration/translation results are checked for missing or invented structures.
- [ ] Model, code commit, environment, split, and parameters are recorded.
- [ ] External/domain-shift validation is performed when claims require it.
