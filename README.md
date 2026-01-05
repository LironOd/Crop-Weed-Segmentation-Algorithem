
# 🚜 AgTech: Weed Detection with YOLOv11 Vs Computer Vision:
Comparative analysis of Classical Computer Vision vs. Deep Learning (YOLOv11) for real-time weed detection in precision agriculture.
## 📌 About The Project
An automated system for identifying **Sugar Beets vs. Weeds** in agricultural fields.
We compared two methods to find the best and most efficient solution  :
1.  **Classical Computer Vision:** Using color indices (ExG) , Erosion and Dilation,  and Otsu thresholding.
2.  **Deep Learning (AI):** Using **YOLOv11-Nano Segmentation** for high precision.

##  Key Results
* **Winner:** YOLOv11 model achieved superior accuracy and robustness to lighting conditions.
* **Performance:** Optimized for T4 GPU, achieving real-time inference speeds.

##  Project Structure
* `notebooks/` - The complete code (Data prep, Training, Evaluation).
* `results/` - Graphs and visualized predictions.

##  How to Run
1.  Clone the repo.
2.  Install requirements: `pip install -r requirements.txt`
3.  Run the notebooks in Google Colab.
