# Nasa_AI4MarsDataset_Test
This is my take for the ai4mars dataset, it is a model that you train, after training, there are deployment scripts that you can look and play around with it, marking the prototype a success.

# FP_GROUP01_Rayyaan_Haamid_ITAI2372

**Team member:**  
- Rayyaan Haamid

**Track:**  
Implementation Track

**Problem:**  
Terrain‐aware autonomous navigation via semantic segmentation of NASA’s AI4Mars MSL dataset.

---

## Project Description  
We build and train a lightweight U-Net (EfficientNet‐B0 backbone) to segment Mars rover imagery into 4 classes: sand, bedrock, soil, big rock. We subsample 3 000 images for fast iteration, augment heavily, and achieve ~0.85 mean IoU on held‐out validation.

---

## Repo Contents

- **train.py:** end‐to‐end training script  
- **inference.py:** load a checkpoint, run on random test images, visualize results  
- **utils.py:** data‐loading, augmentation, metric functions  
- **requirements.txt:** pip dependencies  
- **docs/**  
  - `TECHNICAL_REPORT.md` – architecture, data, training details  
  - `PROJECT_JOURNAL.md` – daily/weekly development log, challenges & fixes  
  - `TESTING_PLAN.md` – unit, integration, manual test cases  
- **slides/** – presentation outline

---

## Setup

1. Clone repo:  
   ```bash
   git clone https://github.com/your-org/FP_GROUP01_Rayyaan_Haamid_ITAI2372.git
   cd FP_GROUP01_Rayyaan_Haamid_ITAI2372
