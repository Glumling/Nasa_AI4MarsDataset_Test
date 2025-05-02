
---

### 🗂 docs/PROJECT_JOURNAL.md

```markdown
# Project Journal

## Week 1 (May 25–31)  
- **Goal:** choose track & problem.  
- **Action:** Reviewed MSL terrain dataset; decided on semantic segmentation (Implementation).  
- **Struggles:** none—planning phase.

## Week 2 (April 1–7)  
- **Dataset prep:** wrote `get_pairs()` for image↔mask, handled missing files.  
- **Initial pipeline:** tried HuggingFace SegFormer → multiple TF errors (mismatched sizes, `_distribute_strategy` attribute, shape mismatches).  
- **Fix:** abandoned TF→PyTorch TF conversion; pivot → `segmentation_models_pytorch` U-Net.

## Week 3 (April 8–14)  
- **U-Net build:** integrated `smp.Unet` with EfficientNet-B0 encoder.  
- **Augmentations:** used Albumentations; encountered missing transforms (`Flip`, `Cutout`) → switched to `A.HorizontalFlip`, `A.Affine`, etc.  
- **Training:** initial run on full 13 000 images too slow; memory issues.  
- **Solution:** subsample 3 000 images, 80/20 train/val split.

## Week 4 (April 15–21)  
- **Hyperparam tuning:**  
  - LR: 1e-4, AdamW → stable convergence  
  - Batch=4 → fits in 16 GB GPU  
  - Augment strength → +5 % IoU  
- **Results:**  
  - Val loss plateau ~0.14  
  - Mean IoU ≈ 0.85 on held‐out  
- **Validation:** ran inference, visual checks look correct.

## Week 5 (April 22–28)  
- **Documentation:** wrote `TECHNICAL_REPORT.md`, `TESTING_PLAN.md`.  
- **Packaging:** scripted via TorchScript for light deployment.  
- **Inference UI:** updated `inference.py` to pick random images each run.  
- **Presentation:** outlined slides.

---

### Key Challenges & Fixes

1. **TFSegFormer weight mismatches**  
   → Switched to PyTorch SMP Unet.

2. **Albumentations API changes**  
   → Updated transforms to new names (`Affine` vs `ShiftScaleRotate`).

3. **OOM on full dataset**  
   → Subsampling to 3 000 images.

4. **Lack of accuracy metric in logs**  
   → Added IoU and pixel‐accuracy prints in `train.py`.

5. **Empty inference sample set**  
   → Now randomly sample `--n_samples` from `data/images`.

---

_End of journal._
