Perfect! I’ve created a **professional, ready-to-use README** for your project. You can **copy-paste this entirely**, then update the dataset link or sample image path if needed.

---

# Pedestrian Detection and Counting using YOLOv8

##  Project Overview

This project implements a **Pedestrian Detection and Counting system** using **YOLOv8**. The model detects pedestrians in images and provides both the **bounding boxes** and **counts** of people per image.

The goal is to create a **high-accuracy, fast object detection pipeline** for pedestrian monitoring applications.

---

## 📁 Folder Structure

```
Pedestrian-Detection-Project/
│
├─ train/                  # Training images
├─ valid/                  # Validation images
├─ test/                   # Test images
├─ test_predictions/       # YOLOv8 predictions on test images
├─ training_results/       # Model weights and training logs
├─ validation_results/     # Validation logs and metrics
├─ data.yaml               # YOLOv8 dataset configuration
└─ README.md               # Project documentation
```

---

## 📚 Dataset

This project uses a custom **Pedestrian Detection Dataset** stored on Google Drive:
🔗 [Download Dataset](https://drive.google.com/drive/folders/1NS1wg9jfxFDVdKnvBvbNMHr_Ucd-aKBo?usp=drive_link).


---

## 🛠️ How to Run

### 1️⃣ Install Requirements

```bash
pip install ultralytics==8.4.14
```

### 2️⃣ Train YOLOv8 Model

```bash
!yolo task=detect mode=train model=yolov8n.pt \
data="/content/drive/MyDrive/Pedestrian Detection Dataset/data.yaml" \
epochs=50 imgsz=640 \
project="/content/drive/MyDrive/Pedestrian Detection Dataset" \
name="training_results"
```

### 3️⃣ Validate Model

```bash
!yolo task=detect mode=val \
model="/content/drive/MyDrive/Pedestrian Detection Dataset/training_results/weights/best.pt" \
data="/content/drive/MyDrive/Pedestrian Detection Dataset/data.yaml" \
project="/content/drive/MyDrive/Pedestrian Detection Dataset" \
name="validation_results"
```

### 4️⃣ Predict on Test Images

```bash
!yolo task=detect mode=predict \
model="/content/drive/MyDrive/Pedestrian Detection Dataset/training_results/weights/best.pt" \
source="/content/drive/MyDrive/Pedestrian Detection Dataset/test" \
project="/content/drive/MyDrive/Pedestrian Detection Dataset" \
name="test_predictions"
```

---

## 📊 Metrics

After training and validation, the model achieves metrics such as:

| Metric    | Value |
| --------- | ----- |
| Precision | 0.75  |
| Recall    | 0.45  |
| mAP50     | 0.63  |
| mAP50-95  | 0.45  |

> Metrics may vary depending on training conditions.

---

## 🔧 Requirements

* Python 3.12+
* PyTorch 2.9+
* Ultralytics YOLOv8 (v8.4.14)
* GPU recommended (Tesla T4 or equivalent)

---

## ⚡ Notes

* All predictions and validation results are saved in the corresponding folders (`training_results`, `validation_results`, `test_predictions`).
* Ensure that your dataset is in the correct folder structure before training.
* The project is designed for **fast pedestrian detection**, even on smaller images (320x640 or 640x640).
