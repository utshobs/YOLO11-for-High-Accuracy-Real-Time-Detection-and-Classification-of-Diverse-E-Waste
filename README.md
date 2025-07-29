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
├── yolov11/                   # YOLOv11 model and source code
├── train.py                   # Training script
├── detect.py                  # Inference script
├── runs/                      # Saved training outputs
├── requirements.txt           # Python dependencies
└── README.md
```

---

## 🚀 Getting Started (Google Colab Recommended)

Follow the steps below to train the YOLOv11 model on your dataset using Google Colab.

---

### 1️⃣ Clone the Repository

```bash
!git clone https://github.com/your-username/yolov11-ewaste-detection.git
%cd yolov11-ewaste-detection
```

---

### 2️⃣ Install Dependencies

```bash
!pip install -r requirements.txt
```

Make sure to install essential packages like `torch`, `opencv-python`, `matplotlib`, etc.

---

### 3️⃣ Prepare Dataset

Ensure your datasets (`Dataset_1` and `Dataset_2`) follow the YOLO format:

```
Dataset_1/
├── train/
│   ├── images/
│   └── labels/
├── val/
│   ├── images/
│   └── labels/
```

Each image must have a corresponding `.txt` label file in the `labels/` folder.

---

### 4️⃣ Train the Model

Use the command below to train on `Dataset_1`:

```bash
!python train.py --img 640 --batch 16 --epochs 100 --data dataset1.yaml --weights yolov11.pt --name yolo11_dataset1
```

To train on `Dataset_2`, update the `--data` flag:

```bash
!python train.py --img 640 --batch 16 --epochs 100 --data dataset2.yaml --weights yolov11.pt --name yolo11_dataset2
```

---

### 5️⃣ Monitor Training (Optional)

```python
%load_ext tensorboard
%tensorboard --logdir runs/train
```

This command launches TensorBoard in Colab to visualize training metrics.

---

### 6️⃣ Export Trained Model

After training, copy the best model weights for future inference:

```bash
!cp runs/train/yolo11_dataset1/weights/best.pt /content/
```

---

### 7️⃣ Run Inference

Use the trained model to detect e-waste objects in new images:

```bash
!python detect.py --weights best.pt --img 640 --source path/to/image.jpg
```

To test on a folder of images:

```bash
!python detect.py --weights best.pt --img 640 --source path/to/folder/
```

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


