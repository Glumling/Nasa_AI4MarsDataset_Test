# Technical Report

## 1. Dataset  
- **Source:** AI4Mars MSL (Curiosity Rover)  
- **Images:** EDR (Enhanced debayered raw) format, various exposures  
- **Masks:** pixel‐wise labels (0–3, four classes)

## 2. Preprocessing & Augmentation  
- Resize to 256×256  
- Random horizontal flip (0.5), 90° rotations (0.5)  
- Affine: rotate ±15°, scale 0.9–1.1 (0.5)  
- Brightness/contrast jitter (0.5)  
- Normalize to ImageNet stats

## 3. Model Architecture  
- **Backbone:** EfficientNet-B0 (imagenet weights)  
- **Decoder:** U-Net style skip connections  
- **Head:** 1×1 conv → NUM_CLASSES logits  
- ~5 M parameters

## 4. Training  
- **Loss:** Cross-entropy (ignore void=255)  
- **Optimizer:** AdamW, lr = 1e-4, weight decay = 1e-2  
- **Batch size:** 4  
- **Epochs:** 20  
- **Subsample:** 3 000 training images → 2 400 train / 600 val  
- **Hardware:** Tesla T4 16 GB

## 5. Results  
| Metric       | Train | Val  |
|-------------:|------:|-----:|
| Loss         | 0.17  | 0.14 |
| Mean IoU     | 0.88  | 0.85 |
| Pixel acc.   | 0.92  | 0.90 |

### Qualitative  
![example_inference](../slides/example_inference.png)

## 6. Deployment  
- Scripted to TorchScript (`torch.jit.script`)  
- CLI tool `inference.py` picks random images, visualizes.

## 7. Future Work  
- Add focal/dice loss  
- Larger backbone (Eff-B3)  
- Real‐time inference on edge device

