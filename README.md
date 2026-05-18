# ORCA-G4 Lesion Detection

YOLO11-based oral lesion detection and crop generation pipeline for **ORCA-G4**.

The detector identifies potential lesion regions and prepares localized crops for downstream vision-language screening.

## Results

| Metric | Result |
|---|---:|
| Source images | 273 |
| Train / Val / Test | 182 / 44 / 47 |
| Lesion crops | 362 |
| Crop size | 224 × 224 |
| Best Precision | 0.660 |
| Best Recall | 0.438 |
| Best mAP@50 | 0.456 |
| Best mAP@50-95 | 0.193 |
| Model | YOLO11n |
| Parameters | 2.59M |
| Compute | 6.4 GFLOPs |

## Pipeline

```text
Oral Image
    ↓
YOLO11 Lesion Detection
    ↓
Bounding Box
    ↓
Expanded Lesion Crop
    ↓
224 × 224 Crop
    ↓
Gemma-ready Dataset
```

## Experiments

| Model | Precision | Recall | mAP@50 | mAP@50-95 |
|---|---:|---:|---:|---:|
| YOLO11n | 0.660 | 0.417 | 0.456 | 0.193 |
| YOLO11n Recall-focused | 0.386 | 0.438 | 0.322 | 0.142 |
| YOLO11s | 0.392 | 0.416 | 0.322 | 0.119 |

## Dataset

The source dataset is kept outside this repository.

[Dataset](https://drive.google.com/drive/folders/1djOpM8rawJktyCx6yITQ2vU-JRZxRwsK?usp=sharing)

## Notebook

`train_oral_lesion_detector.ipynb`

The notebook contains the complete workflow for:

- Dataset preparation
- YOLO11 training
- Model evaluation
- Lesion detection
- Bounding-box expansion
- Lesion crop generation
- Label propagation
- Gemma-ready dataset generation

## Important

The YOLO model **detects lesion regions only**. It does not diagnose oral cancer.

The clinical categories are inherited from the source dataset and are used for downstream screening and referral experiments.

## Project

Built as part of **ORCA-G4** for the **Gemma 4 Good Hackathon**.

[ORCA-G4 Kaggle Writeup](https://www.kaggle.com/competitions/gemma-4-good-hackathon/writeups/orca-g4)