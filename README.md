# Full-Stack On-Premise Data Pipeline for IoT & Weather Data 🌦️

## 🚀 Project Overview
This project demonstrates a complete on-premise data engineering pipeline designed for a hypothetical weather analytics company. It involves real-time and batch data ingestion, processing, storage, orchestration, and monitoring using open-source technologies.

---

## 📌 Key Features
- Ingests real-time weather data from **OpenWeatherMap API** via Kafka.
- Simulates IoT sensor logs using **Faker** saved to CSV and MySQL.
- Real-time streaming and batch processing using **Apache Spark**.
- Stores processed data in **Hive tables**, **MySQL tables**, and **Parquet files**.
- Orchestrates the workflow using **Apache Airflow**.
- Monitors pipeline health with **Grafana + Prometheus**.
- Optional: Docker Compose setup for easy deployment.

---

## 🧰 Tech Stack
| Layer | Tools/Technologies |
|-------|--------------------|
| Ingestion | Python, Kafka, Faker |
| Processing | Apache Spark (Streaming & Batch) |
| Storage | Apache Hive, MySQL, Parquet |
| Orchestration | Apache Airflow |
| Monitoring | Grafana, Prometheus |
| Deployment (Optional) | Docker Compose |

---

## 📥 Data Sources
1. **OpenWeatherMap API**  
   Real-time weather metrics: temperature, humidity, wind, etc.

2. **Simulated CSV Files (IoT Data)**  
   Faker-generated CSV files every minute.

3. **Mock MySQL Historical Data**  
   Simulated structured weather data in a local MySQL database.

---

## 🔄 Pipeline Breakdown

### 1. Ingestion Layer
- Fetch weather data every minute via OpenWeatherMap API.
- Generate fake sensor logs using `faker` and save to CSV.
- Insert mock device/sensor data into MySQL.

### 2. Processing Layer
- **Spark Streaming**: Reads from Kafka and writes Parquet files.
- **Spark Batch**: Joins CSV + MySQL, transforms and writes to Hive and MySQL.

### 3. Storage Layer
- Parquet Files: From streaming.
- Hive Table: Final ETL output.
- MySQL Table: For relational use.

### 4. Orchestration
- Managed using Airflow:
   - `weather_to_kafka_dag.py`
   - `batch_etl_dag.py`

### 5. Monitoring
- Prometheus scrapes metrics.
- Grafana visualizes health of Kafka, Spark, Airflow, etc.

---
### 6. Setup & Execution
- Prerequisites
   - Python 3.x
   - Apache Kafka
   - Apache Spark
   - Apache Hive
   - MySQL
   - Apache Airflow
   - Docker (Optional)

### 7. Sample Output
- Parquet files stored in /data/parquet/
- Hive table: default.final_table
- MySQL table: final_weather_data

---

## 📁 Project Structure
```bash
onprem-data-pipeline-yourname/
│
├── airflow_dags/
│   ├── weather_to_kafka_dag.py
│   └── batch_etl_dag.py
│
├── spark_jobs/
│   ├── streaming_kafka_to_parquet.py
│   └── batch_etl.py
│
├── kafka_producers/
│   └── weather_api_producer.py
│
├── data_generators/
│   ├── fake_sensor_to_csv.py
│   └── mysql_data_loader.py
│
├── hive_scripts/
│   └── create_tables.hql
│
├── docker/
│   └── docker-compose.yml (Optional)
│
├── grafana_dashboards/
│   └── weather_pipeline_dashboard.json
│
└── README.md
