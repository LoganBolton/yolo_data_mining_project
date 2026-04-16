# YOLOv5 Training Analysis

Trained two YOLOv5n models on Pascal VOC:
- **From Scratch** (exp7): Random initialization
- **ImageNet Pretrained** (exp10): Fine-tuned from ImageNet weights

Same hyperparameters for both.

---

## Notebooks

**`training_comparison.ipynb`**
- Side-by-side metrics for both models
- 9-panel plot: mAP, precision, recall, losses, learning rate
- Convergence speed analysis

**`training_analysis_scratch.ipynb`**
- Training metrics for from-scratch model (exp7)
- Predictions and class examples
- Inference benchmarks

**`training_analysis_imagenet_finetune.ipynb`**
- Training metrics for pretrained model (exp6)
- Predictions and class examples
- Inference benchmarks

**`training_analysis_efficiency.ipynb`**
- Standalone inference benchmarking
- Latency, FPS, GPU usage, power consumption
- Note: Both models have identical inference speed (~4.5ms/img). Comparison plot differences are measurement noise.

---

## Files in `runs_backup/`

**exp7**: From scratch
**exp10**: ImageNet pretrained

- `hyp.yaml` - Training hyperparameters
- `opt.yaml` - Model config and training settings
- `results.csv` - Per-epoch metrics
- `events.out.tfevents.*` - TensorBoard logs
- `*.png` - Confusion matrix, PR curves, training samples, validation predictions
