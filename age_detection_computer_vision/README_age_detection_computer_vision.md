# Age Detection — Computer Vision

A computer vision project that predicts a person's age from facial photographs using transfer learning with **ResNet50**. Built for Good Seed Supermarket to help verify customer age for age-restricted products, without requiring staff intervention.

---

## Project Overview

The goal is to train a regression model on a dataset of labeled facial images to predict real age. The project success criterion was achieving a **Mean Absolute Error (MAE) of 8 or below** on the test set.

---

## Dataset

7,600+ facial photographs with corresponding age labels, stored in `/datasets/faces/`.

| File | Description |
|---|---|
| `final_files/` | Folder of facial images |
| `labels.csv` | Maps each image filename to the subject's real age |

The age distribution is skewed toward younger ages with a long tail toward older individuals.

---

## Model Architecture

Transfer learning using **ResNet50** pretrained on ImageNet as the feature extractor, with a custom regression head:

- ResNet50 base (frozen weights)
- GlobalAveragePooling2D
- Dense(128, ReLU)
- Dropout(0.5)
- Dense(1) — regression output

**Optimizer:** Adam (lr=0.0001) | **Loss:** MSE | **Metric:** MAE

---

## Training Results

Trained for 20 epochs on GPU:

| Metric | Start (Epoch 1) | End (Epoch 20) |
|---|---|---|
| Training MAE | 7.43 | 3.17 |
| Training Loss | 95.35 | ~17 |
| Validation MAE | 8.49 | ~6.7 |

**Final MAE is below the 8.0 threshold — project requirement met.**

---

## Key Takeaways

- **Training improves consistently** — MAE drops from 7.43 to 3.17, confirming the model is learning strong internal representations
- **Validation performance is less smooth** — a mid-training spike at epoch 12 (MAE 11.46) indicates instability; best generalization occurs around epoch 17
- **Overfitting is visible** — training MAE continues falling while validation MAE fluctuates and eventually rises, a classic sign of overfitting to dataset-specific patterns
- **ResNet50 transfer learning** proved highly effective for this regression task, extracting rich facial features without training from scratch

---

## Tech Stack

- **Python 3**
- **TensorFlow / Keras** — model building, training, ImageDataGenerator
- **ResNet50** — pretrained CNN backbone (ImageNet weights)
- **Pandas / NumPy** — data handling
- **Matplotlib** — EDA visualizations

---

## How to Run

1. Clone the repository
2. Install dependencies:
   ```bash
   pip install tensorflow pandas numpy matplotlib
   ```
3. Place the dataset in `/datasets/faces/` (or update the path in the notebook)
4. Open and run `age_detection_computer_vision.ipynb` in Jupyter Notebook or JupyterLab

> **Note:** Model training is computationally intensive. A GPU environment is strongly recommended.

---

## Project Structure

```
.
├── age_detection_computer_vision.ipynb   # Main project notebook
└── README.md                             # Project documentation
```

---

## Concepts Demonstrated

- Transfer learning with pretrained CNNs (ResNet50)
- Image data augmentation with ImageDataGenerator
- Regression with deep learning (age prediction)
- MAE evaluation for continuous targets
- Overfitting detection and analysis
- GPU-based model training pipeline
