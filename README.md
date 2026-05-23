# Image Classification Project

A deep learning project for classifying natural scene images into 6 categories, built as a submission for Dicoding's Machine Learning course.

## Dataset

**Intel Image Classification** from Kaggle (~17,034 images)

| Class | Count |
|-------|-------|
| Buildings | 2,628 |
| Forest | 2,745 |
| Glacier | 2,957 |
| Mountain | 3,037 |
| Sea | 2,784 |
| Street | 2,883 |

### Data Split

| Set | Images |
|-----|--------|
| Train | 9,541 |
| Validation | 509 |
| Test | 2,555 |

## Model Architecture

Custom CNN with 4 convolutional blocks:

```
Input (150x150x3)
├── Conv2D(32) → BatchNorm → MaxPool
├── Conv2D(64) → BatchNorm → Conv2D(64) → BatchNorm → MaxPool → Dropout(0.25)
├── Conv2D(128) → BatchNorm → Conv2D(128) → BatchNorm → MaxPool → Dropout(0.25)
├── Conv2D(256) → BatchNorm → MaxPool → Dropout(0.3)
├── Flatten
├── Dense(512) → Dropout(0.5)
├── Dense(256) → Dropout(0.3)
└── Dense(6, softmax)
```

- **Total parameters:** ~11.3M
- **Optimizer:** Adam (lr=1e-3)
- **Loss:** Categorical Crossentropy

## Data Augmentation

Applied to training data:
- Rescale: 1./255
- Rotation: ±20°
- Width/Height shift: ±20%
- Shear: 0.15
- Zoom: ±20%
- Horizontal flip: True
- Fill mode: nearest

## Results

| Metric | Value |
|--------|-------|
| Test Accuracy | **88.73%** |
| Test Loss | 0.2981 |

## Exported Models

| Format | Location |
|--------|----------|
| SavedModel | `saved_model/` |
| TensorFlow Lite | `tflite/model.tflite` |
| TensorFlow.js | `tfjs_model/` |

## Setup

```bash
pip install -r requirements.txt
```

## Usage

Open `notebook.ipynb` in Jupyter to:
1. Load and preprocess the dataset
2. Train the model
3. Evaluate performance
4. Export to different formats

## Author

- **Name:** Jennifer Khang
- **Email:** jenniferkhang07@gmail.com