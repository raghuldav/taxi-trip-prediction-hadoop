# 🚕 Taxi Trip Time Prediction Using Hadoop, PySpark, and Machine Learning

## Overview
This project implements an **end-to-end distributed big data pipeline** for predicting taxi trip duration using over **197 million NYC Yellow Taxi trip records collected between 2019 and 2023**. The solution is designed to handle large-scale data efficiently by leveraging **Hadoop HDFS for distributed storage** and **PySpark for scalable data processing and machine learning**.

The entire workflow is deployed within a **Docker-based Hadoop and Spark environment**, enabling reproducible experimentation, scalable analytics, and efficient model training on massive real-world datasets.

**Dataset Source:**  
https://www.nyc.gov/site/tlc/about/tlc-trip-record-data.page

---

## Technology Stack
- **Apache Hadoop (HDFS)** – Distributed storage
- **Apache Spark (PySpark, MLlib)** – Distributed processing and ML
- **Docker & Docker Compose** – Cluster orchestration
- **Jupyter Notebook** – Interactive development
- **Java** – HDFS data ingestion utilities
- **Parquet** – Columnar data format for optimized performance

---

## Project Structure
```text
.
├── DIC EDA.ipynb # Distributed exploratory data analysis (PySpark)
├── Pyspark.ipynb # Data preprocessing and ML pipeline
├── spark.py # Spark word count example
├── HDFSDataIngestion.java # Java-based HDFS ingestion
├── docker-compose.yaml # Hadoop and Spark cluster configuration
├── docker-compose.override.yaml # Jupyter Notebook setup
├── config/ # Hadoop XML configuration files
├── DIC FINAL submission report.pdf

yaml
```

---

## Machine Learning Objectives

### Trip Duration Prediction (Regression)
- **Model:** Linear Regression  
- **Features:** Trip distance, fare amount, pickup time, passenger count, location  
- **Evaluation Metrics:**  
  - R² = **1.0**  
  - RMSE = **0.0099**

---

### Delay Risk Classification
- **Model:** Decision Tree  
- **Logic:** Trips are labeled as *Delayed* if the duration exceeds the 90th percentile  
- **Evaluation Metrics:**  
  - Accuracy = **0.9878**  
  - AUC = **0.9988**

---

### Temporal Clustering
- **Model:** KMeans (k = 5)  
- **Purpose:** Group trips based on pickup hour, day, and month  
- **Metric:**  
  - WSSSE = **32,162.13**

---

## Data Pipeline Overview

### Distributed Infrastructure
The pipeline runs on a Dockerized Hadoop cluster consisting of:
- Namenode  
- Datanode  
- ResourceManager  
- NodeManager  
- Jupyter Notebook  

---

### Data Ingestion
- Java-based ingestion using `HDFSDataIngestion.java`
- Alternative ingestion using `hdfs dfs -put`
- Data stored in **Parquet format** for efficient distributed processing

---

### Exploratory Data Analysis
- Analysis of trip distance, fare, tip, and duration distributions
- Outlier detection using **IQR** and **Z-score**
- Temporal trend analysis (hourly, daily, monthly)
- Location-based aggregation and summary statistics

---

### Data Cleaning and Feature Engineering
- Missing value handling using **KNN**, median, and mode imputation
- One-hot encoding for categorical time features
- Feature scaling using **StandardScaler**
- Feature assembly using **VectorAssembler**

---

## Model Evaluation Summary

| Task | Model | Key Metrics |
|------|-------|------------|
| Trip Duration Prediction | Linear Regression | R² = 1.0, RMSE = 0.0099 |
| Delay Risk Classification | Decision Tree | Accuracy = 0.9878, AUC = 0.9988 |
| Temporal Clustering | KMeans (k = 5) | WSSSE = 32,162.13 |

---

## HDFS Directory Structure

| Component | HDFS Path |
|---------|-----------|
| Input Data | hdfs://namenode:9000/user/raghu/input/ |
| Model Metrics | hdfs://namenode:9000/user/raghu/metrics/model_metrics/ |
| KMeans Predictions | hdfs://namenode:9000/user/raghu/predictions/kmeans_predictions/ |
| Linear Regression Predictions | hdfs://namenode:9000/user/raghu/predictions/lr_predictions/ |
| Decision Tree Predictions | hdfs://namenode:9000/user/raghu/predictions/dt_predictions/ |
| Trained Models | hdfs://namenode:9000/user/raghu/models/ |

---

## Quickstart Guide

### 1. Start the Hadoop and Spark Cluster
```bash
docker-compose up -d
2. Access Jupyter Notebook
arduino
Copy code
http://localhost:8888
3. Load Data into HDFS
bash
Copy code
hdfs dfs -mkdir -p /user/raghu/input/
hdfs dfs -put *.parquet /user/raghu/input/
4. Run the ML Pipeline
Open Pyspark.ipynb in Jupyter

Execute all cells to perform preprocessing, modeling, and evaluation

Conclusion
This project demonstrates how distributed systems and machine learning can be effectively combined to process massive transportation datasets at scale. By leveraging Hadoop, PySpark, and Docker, the pipeline enables efficient ingestion, scalable analytics, and highly accurate predictive modeling for urban mobility applications.

yaml

---
