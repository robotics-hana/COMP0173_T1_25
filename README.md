## 🌍 Attention U-Net for Iraqi Marshland and Lake Segmentation  
AI for Sustainable Development | MSc Dissertation Project

---

## 1. Overview

This project implements an Attention U-Net architecture to perform semantic segmentation of marshland and lake surface water bodies across Iraq using 4-band Sentinel-2 imagery (RGB + Near-Infrared).

The objective is to generate high-resolution spatial segmentation maps that quantify environmental change, hydrological stress, and surface water dynamics within critical freshwater ecosystems.

This research directly contributes to the following United Nations Sustainable Development Goals (SDGs):

- SDG 6 – Clean Water and Sanitation  
- SDG 13 – Climate Action  
- SDG 15 – Life on Land  

Iraq’s marshlands constitute a UNESCO World Heritage Site and represent one of the most ecologically significant wetland systems in the Middle East. These ecosystems are currently under severe pressure from climate change, reduced upstream discharge, and anthropogenic water management practices.

---

## 2. Datasets

Two publicly available datasets were developed and published on Zenodo for this research.

---

## 2.1 Iraq Lake Surface Water Segmentation Dataset

DOI: 10.5281/zenodo.18601352  
URL: https://zenodo.org/records/18601352  
License: Creative Commons Attribution 4.0 (CC BY 4.0)

### Description

This dataset consists of Sentinel-2 Level-2A surface reflectance imagery of major Iraqi lakes, curated for binary water segmentation tasks.

### Geographic Coverage

- Lake Razzaza  
- Lake Habbaniyah  
- Lake Tharthar  
- Lake Dukan  
- Lake Darbandikhan  

### Data Characteristics

- Four spectral bands: B2 (Blue), B3 (Green), B4 (Red), B8 (Near-Infrared)  
- Level-2A surface reflectance products  
- Seasonal median composites  
- Tiled into 512 × 512 pixel patches  
- Image–mask pairs  
- Stored as float32 normalised arrays  

### Dataset Splits

- Training set: 857 tiles  
- Validation set: 340 tiles  
- Test set: 63 tiles  

---

## 2.2 Southern Iraqi Marshes Surface Water Segmentation Dataset (2021)

DOI: 10.5281/zenodo.18601207  
URL: https://zenodo.org/records/18601207  
License: Creative Commons Attribution 4.0 (CC BY 4.0)

### Description

This dataset contains Sentinel-2 Level-2A surface reflectance imagery of the Southern Iraqi Marshes, specifically curated to benchmark convolutional neural network (CNN) segmentation models in complex wetland environments.

### Data Characteristics

- Four spectral bands (RGB + Near-Infrared)  
- Level-2A surface reflectance imagery  
- Binary water masks derived from:
  - JRC Global Surface Water Yearly History dataset  
  - Normalised Difference Water Index (NDWI) refinement  
- 512 × 512 pixel tiles  
- Balanced class distribution  
- Stored as float32 normalised arrays  

### Dataset Splits

- Training set: 250 tiles  
- Validation set: 100 tiles  
- Test set: 20 tiles  

---

## 3. Dataset Structure and Format

training/
├── images/        (.npy files, shape: 512×512×4)
└── masks/         (.npy files, shape: 512×512×1)

validation/
├── images/        (.npy files, shape: 512×512×4)
└── masks/         (.npy files, shape: 512×512×1)

test/
├── images/        (.npy files, shape: 512×512×4)
└── masks/         (.npy files, shape: 512×512×1)


### Data Format Specifications

- Image files are stored as NumPy (.npy) arrays.
- Each image has dimensions 512 × 512 × 4 corresponding to Sentinel-2 bands (B2, B3, B4, B8).
- Mask files are stored as NumPy (.npy) arrays with dimensions 512 × 512 × 1.
- Masks are binary encoded:
  - 0 represents land
  - 1 represents water
- All imagery is min–max normalised to the range [0, 1].

---

## 4. Citation

If these datasets are used in academic work, please cite:

@dataset{iraq_lakes_2025,  
  author    = {Hadidi, Hana},  
  title     = {Iraq Lake Image Dataset for Semantic Segmentation},  
  year      = {2025},  
  publisher = {Zenodo},  
  doi       = {10.5281/zenodo.18601352}  
}

@dataset{iraq_marshes_2025,  
  author    = {Hadidi, Hana},  
  title     = {Sentinel-2 Surface Water Segmentation Dataset for the Southern Iraqi Marshes (2021)},  
  year      = {2025},  
  publisher = {Zenodo},  
  doi       = {10.5281/zenodo.18601207}  
}

---

## 5. Model Architecture

The segmentation model is based on the Attention U-Net architecture, incorporating attention gating mechanisms to enhance spatial feature discrimination and boundary refinement.

Model configuration:

- Base number of convolutional filters: 32  
- Batch Normalization layers  
- SpatialDropout2D regularisation  
- Loss function: Binary Cross-Entropy  
- Optimiser: Adam  

The model is trained to perform binary semantic segmentation of water versus land across multispectral Sentinel-2 imagery.


# 6. . Experimental Reproducibility

This repository contains two primary experimental pipelines to ensure full reproducibility of both the original baseline model and the adapted dissertation model.

## 6.1 Adapted Iraq Lakes and Marshes Experiments

File: Experimentation Lake Marshes.ipynb

This notebook contains the full experimental pipeline for the adapted model developed in this dissertation.

It uses:
- The Iraq Lake Surface Water Segmentation Dataset
- The Southern Iraqi Marshes Surface Water Segmentation Dataset
- 4-band Sentinel-2 imagery (RGB + NIR)
- The modified Attention U-Net architecture

To reproduce the adapted experiments:
1. Place the dataset folders (training, validation, test) in the correct directory structure.
2. Open Experimentation Lake Marshes.ipynb.
3. Run all cells sequentially.

The notebook performs:
- Loading .npy 4-band multispectral images
- Min-max normalisation
- Model training (U-Net and Attention U-Net)
- Evaluation using Accuracy, Precision, Recall, and F1-score
- Cross-dataset transfer evaluation (marshes → lakes)

This file represents the primary experimental contribution of the MSc dissertation.

## 6.2 Original Baseline Reproduction

Files: 
- Experimentation_Adpated.ipynb
- Experimentation-Code_Original.pdf

These files reproduce the original dataset and baseline model setup used as the methodological foundation for this project.

To rerun the original experiment:
1. Ensure the original dataset is structured as expected in the notebook.
2. Open Experimentation_Adpated.ipynb.
3. Run all cells sequentially.

The notebook:
- Loads the original dataset
- Preprocesses RGB images and masks
- Trains the baseline U-Net architecture
- Outputs segmentation metrics

This provides a controlled baseline for comparison against the adapted Iraq Lakes and Marshes experiments.

# References

FAO (2021) The State of the World’s Forests 2021. Rome: Food and Agriculture Organization of the United Nations.

John, D. and Zhang, C. (2022) ‘An attention-based U-Net for detecting deforestation within satellite sensor imagery’, International Journal of Applied Earth Observation and Geoinformation, 107, p. 102685. Available at: https://doi.org/10.1016/j.jag.2022.102685

UNEP (2011) Towards a Green Economy: Pathways to Sustainable Development and Poverty Eradication. Nairobi: United Nations Environment Programme.

UNESCO World Heritage Centre (n.d.) The Ahwar of Southern Iraq: Refuge of Biodiversity and the Relict Landscape of the Mesopotamian Cities. Available at: https://whc.unesco.org/en/list/1481/
 (Accessed: 11 February 2026).
