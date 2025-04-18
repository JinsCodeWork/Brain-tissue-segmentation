# 🧠 Brain Tissue Segmentation

Segmentation of different brain tissues from MRI scans is a crucial preprocessing step for tasks such as disease diagnosis, classification, and brain age estimation. This project implements and compares **classical unsupervised learning** and **deep supervised learning** methods to segment four tissue classes:

- Background  
- Cerebrospinal Fluid (CSF)  
- White Matter (WM)  
- Gray Matter (GM)  

I use a dataset of **652 healthy subjects**, split into training/validation and a hold-out test set.

---

## 🧪 Methods

### 1. 🧩 Unsupervised Classical Methods

#### 📌 K-Means Clustering
- Uses voxel intensity as a single feature.
- Cluster number \( K=4 \), one for each tissue class.
- Sensitive to initialization and intensity overlaps.
- **Fast but spatially unaware**.

#### 📌 Gaussian Mixture Model (GMM)
- Assumes voxel intensities follow a mixture of 4 Gaussians.
- Applies Expectation-Maximization (EM) to optimize soft class probabilities.
- **Better boundary modeling** than K-Means.

---

### 2. 🧠 Deep Supervised Method

#### 📌 3D U-Net
- Fully convolutional neural network for 3D voxel-wise segmentation.
- **Input**: normalized and resampled 3D MRI volumes.
- **Loss**: combination of Dice Loss and Cross-Entropy Loss.
- **Augmentations**: flipping, rotation, and scaling.
- **Training**: monitored using validation Dice scores.

---

## 📊 Evaluation Results

I evaluate all methods using **Dice coefficient**, **Precision**, and **Recall** across the three tissues (CSF, WM, GM):

| Tissue | Metric   | K-Means | GMM     | U-Net   |
|--------|----------|---------|---------|---------|
| **CSF** | Dice     | 0.966   | 0.964   | **0.984** |
|        | Precision| 0.985   | 0.979   | **0.986** |
|        | Recall   | 0.939   | 0.944   | **0.983** |
| **WM**  | Dice     | 0.810   | 0.838   | **0.930** |
|        | Precision| 0.955   | 0.924   | **0.940** |
|        | Recall   | 0.743   | 0.785   | **0.921** |
| **GM**  | Dice     | 0.900   | 0.932   | **0.971** |
|        | Precision| 0.949   | 0.946   | **0.966** |
|        | Recall   | 0.873   | 0.916   | **0.975** |

> The U-Net model **consistently outperforms** classical unsupervised approaches in all metrics and tissue types. It is especially effective at handling difficult regions like WM.



