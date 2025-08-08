🌍 Landslide Detection using Remote Sensing and Machine Learning
This repository contains a complete pipeline for detecting landslides from satellite imagery using handcrafted features and classical machine learning models. It was developed for the Zindi Landslide Detection Challenge, a geospatial competition focused on identifying landslide-prone areas from .npy image data.
📁 Contents
•	LANDSLIDE_DETECTION.ipynb: Core notebook with data processing, feature engineering, model training, and visualization.
•	Whole data is in the zindi link attached in the refference
•	README.md: Project documentation.
________________________________________
📌 Problem Overview
Landslides are hazardous geological phenomena with significant environmental and human impact. The challenge involves classifying image patches as landslide or non-landslide using satellite-based RGB image arrays.
________________________________________
🛠️ Approach Overview
🧪 Data Format
•	Images are stored as .npy files of shape (3, H, W) representing RGB channels.
•	Each sample is uniquely identified and used for feature extraction and prediction.
⚙️ Feature Engineering
The model relies heavily on domain-aware handcrafted features, including:
•	Spectral Features:
o	NDVI approximation (from RGB only)
•	Texture Features:
o	GLCM (Gray-Level Co-occurrence Matrix)
o	Sobel edge detection
o	Laplacian features
•	Statistical Features:
o	Channel-wise mean, std, entropy, skewness, kurtosis
•	Color/Pattern Features:
o	Brown tone intensity
o	Green dominance
o	Presence of cloud-like structures or irregular shapes
🗺️ Visual Insights
The notebook includes rich visualizations of input images and extracted terrain patterns to understand distinguishing visual characteristics between landslide and non-landslide areas.
🤖 Model Pipeline
•	Core model: HistGradientBoostingClassifier (fast and accurate on tabular data)
•	Output: Probabilities with manual threshold tuning (typically between 0.45 and 0.49)
🚫 Deep Learning Experiments
•	Attempts using CNNs and Vision Transformers (ViTs) were explored but yielded worse results than handcrafted features.
•	These methods were excluded from the final pipeline due to underperformance on validation and leaderboard metrics.
________________________________________
📈 Performance
Metric	Value
F1 Score	0.8803 (Public LB)
Accuracy	High (balanced P/R)
Runtime	~5 minutes (Google Colab)
________________________________________
📌 Key Observations
•	Landslide indicators: cloudiness, irregular-shaped rivers, brown/gray tones, rough terrain.
•	Non-landslide indicators: sparkling green/blue hues, smooth/structured terrain, visible houses, large regular rivers.
•	Integrating domain logic with statistical features significantly improves performance.
________________________________________
🚀 How to Use
1.	Clone the repo:
git clone https://github.com/keystats/Landslide-Detection.git
2.	Upload your train_data/ and test_data/ .npy files.
3.	Run the notebook:
o	Open LANDSLIDE_DETECTION.ipynb in Jupyter or Google Colab
o	Execute cells in sequence to extract features, train the model, and generate predictions
4.	Modify threshold or feature flags if needed to tune performance.
________________________________________
🚧 Future Work
•	Improve the F1-score from 0.8803 → 0.92+ using:
o	Advanced hybrid models
o	Better rule-based overrides
o	Ensemble methods with smarter post-processing
•	Incorporate elevation or geolocation data if available
•	Build a lightweight UI for visual inspection and rule explanation
________________________________________
📚 References
https://zindi.africa/competitions/classification-for-landslide-detection/data
________________________________________
👨‍💻 Author
Keystats
Jackson Kahungu Njeri
Data Scientist
 

