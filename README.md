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

Directory structure:

training/  
  ├── images/   (.npy, shape: 512×512×4)  
  └── masks/    (.npy, shape: 512×512×1)  

validation/  
test/  

### Data Format Specifications

- Images are stored as NumPy (.npy) arrays  
- Input tensors have dimensions 512 × 512 × 4  
- Masks are binary with:
  - 0 representing land  
  - 1 representing water  
- All imagery is min–max normalised to the range [0,1]  

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
