# YOLOv5 Training Analysis

I trained two YOLOv5n models on the Pascal VOC dataset to compare different initialization strategies:
- **From Scratch**: Random weight initialization (exp7)
- **ImageNet Pretrained**: Fine-tuned from ImageNet weights (exp6)

Both models used identical training hyperparameters to ensure a fair comparison.

---

## 📚 Notebooks

### `training_comparison.ipynb`
**Detailed side-by-side training comparison**

This notebook shows comprehensive training metrics for both models:
- 9-panel detailed metrics plot (mAP, precision, recall, all losses)
- Summary statistics table
- Convergence speed analysis
- Early training behavior (first 20 epochs)

Key finding: The pretrained model converges faster and achieves higher final mAP.

---

### `training_analysis_scratch.ipynb`
**Complete analysis of from-scratch training (exp7)**

Full training analysis including:
- Training curves and loss progression
- Model predictions with diverse class examples
- Inference efficiency benchmarks

This is the baseline model with random initialization.

---

### `training_analysis_imagenet_finetune.ipynb`
**Complete analysis of ImageNet pretrained model (exp6)**

Same structure as the scratch notebook but for the pretrained model:
- Training metrics and convergence
- Prediction visualizations across all 20 VOC classes
- Inference performance benchmarks

This model benefits from transfer learning via ImageNet weights.

---

### `training_analysis_efficiency.ipynb`
**Standalone inference benchmarking**

Detailed inference efficiency analysis:
- Latency measurements (batch sizes 1, 4, 8, 16)
- Throughput (FPS) scaling
- GPU utilization, memory usage, power consumption
- Energy efficiency (images per joule, cost estimates)

**Note on inference metrics**: Both models have identical inference performance since they use the same architecture (YOLOv5n). Any differences in the comparison plots are just measurement noise from cold starts or GPU scheduling. The real per-image latency is ~4-5ms (~230 FPS) for both models when using batch_size=4 or higher.

---

## 📂 Training Artifacts (`runs_backup/`)

I copied the training directories here with large model weights removed. Key experiments:
- **exp7**: From scratch model
- **exp6**: ImageNet pretrained model

### Important files to review:

**`hyp.yaml`** - Training hyperparameters:
- Learning rate: 0.01 initial
- Momentum: 0.937
- Weight decay: 0.0005
- Warmup epochs: 3
- Data augmentation settings (HSV, translation, scale, etc.)

**`opt.yaml`** - Training configuration:
- Model architecture: YOLOv5n
- Image size: 640x640
- Batch size: 128
- Epochs: 100
- Optimizer: SGD

**`results.csv`** - Per-epoch metrics:
- Training losses (box, objectness, classification)
- Validation mAP@0.5 and mAP@0.5:0.95
- Precision, recall
- Learning rates

**`events.out.tfevents.*`** - TensorBoard logs for visualization

**`*.png` files** - Training visualizations:
- Confusion matrices
- Precision-Recall curves
- F1 curves
- Training batch samples
- Validation predictions

---

## 🎯 Key Takeaways

### Training Performance
- **ImageNet pretrained** achieves higher final mAP (~50% vs ~36%)
- **Pretrained** converges in fewer epochs
- Both models show stable, smooth training curves

### Inference Performance
- **Identical** for both models (~4.5ms per image, ~230 FPS)
- Same architecture = same inference speed
- GPU memory usage: ~24GB (batch processing)

### Transfer Learning Benefit
The ImageNet pretrained weights provide:
- Faster convergence (reaches milestones sooner)
- Better final performance (+14% mAP)
- More stable early training

---

## 📊 Generated Visualizations

All analysis notebooks generate high-quality plots saved as PNG files:
- `detailed_training_comparison.png` - 9-panel training metrics
- `convergence_comparison.png` - Speed to milestones
- `inference_efficiency.png` - Latency and throughput
- `diverse_predictions.png` - Multi-class detection examples
- `all_classes_predictions.png` - All 20 VOC classes

Run the notebooks to regenerate these with embedded outputs.
