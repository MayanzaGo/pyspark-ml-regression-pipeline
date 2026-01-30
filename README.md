# Airfoil Self-Noise Prediction — PySpark ML Pipeline

## Project Overview

This project demonstrates an end-to-end **Data Engineering + Machine Learning pipeline** using **PySpark** to predict airfoil self-noise levels based on aerodynamic and physical characteristics.

As a Data Engineer, the objective was to:

✔ Perform ETL on raw CSV data  
✔ Clean and transform the dataset  
✔ Build a scalable Spark ML pipeline  
✔ Train and evaluate a regression model  
✔ Persist the trained model for production use  

The project simulates a real-world workflow where data scientists rely on engineered pipelines to efficiently train and deploy models.

Dataset: **NASA Airfoil Self Noise Dataset**

---

## Tech Stack

- Python
- PySpark (Spark MLlib)
- Spark SQL
- Linear Regression
- Parquet (columnar storage)
- Jupyter Notebook

---

## Pipeline Architecture

Raw CSV
↓
ETL Cleaning
• Remove duplicates
• Drop nulls
• Rename columns
↓
Parquet Storage
↓
VectorAssembler
↓
StandardScaler
↓
Linear Regression Model
↓
Evaluation (MSE, MAE, R²)
↓
Saved Pipeline Model (Production Ready)

## Project Structure

airfoil-noise-ml-pipeline/
│
├── data/
│ └── NASA_airfoil_noise_raw.csv
│
├── notebooks/
│ └── Airfoil_ML_Pipeline.ipynb
├── src/
│   └── airfoil_pipeline.py
│
├── requirements.txt
├── README.md
└── .gitignore



---

## Features

Input Variables:

- Frequency
- AngleOfAttack
- ChordLength
- FreeStreamVelocity
- SuctionSideDisplacement

Target:

- SoundLevelDecibels

---

## ETL Steps

1. Load raw CSV into Spark DataFrame
2. Remove duplicate rows
3. Drop rows with null values
4. Rename target column
5. Save cleaned dataset as Parquet

Why Parquet?
- Faster reads
- Columnar format
- Optimized for big data workloads

---

## Machine Learning Pipeline

The Spark ML pipeline contains 3 stages:

### Stage 1 — VectorAssembler
Combine all features into a single vector column

### Stage 2 — StandardScaler
Normalize features for better regression performance

### Stage 3 — Linear Regression
Predict airfoil sound level

---

## Model Evaluation

Metrics used:

- MSE (Mean Squared Error)
- MAE (Mean Absolute Error)
- R² (Coefficient of Determination)

Example:
MSE = 22.59
MAE = 3.73
R² = 0.54


---

## Model Persistence

The trained pipeline is saved using:

```python
pipelineModel.write().overwrite().save("Final_Project")



