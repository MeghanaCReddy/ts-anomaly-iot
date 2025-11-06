Time Series Anomaly Detection for IoT Sensors
Project Overview

This project implements an end-to-end machine learning pipeline to detect anomalies in time series sensor data from manufacturing equipment.
It includes data preparation, feature engineering, anomaly detection (statistical & deep learning methods), and visualizations.

Folder Structure
ts-anomaly-iot/
│
├── data/
│   ├── raw/             # Original dataset files (bearings dataset)
│   ├── processed/       # Cleaned & feature-engineered CSV files
│
├── notebooks/
│   ├── 01_EDA.ipynb         # Data preparation, feature engineering, anomaly detection
│   └── visualization.ipynb  # Visualizations of EDA, features, and anomaly results
│
├── reports/
│   ├── figures/            # Generated plots from visualization notebook
│   └── final_report.md    # Summary document
│
├── requirements.txt        # Python dependencies
└── README.md               # This file


Installation

Make sure Python 3.10+ is installed.

Install dependencies:

pip install -r requirements.txt


Dependencies include:

pandas

numpy

matplotlib

seaborn

scipy

scikit-learn

torch (PyTorch)

notebook (optional, for running Jupyter notebooks)

How to Run
1️⃣ EDA, Data Preparation & Anomaly Detection

Open and run the notebook:

notebooks/01_EDA.ipynb


This notebook will:

Load the raw dataset from data/raw/

Clean missing values and handle outliers

Perform feature engineering

Run anomaly detection using Isolation Forest and Autoencoder

Save the cleaned and feature-engineered dataset to data/processed/features.csv

2️⃣ Visualizations

Open and run the notebook:

notebooks/visualization.ipynb


This notebook will:

Load data/processed/features.csv

Generate visualizations for:

EDA (distributions, trends)

Feature distributions

Anomaly detection results across channels

Save plots to reports/figures/

3️⃣ Summary & Reports

The final report (reports/final_report.pdf) summarizes:

Problem understanding and approach

Feature engineering rationale

Model selection and comparison

Key findings and business insights

Limitations and future improvements

Notes

Ensure all raw dataset files are in data/raw/ as per the folder structure.

All code is in notebooks; you can run cells sequentially to reproduce results.

You can customize paths in notebooks if your directory structure is different.