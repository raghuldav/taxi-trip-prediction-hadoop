# 🚕 Taxi Trip Time Prediction Using Hadoop, PySpark, and Machine Learning

## Overview
This project implements an **end-to-end distributed big data pipeline** for predicting taxi trip duration using **197+ million NYC Yellow Taxi records (2019–2023)**. The system is built on a **Dockerized Hadoop and Spark ecosystem**, enabling scalable data ingestion, distributed analytics, and machine learning at scale.

The pipeline integrates **HDFS for storage**, **PySpark for large-scale data processing**, and **MLlib-based machine learning models** for regression, classification, and clustering tasks related to trip duration and delay risk prediction.

**Dataset Source:**  
https://www.nyc.gov/site/tlc/about/tlc-trip-record-data.page

---

## Tech Stack
- **Apache Hadoop (HDFS)** – Distributed storage (Dockerized)
- **Apache Spark (PySpark + MLlib)** – Distributed processing & ML
- **Docker & Docker Compose** – Cluster orchestration
- **Jupyter Notebook** – Interactive PySpark development
- **Java** – HDFS ingestion utilities
- **Parquet** – Columnar data format for efficient big data handling

---

## Project Structure
.
├── DIC EDA.ipynb # PySpark-based exploratory data analysis
├── Pyspark.ipynb # Data preprocessing and ML pipeline
├── spark.py # Spark word count example
├── HDFSDataIngestion.java # Java-based HDFS file ingestion
├── docker-compose.yaml # Hadoop + Spark cluster setup
├── docker-compose.override.yaml # Jupyter Notebook configuration
├── config/ # Hadoop XML configuration files
├── DIC FINAL submission report.pdf

yaml
Copy code

---

## Machine Learning Objectives

### 1. Trip Duration Prediction (Regression)
- **Model:** Linear Regression  
- **Features:** Trip distance, fare, pickup/dropoff time, passenger count, location  
- **Metrics:**  
  - R² = **1.0**  
  - MAE = **0.0081**  
  - RMSE = **0.0099**

---

### 2. Delay Risk Classification (Binary Classification)
- **Model:** Decision Tree  
- **Logic:** Trip labeled *Delayed* if duration exceeds the 90th percentile  
- **Metrics:**  
  - Accuracy = **0.9878**  
  - AUC = **0.9988**

---

### 3. Temporal Clustering
- **Model:** KMeans (k = 5)  
- **Insight:** Trips clustered based on pickup hour, day, and month  
- **Metric:**  
  - WSSSE = **32,162.13** (compact clusters)

---

## Data Pipeline Overview

### Dockerized Hadoop Cluster
- Namenode  
- Datanode  
- ResourceManager  
- NodeManager  
- Jupyter Notebook  

Cluster services are defined in `docker-compose.yaml`.

---

### Data Ingestion
- Java-based ingestion using `HDFSDataIngestion.java`
- Alternative bulk upload using `hdfs dfs -put`
- File format: **Parquet** (efficient columnar storage)

---

### Exploratory Data Analysis (EDA)
- Trip distance, fare, tip, and duration distributions
- Outlier detection using **IQR and Z-score**
- Temporal trends (hourly, daily, monthly)
- Location-based aggregations and averages

---

### Data Cleaning & Feature Engineering
- Missing value handling using **KNN, median, and mode imputation**
- One-hot encoding for categorical time features
- Feature scaling using **StandardScaler**
- Feature assembly using **VectorAssembler** (MLlib)

---

## Evaluation Summary

| Task | Model | Key Metrics |
|-----|------|-------------|
| Trip Duration Prediction | Linear Regression | R² = 1.0, RMSE = 0.0099 |
| Delay Risk Classification | Decision Tree | Accuracy = 0.9878, AUC = 0.9988 |
| Temporal Clustering | KMeans (k=5) | WSSSE = 32,162.13 |

---

## Data Access in HDFS

| Item | HDFS Path |
|----|---------|
| Input Data | hdfs://namenode:9000/user/raghu/input/ |
| Model Metrics | hdfs://namenode:9000/user/raghu/metrics/model_metrics/ |
| KMeans Predictions | hdfs://namenode:9000/user/raghu/predictions/kmeans_predictions/ |
| Linear Regression Predictions | hdfs://namenode:9000/user/raghu/predictions/lr_predictions/ |
| Decision Tree Predictions | hdfs://namenode:9000/user/raghu/predictions/dt_predictions/ |
| Tuned Models (LR, DT, KMeans) | hdfs://namenode:9000/user/raghu/models/ |

---

## Quickstart Instructions

### 1. Start Hadoop & Spark Cluster
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
4. Run ML Pipeline
Open Pyspark.ipynb in Jupyter

Execute all cells to perform preprocessing, modeling, and evaluation

Conclusion
This project demonstrates how distributed systems and machine learning can be combined to process and analyze massive real-world datasets at scale. By leveraging Hadoop, PySpark, and Docker, the pipeline efficiently ingests, processes, and models over 197 million taxi records, delivering accurate predictions and actionable insights for urban mobility analytics.

yaml
Copy code

---

If you want next:
- **Shortened version for GitHub profile Overview**
- **Resume bullets (Big Data / Data Engineer / ML roles)**
- **Architecture diagram section**
- **Results visualization preview**

Just tell me 👍
