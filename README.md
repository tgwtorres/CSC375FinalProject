# Faster R-CNN on COCO 2017: Reproducibility & Evaluation

## Project Overview

This project evaluates the performance of the Faster R-CNN model with a ResNet-50-FPN backbone, pretrained on COCO 2014, on the COCO 2017 validation dataset. The primary goals were to:

* Reproduce inference performance using a pretrained model.
* Test generalization of the model to a newer dataset (COCO 2017).

---

## Dataset

* **Name:** MS COCO 2017 (Validation Set)
* **Images:** 5,000
* **Classes:** 80 object categories
* **Annotations:** `instances_val2017.json`

Directory structure:

```
Final_Project/
 ├── dataset/
     ├── val2017/                # COCO val2017 images
     └── annotations/
           └── instances_val2017.json
```

---

## Model Setup

* **Architecture:** Faster R-CNN with ResNet-50 FPN
* **Source:** `torchvision.models.detection`
* **Inference device:** CUDA if available, otherwise CPU
* **Transform:** `ToTensor()` from `torchvision.transforms`

---

## Inference & Evaluation

* Ran inference on all 5,000 validation images.
* Filtered predictions with confidence threshold > 0.05.
* Used `pycocotools` for mAP and AP computation.

### Key Results:

* **mAP@\[0.50:0.95]:** 0.370
* **AP\@0.50:** 0.585
* **AP by object size:**

  * Small: 0.211
  * Medium: 0.403
  * Large: 0.482
* **Inference Time (100 samples):**

  * Average: 0.0575s/image
  * Median: 0.0588s

---

## Visualization

* Confidence score histogram of all predictions
* Top-20 classes by AP (bar chart)

---

## How to Run

```bash
pip install torch torchvision pycocotools matplotlib opencv-python tqdm ultralytics
```

### Run Inference & Evaluation

```python
# Load dataset and model
# Run prediction loop
# Save predictions as coco_predictions.json
# Evaluate with pycocotools
```

---

## Contributors

* Jesse Gao
* Boyuan Pan
* Christopher Tang
* Isaias Bahena

## License

This project uses open datasets and pretrained models provided by PyTorch and MS COCO under their respective licenses.
