
# 🚜 AgTech: Weed Detection with YOLOv11 Vs Computer Vision:
Comparative analysis of Classical Computer Vision vs. Deep Learning (YOLOv11-Medium) for real-time weed detection in precision agriculture.

## Problem Overview
- Weed–crop separation is a key challenge in precision agriculture
- Sugar beet fields present high visual similarity between crops and weeds
- Accurate segmentation enables site-specific spraying and yield optimization

## 📌 About The Project
An automated system for identifying **Sugar Beets vs. Weeds** in agricultural fields.
We compared two methods to find the best and most efficient solution  :
1.  **Classical Computer Vision:** Using color indices (ExG) , Erosion and Dilation,  and Otsu thresholding.
2.  **Deep Learning (AI):** Using **YOLOv11-Meduim Segmentation** for high precision.


## Dataset

## 📂 Dataset
We utilize the **Amiran / Lincoln Beet Dataset** (via Kaggle) to simulate real-world precision agriculture tasks.

* **Scale:** 4,402 RGB images captured in outdoor field conditions.
* **Resolution:** High-definition (typically 1920×1080).
* **Classes:** `Sugar Beet` (Crop) vs. `Weed`.
* **Preprocessing:** Since raw pixel-level masks were unavailable, original bounding box annotations were converted into **rectangular polygons** to enable segmentation training.
* **Key Challenge:** High visual similarity between crops and weeds under variable lighting.
* **Usage:** Serves as the benchmark for comparing our Classical CV approach vs. YOLOv11 segmentation.

## Methodology
### Classical Segmentation Approach
- Vegetation enhancement using Excess Green index  
- Automatic thresholding (Otsu)  
- Morphological noise removal  
- Object extraction via contour analysis  

### Deep Learning Approach (YOLO Segmentation)
**Stage A** — Baseline (YOLO Nano): Trained YOLO11n-seg for 50 epochs on raw data (no balancing) → mAP50 = 0.56.

Failure analysis: Model detected only Weed and ignored Sugar Beet due to an XML→YOLO class-mapping mismatch, effectively training on one class.

**Stage B** — Fixed + Rebalanced (YOLO Medium): Fixed conversion script + rebalance to ~40:60 → trained YOLO11m-seg for up to 100 epochs with early stopping → mAP50 = 0.734.

Observation: Training stopped at epoch 27 (low patience), suggesting mild underfitting and need for stronger regularization/augmentation.

**Stage C** — Final Optimized (YOLO Large): Trained YOLO11l-seg with 960×960 input resolution + geometric augmentations → best performance: mAP50 = 0.782, Precision = 0.794.

Generalization: Very small train–val gap (~0.39%), indicating strong stability and no clear overfitting.
 
##  Key Results
* **Winner:** YOLOv11 model achieved superior accuracy and robustness to lighting conditions.
* **Performance:** Optimized for T4 GPU, achieving real-time inference speeds.
<img width="724" height="491" alt="image" src="https://github.com/user-attachments/assets/f401993c-01ef-4c35-babf-5422836b9bac" />

## Visual Examples (more in assets) 
YOLO - Large Final Model: 
<img width="656" height="410" alt="image" src="https://github.com/user-attachments/assets/e1fea041-7d61-4640-98fd-0ef0c075b81f" />

CLassic Methods : 
<img width="623" height="410" alt="image" src="https://github.com/user-attachments/assets/f7faf2ac-79b1-4520-be76-9ed3aadd10da" />


##  Project Structure
* `notebooks/` - The complete code (Data prep, Training, Evaluation).
* `results/` - Graphs and visualized predictions.

##  How to Run
1.  Clone the repo.
2.  Install requirements: `pip install -r requirements.txt`
3.  Run the notebooks in Google Colab.
