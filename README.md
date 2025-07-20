# MV-RSD YOLO: Object Detection on Military Vehicles Dataset

A professional deep learning project for training and evaluating object detection models on the **MV-RSD (Military Vehicle Remote Sensing Dataset)** using **YOLOv8n** and **YOLOv12m** architectures.

---

## 🚀 Overview

This repository contains all resources and results related to training YOLO models for object detection on satellite images of military vehicles. The goal is to detect and classify five classes of vehicles in low-resolution aerial images.

- Dataset: [MV-RSD Dataset](https://scidb.ai) *(downloaded from SciDB)*
- Models trained:
  - `YOLOv8n` (lightweight baseline)
  - `YOLOv12m` (mid-weight architecture for better performance)

---

## 🧠 Project Highlights

| Model    | Box Precision | Recall | mAP\@0.5 | mAP\@0.5:0.95 |
| -------- | ------------- | ------ | -------- | ------------- |
| YOLOv8n  | 0.879         | 0.79   | 0.877    | 0.614         |
| YOLOv12m | 0.871         | 0.831  | 0.883    | 0.620         |

*Trained with batch size 10, img size 640, 50 epochs.*

---




## 🏋️‍♂️ Training Instructions

```bash
# Train YOLOv8n
yolo detect train \
  data=data.yaml \
  model=yolov8n.pt \
  epochs=50 \
  imgsz=640 \
  batch=16 \
  project=results \
  name=8n_exp1

# Train YOLOv12m
yolo detect train \
  data=data.yaml \
  model=yolo12m.pt \
  epochs=50 \
  imgsz=640 \
  batch=10 \
  cache=True \
  project=results \
  name=12m_exp15
```

---

## 🔍 Validation Command

```bash
# Evaluate a trained model
yolo detect val \
  model=results/12m_exp15/weights/best.pt \
  data=data.yaml
```

---

## 📷 Example Results

YOLO12M
![Training Curves](results/12m_exp15/results.png)
![Confusion Matrix](results/12m_exp15/confusion_matrix.png)

<img src="results\12m_exp15\val_batch1_labels.jpg" width="400"/> <img src="results\12m_exp15\val_batch1_pred.jpg" width="400"/>


YOLOV8n
![Training Curves](results/train5/results.png)
![Confusion Matrix](results/train5/confusion_matrix.png)

<img src="results\train5\val_batch1_labels.jpg" width="400"/> <img src="results\train5\val_batch1_pred.jpg" width="400"/>


> 🔎 Class-wise mAPs:
>
> - LMV: 0.656
> - SMV: 0.658
> - MCV: 0.635
> - CV: 0.735
> - AFV: 0.416

---

## 🛠 Requirements

- Python 3.10+
- PyTorch 2.0+
- CUDA GPU (4GB VRAM minimum)

Install dependencies (recommended inside a virtual environment):

```bash
pip install -r requirements.txt
```

---

## ⚖️ License

This project is released under the MIT License. You are free to use, modify, and distribute.

---

## 🙋‍♂️ Author

**Yusuf Soylemez**\
Aspired AI Engineer | Passionate about computer vision, real-time systems, and ML pipelines.

---

## 📌 Notes

- This project is part of a professional portfolio demonstrating end-to-end ML model development.
- Data source acknowledged: SciDB
- Long training times due to hardware limitations (YOLOv12m took \~50 hours on RTX 3050 Ti)

---

## ⭐ Contributing

Feel free to fork this repo, submit issues or pull requests!

