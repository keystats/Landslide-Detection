

# 🌍 Landslide Detection using Remote Sensing and Machine Learning

This repository presents a complete pipeline for detecting landslides from satellite imagery using handcrafted features and classical machine learning models. It was developed for the **Zindi Landslide Detection Challenge**, which focuses on identifying landslide-prone areas from `.npy` image data.

---

## 📁 Contents

* `LANDSLIDE_DETECTION.ipynb`: Core notebook with data processing, feature engineering, model training, and visualization.
* `README.md`: Project documentation.
* Dataset: Download available via the Zindi link in the [References](#-references) section.

---

## 📌 Problem Overview

Landslides are hazardous geological events with significant environmental and human impacts.
The challenge is to classify image patches as **landslide** or **non-landslide** using satellite-based RGB imagery in `.npy` format.

---

## 🛠️ Approach Overview

### 🧪 Data Format

* Images are stored as `.npy` files with shape `(3, H, W)`, representing RGB channels.
* Each sample is uniquely identified and used for feature extraction and classification.

### ⚙️ Feature Engineering

The pipeline relies on **domain-informed, handcrafted features**, including:

#### Spectral Features

* NDVI approximation (from RGB only)

#### Texture Features

* Gray-Level Co-occurrence Matrix (GLCM)
* Sobel edge detection
* Laplacian filters

#### Statistical Features

* Channel-wise mean, standard deviation, entropy, skewness, and kurtosis

#### Color & Pattern Features

* Brown tone intensity
* Green dominance
* Cloud-like structure detection

### 🗺️ Visual Insights

Includes rich visualizations of input patches and extracted terrain features to help interpret model predictions.

---

## 🤖 Model Pipeline

* **Core Model**: `HistGradientBoostingClassifier` (high performance on tabular features)
* **Output**: Probabilities converted to binary classes using manually tuned thresholds (typically `0.45 - 0.49`)

---

## ❌ Deep Learning Experiments

> Attempts using CNNs and Vision Transformers (ViTs) were explored but underperformed on validation and leaderboard metrics.

* These were excluded in favor of classical models with engineered features.

---

## 📈 Performance Summary

| Metric   | Value                              |
| -------- | ---------------------------------- |
| F1 Score | **0.8803** (Public Leaderboard)    |
| Accuracy | High (balanced precision & recall) |
| Runtime  | \~5 minutes (Google Colab)         |

---

## 📌 Key Observations

* **Landslide Indicators**:

  * Cloudiness
  * Irregular-shaped rivers
  * Brown/gray tone intensity
  * Rough terrain

* **Non-Landslide Indicators**:

  * Vibrant green/blue hues
  * Smooth, structured terrain
  * Visible buildings
  * Large, regular rivers

> Integrating domain knowledge with statistical features significantly improves prediction accuracy.

---

## 🚀 How to Use

1. **Clone the repository:**

   ```bash
   git clone https://github.com/keystats/Landslide-Detection.git
   ```

2. **Upload your `train_data/` and `test_data/` `.npy` files.**

3. **Run the notebook:**

   * Open `LANDSLIDE_DETECTION.ipynb` in **Jupyter Notebook** or **Google Colab**
   * Execute all cells to extract features, train the model, and make predictions

4. **Optional Tuning:**

   * Adjust thresholds or feature toggles for better performance.

---

## 🚧 Future Work

* Improve F1 Score from **0.8803 → 0.92+** via:

  * Advanced hybrid models
  * Rule-based post-processing
  * Ensemble techniques
* Incorporate geolocation or elevation data
* Build a lightweight UI for:

  * Manual inspection
  * Explaining predictions

---

## 📚 References

* [Zindi Challenge – Classification for Landslide Detection](https://zindi.africa/competitions/classification-for-landslide-detection/data)

---

## 👨‍💻 Author

**Keystats**
*Jackson Kahungu Njeri*
Data Scientist

---


