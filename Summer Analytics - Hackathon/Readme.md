# 🌿 NDVI-based Land Cover Classification  
**Summer Analytics 2025 Hackathon – IIT Guwahati x GeeksforGeeks**

This repository contains my solution to the **Mid Hackathon** of **Summer Analytics 2025**, hosted by the **Consulting & Analytics Club (CAC), IIT Guwahati**, in collaboration with **GeeksforGeeks (GFG)**. The task involved classifying land cover types from noisy satellite-based NDVI time-series data using **only Logistic Regression**.

---

## 📌 Table of Contents

- [🧠 Problem Statement](#-problem-statement)
- [📊 Competition Overview](#-competition-overview)
- [🗂️ Dataset Description](#️-dataset-description)
- [🧪 Approach & Methodology](#-approach--methodology)
- [⚙️ Model Details](#️-model-details)
- [📤 Submission Format](#-submission-format)
- [📈 Results](#-results)
- [🔗 Useful Links](#-useful-links)

---

## 🧠 Problem Statement

Participants were asked to build a **Logistic Regression model** to classify land into one of six classes using NDVI time-series data derived from satellite imagery.

### 🌍 Target Classes:
- `Water`
- `Impervious`
- `Farm`
- `Forest`
- `Grass`
- `Orchard`

### ⚠️ Constraints:
- **Model:** Logistic Regression only (multiclass)
- **Metric:** Accuracy Score
- **Challenge:** High noise due to cloud cover and digitization errors

---

## 📊 Competition Overview

| Metric                  | Value                |
|-------------------------|----------------------|
| 👥 Total Participants   | 1,395                |
| 📤 Total Submissions    | 6,504                |
| 📈 Public Leaderboard   | **Rank 56 / 1,395**   |
| 🔐 Private Leaderboard  | **Rank 192 / 1,395**  |
| 🏆 Awards               | Kudos (Non-rated)     |

---

## 🗂️ Dataset Description

The dataset includes time-series NDVI values for various land patches.

### Files:
- `hacktrain.csv`: Training data (with labels)
- `hacktest.csv`: Test data (no labels)

Each row consists of:
- `ID`: Unique identifier
- `class`: Land cover type (only in train)
- `27 NDVI columns`: Timestamps (e.g., `20150720_N`)

> 🧪 **Note:** Test set contains:
> - **89% noisy** samples → used for **public leaderboard**
> - **11% clean** samples → used for **private leaderboard**

---

## 🧪 Approach & Methodology

### 🔧 1. Preprocessing
- **Missing Values**:
  - Imputed using **median** per column.
- **Outlier Removal**:
  - Filtered using **IQR-based method** to reduce noise from clouds.
- **Feature Engineering**:
  - Statistical features: `mean`, `std`, `min`, `max`, `skew`, `kurtosis`
  - Temporal patterns: Early-season vs. late-season NDVI difference
  - NDVI signal features:
    - Count of values < 0
    - NDVI range (`max - min`)

---

## ⚙️ Model Details

- **Algorithm**: Logistic Regression (One-vs-Rest)
- **Library**: `scikit-learn`
- **Scaler**: `StandardScaler`
- **Regularization**: L2 (Ridge)
- **Validation**:
  - **5-fold Stratified Cross-Validation**
  - Averaged accuracy across folds

---

## 📤 Submission Format

Final predictions were submitted as a CSV file:

```csv
ID,class
1,water
2,impervious
3,grass
...
