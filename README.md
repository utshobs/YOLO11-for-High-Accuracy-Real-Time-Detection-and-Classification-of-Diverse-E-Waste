# YOLO11 for High Accuracy Real-Time Detection and Classification of Diverse E-Waste

This repository contains the implementation and training pipeline for an e-waste classification and detection model using **YOLOv11**, with two pre-structured datasets: `Dataset_1` and `Dataset_2`. The model is trained and evaluated using **Google Colab**.

---

## 📁 Project Structure

```
├── Dataset_1/
│   ├── train/
│   └── val/
├── Dataset_2/
│   ├── train/
│   └── val/                
├── train.py                                                           
└── README.md


---

## 🚀 Getting Started (Google Colab)

Follow the steps below to train the YOLOv11 model on your dataset using Google Colab.

---

### 1️⃣ Clone the Repository

```bash
!git clone https://github.com/your-username/yolov11-ewaste-detection.git
```

---

### 2️⃣ Install Dependencies

```bash
!pip install ultralytics
```
---

### 3️⃣ Prepare Dataset

Ensure your datasets (`Dataset_1`) follow the YOLO format for detection:

```
Dataset_1/
├── train/
│   ├── images/
│   └── labels/
├── val/
│   ├── images/
│   └── labels/
├── data.yaml 
```

Each image must have a corresponding `.txt` label file in the `labels/` folder.
Ensure the train and val split from `Dataset_1` according to your need.

---

### 4️⃣ Train the Model

Use the command below to train on `Dataset_1`:

```bash
!yolo detect train data=/content/E-waste-1/data.yaml model=yolo11s.pt epochs=50 imgsz=640
```

To train on `Dataset_2`:

```bash
!python train.py --img 640 --batch 16 --epochs 100 --data dataset2.yaml --weights yolov11.pt --name yolo11_dataset2
```

---

### 5️⃣ Export Trained Model

After training, download the best model weights for future inference:

```bash
!zip -r /content/runs.zip /content/runs/
```

Then download the runs.zip folder. This folder includes all the training results files and the best trained model.
---



## 📌 Notes

- Images in `Dataset_1` were resized to **640×640** using **Roboflow**.
- `Dataset_2` uses YOLOv11's **default image preprocessing** pipeline.
- Label files follow standard YOLO format:  
  `class_id x_center y_center width height` (all values normalized to [0, 1]).

---

## 🔬 Future Work

To enhance model robustness and generalization, future directions include:

- **Multi-modal learning**: combining images with sensor data, metadata, or text.
- **Evaluation on external noisy datasets** to test real-world performance.
- **Model optimization**: applying quantization and pruning for mobile/edge deployment.

---

## 🧠 Research Objective

This work focuses on leveraging YOLOv11 for practical and efficient e-waste detection, with a goal to support automated smart waste management systems through real-time object classification and recognition.

---

## 📬 Contact

For questions or collaboration:

**Utshob Sutradhar**  
📧 utshob@email.com 


