# Deep-Learning Cheat Sheet

## Core objects

| Concept | Meaning | PyTorch |
|---|---|---|
| tensor | multi-dimensional numeric array | `torch.Tensor` |
| model | parameterized function | `nn.Module` |
| parameter | learned weight/bias | `model.parameters()` |
| forward pass | input → prediction | `pred = model(x)` |
| loss | training error objective | `loss_fn(pred, y)` |
| gradient | derivative of loss w.r.t. parameter | `loss.backward()` |
| optimizer | changes parameters | `torch.optim.Adam(...)` |
| dataset | returns examples | `Dataset` |
| dataloader | batches/shuffles examples | `DataLoader` |

## Image tensor shapes

```text
2-D images: [N, C, H, W]
3-D volumes: [N, C, D, H, W]
```

Never guess channel order. Print shapes.

## Correct training step

```python
model.train()
optimizer.zero_grad(set_to_none=True)
pred = model(x)
loss = loss_fn(pred, target)
loss.backward()
optimizer.step()
```

## Correct validation pattern

```python
model.eval()
with torch.no_grad():
    pred = model(x)
```

No `optimizer.step()` in validation.

## Tiny-set overfit test

Before a long experiment, try to memorize 4–16 training examples. Failure suggests a bug in data, labels, shapes, output activation, loss, optimizer, or learning rate.

## Common output/loss pairings

| Task | Model output | Typical loss |
|---|---|---|
| binary classification | 1 raw logit | `BCEWithLogitsLoss` |
| multi-class classification | C raw logits | `CrossEntropyLoss` |
| binary segmentation | 1 logit/pixel | BCEWithLogits + Dice |
| multi-class segmentation | C logits/pixel | CrossEntropy + Dice |
| regression/restoration | continuous image/value | L1/MSE + task terms |

## Sigmoid/softmax rule

`BCEWithLogitsLoss` already combines sigmoid internally. Do not apply sigmoid before it.

`CrossEntropyLoss` expects raw class logits. Do not apply softmax before it.

Use sigmoid/softmax for interpretation/inference probabilities.

## Learning-rate symptoms

```text
Too high: loss unstable/explodes, NaNs, oscillation
Too low: loss barely changes, training extremely slow
```

## Overfitting symptoms

```text
training loss ↓
training metric ↑
validation loss starts ↑
validation metric stagnates/declines
```

Before adding regularization, verify there is no leakage/split problem.

## Reproducibility essentials

```text
seed
code commit
config
split manifest
package versions
GPU
preprocessing
checkpoint-selection rule
metric implementation
```

## Optimization order

```text
correctness
→ valid split
→ tiny overfit
→ baseline
→ benchmark
→ DataLoader
→ AMP
→ batch/accumulation
→ profiler
→ torch.compile
→ distributed only if necessary
```
