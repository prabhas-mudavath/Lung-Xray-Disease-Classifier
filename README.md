
# Lung-Xray-Disease-Classifier


Lung disease segmentation and classification using UNeXt and MobileNetV2 on PadChest X-rays. Manually created lung masks from Roboflow improve accuracy and explainability by focusing the classifier on precise lung regions instead of full chest images.
#  Lung Disease Segmentation and Classification using UNeXt & MobileNetV2 (PadChest Dataset)
## Dataset
The PadChest dataset and manually annotated lung masks are not included
in this repository due to size constraints.

They were used only for academic research purposes during the internship.

##  Overview
This project focuses on improving **lung disease detection** in chest X-rays by combining **manual lung segmentation** with **MobileNetV2-based classification**.  
Instead of relying on automated segmentation models, precise lung masks are **manually created in Roboflow**, ensuring accurate lung boundaries. These masks are applied directly to the chest X-rays, removing irrelevant background (ribs, heart, etc.) and keeping only the lung regions for classification.

The masked lung images are then used to train a **MobileNetV2** classifier that distinguishes between **Normal** and **Diseased** cases, improving both accuracy and interpretability.

---

## Objectives
- Enhance disease classification accuracy by focusing on the lung region only.  
- Use **manual segmentation** to eliminate errors common in automated masks.  
- Improve **explainability** and **robustness** of predictions.  
- Compare manual segmentation with **UNeXt**-based automated segmentation.

---

## Models Used
| Task | Model | Description |
|------|--------|-------------|
| Segmentation | **UNeXt** | Benchmark segmentation model trained for comparison |
| Classification | **MobileNetV2** | Lightweight CNN for Normal/Diseased classification |

---

##  Dataset
- **Source:** [PadChest Dataset](https://bimcv.cipf.es/bimcv-projects/padchest/)  
- **Total Images:** 4,556 grayscale chest X-rays (.jpg format)  
- **Masks:** Binary lung masks (.png) manually annotated using Roboflow  
- **Input Size:** 224 × 224  
- **Classes:** `Normal`, `Diseased`

---

##  Workflow
1. **Manual Masking:** Create accurate binary lung masks in Roboflow.  
2. **Mask Application:** Multiply X-ray by mask to isolate lung regions.  
3. **Segmentation Evaluation:** Train UNeXt to measure segmentation quality (optional).  
4. **Classification:** Train MobileNetV2 on masked images.  
5. **Evaluation:** Assess model with accuracy, Dice, and Mean IoU metrics.

---

##  Model Performance

###  Segmentation (UNeXt)
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

##  Classification (MobileNetV2)
- **Input:** Masked lung X-rays (224×224)  
- **Output:** Normal / Diseased  
- **Loss:** Binary Crossentropy  
- **Optimizer:** Adam  
- **Metrics:** Accuracy, Precision, Recall, F1-Score
