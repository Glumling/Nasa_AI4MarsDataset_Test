# Testing Plan

## 1. Unit Tests  
- **utils.get_pairs**: mask/image matching  
- **MarsDataset**: length, shape, dtype  
- **augmentation pipeline**: deterministic seed test  

## 2. Integration Tests  
- **train.py** dry‐run 1 epoch, 10 samples → checkpoint saved  
- **inference.py** on 3 known images → output masks shapes match, display invoked  

## 3. Manual Tests  
- Random seeds reproducibility (with `--seed`)  
- Visual inspection on edge cases (pure sand, big rock)  

## 4. CI Integration (optional)  
- GitHub Actions: run `pytest` on push & PR  
- Linting via `flake8`
