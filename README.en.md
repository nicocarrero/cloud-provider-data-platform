# ☁️ Cloud Provider Data Platform

End-to-end **Data Engineering and Big Data project** developed with **PySpark and Google Colab** for a simulated cloud provider environment.

The project implements a complete data pipeline combining **ETL/ELT, Batch Processing, Structured Streaming, a Medallion Data Lake and a Serving Layer with AstraDB / Apache Cassandra**.

## 🎯 Overview

The platform processes data from different areas of a cloud provider, including customers, users, cloud resources, billing, support and usage events.

The main pipeline follows:

```text
Landing → Bronze → Silver → Gold → Serving
```

The solution combines historical batch processing with near real-time streaming using a **Lambda Architecture**.

## 🏗️ Architecture

```text
Data Sources
     │
     ├── Batch (CSV)
     └── Streaming (JSONL)
            │
            ▼
        🟦 Landing
            │
            ▼
        🟫 Bronze
            │
            ▼
        🟩 Silver
          /     \
         /       \
        ▼         ▼
     🟨 Gold   Speed Layer
        │         │
        └────┬────┘
             ▼
       AstraDB / Cassandra
             │
             ▼
        BI / Analytics
```

* **Batch Layer:** processes historical data through the Data Lake.
* **Speed Layer:** processes streaming events using Structured Streaming.
* **Serving Layer:** provides processed data through AstraDB / Cassandra.

## 🔄 Data Pipeline

### Batch

```text
Landing → Bronze → Silver → Gold → Serving
```

Processes historical and master data, applying cleaning, validation, enrichment and analytical transformations.

### Streaming

```text
Streaming Events → Speed Layer → AstraDB
```

Processes usage events through micro-batches for near real-time metrics.

## 📊 Business Use Cases

**FinOps**

* Cost and consumption analysis
* Top-N services
* Revenue metrics
* Cost anomalies

**Support**

* Support tickets
* Severity analysis
* SLA monitoring
* CSAT

**Product & GenAI**

* Token consumption
* Estimated costs
* Near real-time usage

## 🛠️ Technologies

* Python
* PySpark / Apache Spark
* Spark SQL
* Structured Streaming
* Pandas
* Apache Cassandra / AstraDB
* Parquet
* Google Colab

🚀 Reproducibility

The project is designed to run in **Google Colab**, using Google Drive as the storage environment for the Data Lake.

### 1. Clone the repository

```bash
git clone https://github.com/nicocarrero/cloud-provider-data-platform.git
```

### 2. Open the notebook

Open the following notebook in **Google Colab**:

```text
datalake/proyecto.ipynb
```

### 4. Configure the environment

The notebook requires access to the Data Lake and to an AstraDB connection bundle
(`secure-connect-db-cloudprovider.zip`).

⚠️ Not included in this repository for security reasons. Generate/download your own
from your AstraDB dashboard and place it locally before running the notebook.

```text
datalake/
├── landing/
├── bronze/
├── silver/
├── gold/
└── quarantine/
```

### 5. Execute the notebook

Run the sections **in order**:

1. **Initial Setup**
2. **Landing → Bronze Ingestion**
3. **Bronze → Silver Transformation**
4. **Silver → Gold Transformation**
5. **Queries / Visualization**

## 📁 Project Structure

```text
cloud-provider-data-platform/
│
├── README.md
│
├── datalake/
│   ├── proyecto.ipynb
│   ├── landing/
│   ├── bronze/
│   ├── silver/
│   ├── gold/
│   └── quarantine/
│
└── docs/
    ├── CHECKLIST.pdf
    ├── Log de decisiones.txt
    └── Reporte proyecto.pdf
```

## ⚙️ Data Engineering Concepts

* Lambda Architecture
* Medallion Architecture
* ETL / ELT
* Batch Processing
* Structured Streaming
* Data Quality
* Data Enrichment
* Data Deduplication
* Anomaly Detection
* Analytical Data Marts
* Data Lake
* Serving Layer
* NoSQL / Cassandra

## 🎥 Project Presentation

[Watch on YouTube](https://youtu.be/ER9ghQQsOKs)

## 📌 Academic Project

Developed for **Minería de Datos II – ISTEA**.

🌐 **[Leer en español](README.md)**