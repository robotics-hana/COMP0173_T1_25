Perfect — here is your updated README section with the Zenodo datasets properly integrated, formatted professionally for GitHub and academic use.

You can replace your Dataset section with this:

🌍 Attention U-Net for Iraqi Marshland & Lake Segmentation

AI for Sustainable Development | MSc Project

📌 Overview

This project applies an Attention U-Net architecture to segment and analyse marshland and lake water bodies across Iraq using 4-band Sentinel-2 imagery (RGB + NIR).

The model generates spatial segmentation maps to quantify environmental change and hydrological stress in freshwater ecosystems.

This work supports:

SDG 6 – Clean Water and Sanitation

SDG 13 – Climate Action

SDG 15 – Life on Land

Iraq’s marshlands are a UNESCO World Heritage Site and a globally significant biodiversity hotspot under severe climate and upstream water stress.

🛰️ Datasets

This project uses two publicly available datasets published on Zenodo.

1️⃣ Iraq Lake Surface Water Segmentation Dataset

📄 DOI: 10.5281/zenodo.18601352
🔗 https://zenodo.org/records/18601352

📜 License: CC BY 4.0

Description

Sentinel-2 Level-2A satellite imagery of major Iraqi lakes prepared for binary water segmentation.

Coverage

Lake Razzaza

Lake Habbaniyah

Lake Tharthar

Lake Dukan

Lake Darbandikhan

Data Characteristics

4-band input (B2, B3, B4, B8 – RGB + NIR)

Surface reflectance imagery

Seasonal median composites

512 × 512 tiles

Image–mask pairs

Float32 normalised arrays

Splits

Training: 857 tiles

Validation: 340 tiles

Test: 63 tiles

2️⃣ Southern Iraqi Marshes Surface Water Segmentation Dataset (2021)

📄 DOI: 10.5281/zenodo.18601207
🔗 https://zenodo.org/records/18601207

📜 License: CC BY 4.0

Description

A Sentinel-2 based surface water segmentation dataset for the Southern Iraqi Marshes, designed for benchmarking CNN segmentation models in complex wetland environments.

Data Characteristics

4-band Sentinel-2 (RGB + NIR)

Level-2A surface reflectance

Water masks derived from:

JRC Global Surface Water Yearly History

NDWI refinement

512 × 512 tiles

Balanced class distribution

Float32 normalised arrays

Splits

Training: 250 tiles

Validation: 100 tiles

Test: 20 tiles

📦 Dataset Format
training/
    images/  (.npy, shape: 512x512x4)
    masks/   (.npy, shape: 512x512x1)

validation/
test/


Images are stored as NumPy arrays

Masks are binary (0 = land, 1 = water)

All data normalised to [0,1]

📚 Citation

If you use these datasets, please cite:

@dataset{iraq_lakes_2025,
  author       = {Hadidi, Hana},
  title        = {Iraq Lake Image Dataset for Semantic Segmentation},
  year         = {2025},
  publisher    = {Zenodo},
  doi          = {10.5281/zenodo.18601352}
}

@dataset{iraq_marshes_2025,
  author       = {Hadidi, Hana},
  title        = {Sentinel-2 Surface Water Segmentation Dataset for the Southern Iraqi Marshes (2021)},
  year         = {2025},
  publisher    = {Zenodo},
  doi          = {10.5281/zenodo.18601207}
}

🧠 Model

Architecture: Attention U-Net

Base filters: 32

Batch Normalization

SpatialDropout2D

Binary Cross Entropy loss

Adam optimizer
