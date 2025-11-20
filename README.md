	
# TeamQuals

Overview

This repository contains a complete benchmarking suite comparing:
	•	Deep Learning:
		BERT (bert-base-uncased)
	•	Traditional Machine Learning:
		Support Vector Machine (SVM)
		Naive Bayes
		Random Forest
		XGBoost

The goal is to classify bug priority (P1–P5) using Firefox bug reports, evaluating each model across:
	•	Accuracy
	•	F1-Macro Score
	•	Per-class Precision
	•	Full classification reports
	•	Prediction CSV exports
	•	Visualization plots

The suite is implemented in Python using Google Colab, PyTorch, scikit-learn, Transformers, and XGBoost.

⸻

🚀 Run the Notebook in Google Colab

1. Open the Notebook

Click the badge below to open the notebook directly in Google Colab:

[![ Click to Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/oloriafin/TeamQuals/blob/main/Project_Del_5_TeamQuals.ipynb)

2. Enable GPU (Required for BERT to run fast)
	1.	Go to: Runtime → Change runtime type
	2.	Set Hardware Accelerator = GPU
	3.	Click Save

3. 3. Upload the Dataset

The notebook expects: Firefox_bugs.csv

# Dataset  
This project uses the [GitBugs dataset](https://www.kaggle.com/datasets/av9ash/gitbugs) (hosted on Kaggle). 
Navigate to the firefox folder and download Firefox_bugs_csv
- Download the dataset from Kaggle and place it in your working directory (Colab or local). 

4. Run the Notebook

You have two options:

Option A — Run All
	•	Colab: Runtime → Run all

Option B — Run step-by-step (recommended)
Run each cell from top to bottom so you can observe preprocessing, model training, and outputs.\

5. What the Notebook Does

	1. Data Cleaning
		•	Remove duplicate bug reports
		•	Fix missing values
		•	Encode categorical fields (Status, Resolution, Priority)
	
	2. Text Preprocessing
		•	Combine Summary + Description
		•	Tokenize
		•	Remove stopwords
		•	Stem tokens
		•	Build processed_text column
	
	3. Train/Test Split
	
	Uses Priority_encoded with stratification.
	
	4. TF-IDF Vectorization
	
	Required for all classical ML models.
	
	5. Model Training
	
	Models included:
	
	SVM (LinearSVC) / Fast, strong baseline
	Naive Bayes / Classic text classifier
	Random Forest / TF-IDF
	XGBoost / Highest performing traditional model 
	BERT / Deep transformer for context-aware predictions
	
	All models compute:
	•	Accuracy
	•	Precision/Recall/F1
	•	Predictions saved to CSV

6. Output Files Automatically Generated

For each model:
	•	*_predictions.csv
	•	*_classification_report.txt

Plots generated:
	•	Model Accuracy Comparison
	•	Model F1-Macro Comparison
	•	Precision by Class Across All Models



