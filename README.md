# Lung-Xray-Disease-Classifier
Lung disease segmentation and classification using UNeXt and MobileNetV2 on PadChest X-rays. Manually created lung masks from Roboflow improve accuracy and explainability by focusing the classifier on precise lung regions instead of full chest images.
# 🩻 Lung Disease Segmentation and Classification using UNeXt & MobileNetV2 (PadChest Dataset)

## 📘 Overview
This project focuses on improving **lung disease detection** in chest X-rays by combining **manual lung segmentation** with **MobileNetV2-based classification**.  
Instead of relying on automated segmentation models, precise lung masks are **manually created in Roboflow**, ensuring accurate lung boundaries. These masks are applied directly to the chest X-rays, removing irrelevant background (ribs, heart, etc.) and keeping only the lung regions for classification.

The masked lung images are then used to train a **MobileNetV2** classifier that distinguishes between **Normal** and **Diseased** cases, improving both accuracy and interpretability.

---

## 🎯 Objectives
- Enhance disease classification accuracy by focusing on the lung region only.  
- Use **manual segmentation** to eliminate errors common in automated masks.  
- Improve **explainability** and **robustness** of predictions.  
- Compare manual segmentation with **UNeXt**-based automated segmentation.

---

## 🧠 Models Used
| Task | Model | Description |
|------|--------|-------------|
| Segmentation | **UNeXt** | Benchmark segmentation model trained for comparison |
| Classification | **MobileNetV2** | Lightweight CNN for Normal/Diseased classification |

---

## 🩺 Dataset
- **Source:** [PadChest Dataset](https://bimcv.cipf.es/bimcv-projects/padchest/)  
- **Total Images:** 4,556 grayscale chest X-rays (.jpg format)  
- **Masks:** Binary lung masks (.png) manually annotated using Roboflow  
- **Input Size:** 224 × 224  
- **Classes:** `Normal`, `Diseased`

---

## ⚙️ Workflow
1. **Manual Masking:** Create accurate binary lung masks in Roboflow.  
2. **Mask Application:** Multiply X-ray by mask to isolate lung regions.  
3. **Segmentation Evaluation:** Train UNeXt to measure segmentation quality (optional).  
4. **Classification:** Train MobileNetV2 on masked images.  
5. **Evaluation:** Assess model with accuracy, Dice, and Mean IoU metrics.

---

## 🧮 Model Performance

### 🫁 Segmentation (UNeXt)
| Metric | Train | Validation |
|--------|--------|------------|
| Accuracy | 97.53% | 96.93% |
| Dice Coefficient | 93.46 | 92.57 |
| Mean IoU | 36.03 | 36.01 |
| Loss | 0.0617 | 0.0814 |

**Optimizer:** Adam  
**Loss:** Binary Crossentropy  
**Learning Rate:** 5e-4  
**Early Stopping:** 12 epochs

---

## 🔍 Classification (MobileNetV2)
- **Input:** Masked lung X-rays (224×224)  
- **Output:** Normal / Diseased  
- **Loss:** Binary Crossentropy  
- **Optimizer:** Adam  
- **Metrics:** Accuracy, Precision, Recall, F1-Score  

---

## 📂 Repository Structure
LungXray-Disease-Classifier/
│
├── README.md                  # Project overview, setup, usage
├── requirements.txt           # Python dependencies
├── .gitignore                 # Ignore model weights, temp files, etc.
│
├── data/
│   ├── raw_images/            # Original PadChest X-rays (.jpg)
│   ├── lung_masks/            # Binary lung masks (.png) from Roboflow
│   ├── masked_images/         # X-rays with lungs segmented
│   ├── train/                 # Training set (masked images + labels)
│   ├── valid/                 # Validation set
│   └── test/                  # Test set
│
├── notebooks/
│   ├── 01_segmentation_unext.ipynb     # UNeXt segmentation (optional)
│   └── 02_classification_mobilenet.ipynb # MobileNetV2 training
│
├── models/
│   ├── unext_test_model.h5             # UNeXt model weights
│   ├── mobilenet_binary.tflite         # MobileNetV2 (TFLite format)
│   ├── convert_binary_best.keras       # Keras format
│   └── best_convert_binary.h5          # Best model checkpoint
│
├── src/
│   ├── preprocess.py          # Resize, mask, crop lungs
│   ├── train_classifier.py    # MobileNetV2 training script
│   ├── evaluate.py            # Accuracy, Dice, IoU metrics
│   └── utils.py               # Helper functions (e.g., loaders, metrics)
│
├── outputs/
│   ├── predictions.csv        # Model predictions
│   ├── accuracy_curve.png     # Training accuracy plot
│   ├── loss_curve.png         # Training loss plot
│   ├── gradcam_exports/       # Grad-CAM visualizations
│   └── feature_maps/          # Intermediate feature maps
│
├── results_export/            # Final results, metrics, confusion matrix
├── plots/                     # Additional visualizations
├── test/                      # Test images and predictions
├── valid/                     # Validation images
├── train/                     # Training images
└── .ipynb_checkpoints/        # Auto-generated Jupyter checkpoints


🧑‍💻 Author
Mudavath Prabhas
Deep Learning & Medical Imaging Research
📧 mudavathprabhas789@gmail.com


⭐ If you find this repository helpful, please consider giving it a star!
