# Skin Cancer Identification With Multimodal Methods

## Project Overview
This repository contains the experimental code, data processing pipelines, and evaluation metrics for a skin cancer classification study. This research was developed as the final project for the Master's level Pattern Recognition course at **UTFPR(CM)-PPGCC**. 

The primary objective of this study is to facilitate the early detection of skin cancer by leveraging machine learning algorithms and multimodal data. By evaluating various feature extraction techniques (Transfer Learning) and combining clinical metadata with image data through early fusion, late fusion, and hypernetwork-based fusion, this project aims to maximize diagnostic accuracy and patient survival probabilities.

## Dataset & Subsampling Strategy
The base dataset utilized for this research is the **[ISIC 2024 Challenge Dataset](https://www.kaggle.com/competitions/isic-2024-challenge/data)** available on Kaggle. 

To mitigate computational costs and prevent severe class imbalance during model training, a rigorous statistical subsampling strategy was applied:
* **Total Images:** 2,956 images.
* **Patient Cohorts:** 514 patients in total (257 diagnosed with cancer, 257 without).
* **Class Distribution:** 2,570 benign lesions and 386 malignant lesions.
* **Balancing Method:** A patient-level stratification was strictly maintained between training and testing sets to ensure robust generalization.

## Methodology
Our approach tests and combines multiple data modalities and classification architectures:
* **Feature Extraction:** Pre-trained Vision Transformers (ViT-Base) and Residual Networks (ResNet-50) were used to extract deep representations from lesion images.
* **Clinical Metadata:** Patient metadata was utilized as an independent feature space.
* **Classifiers:** Decision Trees (DT), Multilayer Perceptrons (MLP), and Support Vector Machines (SVM).
* **Fusion Techniques:**
  * **Late Fusion:** Aggregating classifier predictions using the **Sum Rule** and **Product Rule**.
  * **Advanced Fusion:** Early fusion and Hypernetwork-based feature fusion.

## Execution Pipeline
To reproduce the experiments, the Jupyter Notebooks should be executed in the following sequential order:

1. **`Data Sample.ipynb`**: Initial exploration and subsampling of the ISIC 2024 dataset.
2. **`Data Cleaning.ipynb`**: Preprocessing metadata, handling missing values, and formatting the data structures.
3. **`Images Selection.ipynb`**: Filtering and stratifying the image set to enforce the 5:1 benign-to-malignant ratio per patient.
4. **`Feature Extraction.ipynb` & `Transformers Feature Extraction.ipynb`**: Passing the selected images through the ViT-Base and ResNet-50 architectures to generate tabular embeddings.
5. **`Classification.ipynb`**: Training the base models (DT, MLP, SVM) on the individual image and metadata feature sets.
6. **`ResultsFusion.ipynb`**: Applying the late fusion algorithms and generating the final performance metrics.
