
-----

# Summer Analytics First Hackathon: NDVI-based Land Cover Classification

-----

## 🌟 Overview

Welcome to the **First Course Hackathon of Summer Analytics 2025**\! This exciting event, hosted by the **Consulting & Analytics Club** and **GeeksforGeeks (GFG)**, challenges you to classify land cover types using **NDVI time-series data** from satellite imagery and OpenStreetMap (OSM) labels.

**🔗 Hackathon Link:** [https://www.kaggle.com/competitions/summer-analytics-mid-hackathon/overview](https://www.kaggle.com/competitions/summer-analytics-mid-hackathon/overview)

Your primary goal is to build a **Logistic Regression model** that accurately predicts land cover classes despite the inherent noise in the NDVI signals. Top performers stand a chance to win **GFG Premium memberships**, and all participants will receive **exclusive discounts**\!

-----

## 🎯 The Challenge: NDVI-based Land Cover Classification

### Key Concepts

1.  **NDVI (Normalized Difference Vegetation Index)**
    The NDVI is a crucial metric for measuring vegetation health using satellite data. It's calculated as:

    $$
    $$$$\\text{NDVI} = \\frac{\\text{NIR} - \\text{RED}}{\\text{NIR} + \\text{RED}}

    $$
    $$$$Where:

      * **NIR** = Near-Infrared reflectance
      * **RED** = Red reflectance

2.  **Data Challenges**
    The dataset presents several real-world complexities you'll need to address:

      * **Noise**: Both the satellite imagery and crowdsourced data contain noise, stemming from factors like cloud cover in images and inaccuracies in OpenStreetMap (OSM) labeling/digitization of polygons.
      * **Missing Data**: Certain NDVI values are missing due to cloud cover obstructing satellite views.
      * **Temporal Variations**: NDVI values naturally vary seasonally. Effective feature engineering will be key to extracting meaningful trends from these time series.

    **Important Note:** The training data (`hacktrain.csv`) and the public leaderboard test data (`hacktest.csv`, 89% of it) contain noisy observations. However, the **private leaderboard data** (the remaining 11% of `hacktest.csv`) is **clean and free of noise**. This design will evaluate how well your model generalizes beyond noisy training conditions to real-world clean data.

-----

## 📊 Dataset Description

Each row in the dataset provides the following information:

  * **`class`**: The ground truth label of the land cover type. Possible classes are: `{Water, Impervious, Farm, Forest, Grass, Orchard}`
  * **`ID`**: A unique identifier for each sample.
  * **27 NDVI Time Points**: Columns labeled in the format `YYYYMMDD_N` (e.g., `20150720_N`, `20150602_N`). These represent NDVI values collected on different dates, forming a time series that illustrates vegetation dynamics for each location.

### Files

You will be working with two primary files:

  * **`hacktrain.csv`**: This is your training dataset. It contains noise due to inaccurate NDVI calculations in the presence of clouds.
  * **`hacktest.csv`**: This dataset will be used to test your model. As mentioned, 89% of it contains noise (for the public leaderboard), and 11% is clean (for the private leaderboard evaluation).

### Data Download

You can download the dataset directly from Kaggle using the following command in your terminal or Kaggle Notebook:

```bash
kaggle competitions download -c summer-analytics-mid-hackathon
```

*Make sure you have the Kaggle API installed and configured.*

-----

## ⚙️ Rules & Evaluation

### Model Constraint

  * You are strictly required to use **Logistic Regression** only. Multiclass classification is expected.

### Preprocessing

  * You are encouraged to perform **denoising, imputation, and feature engineering** to improve your model's performance.

### Leaderboard

  * **Public Leaderboard (89% of test data)**: Provides immediate feedback on your submission's performance.
  * **Private Leaderboard (11% of test data)**: This will determine your final ranking and is designed to prevent overfitting to the noisy public data.

### Evaluation Metric

  * Submissions will be evaluated based on the **accuracy score** of the predicted class.

### Submission Format

Your submission file should be a CSV with two columns: `ID` and `class`.

Example:

```csv
ID,class
1,water
2,water
3,grass
4,impervious
..
```

-----

## 🚀 Submissions

You can make multiple submissions. The evaluated submission with the **best Private Score** will be used for your final ranking.

  * You can select up to 2 submissions to be evaluated for your final leaderboard score.
  * Ensure your submission file adheres strictly to the specified format.

-----

Good luck, and happy hacking\! If you have any questions during the hackathon, please refer to the Kaggle competition page for discussions or announcements.

-----