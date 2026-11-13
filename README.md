# ☁️ Cloud Provider Data Platform

🌐 **[Read in English](README.en.md)**

Proyecto integral de **Ingeniería de Datos y Big Data** desarrollado con **PySpark y Google Colab** para un entorno simulado de proveedor de nube.

El proyecto implementa un pipeline de datos completo que combina **ETL/ELT, procesamiento Batch, Structured Streaming, un Data Lake con arquitectura Medallion y una capa de servicio con AstraDB / Apache Cassandra**.

## 🎯 Descripción general

La plataforma procesa datos de distintas áreas de un proveedor de nube, incluyendo clientes, usuarios, recursos cloud, facturación, soporte y eventos de uso.

El pipeline principal sigue el flujo:

```text
Landing → Bronze → Silver → Gold → Serving
```

La solución combina procesamiento batch histórico con streaming en casi tiempo real mediante una **Arquitectura Lambda**.

## 🏗️ Arquitectura

```text
Fuentes de datos
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

* **Batch Layer:** procesa datos históricos a través del Data Lake.
* **Speed Layer:** procesa eventos en streaming usando Structured Streaming.
* **Serving Layer:** expone los datos procesados mediante AstraDB / Cassandra.

## 🔄 Pipeline de datos

### Batch

```text
Landing → Bronze → Silver → Gold → Serving
```

Procesa datos históricos y maestros, aplicando limpieza, validación, enriquecimiento y transformaciones analíticas.

### Streaming

```text
Eventos Streaming → Speed Layer → AstraDB
```

Procesa eventos de uso mediante micro-batches para obtener métricas en casi tiempo real.

## 📊 Casos de uso de negocio

**FinOps**

* Análisis de costos y consumo
* Top-N de servicios
* Métricas de ingresos
* Anomalías de costos

**Soporte**

* Tickets de soporte
* Análisis de severidad
* Monitoreo de SLA
* CSAT

**Producto y GenAI**

* Consumo de tokens
* Costos estimados
* Uso en casi tiempo real

## 🛠️ Tecnologías

* Python
* PySpark / Apache Spark
* Spark SQL
* Structured Streaming
* Pandas
* Apache Cassandra / AstraDB
* Parquet
* Google Colab

## 🚀 Reproducibilidad

El proyecto está diseñado para ejecutarse en **Google Colab**, usando Google Drive como almacenamiento del Data Lake.

### 1. Clonar el repositorio

```bash
git clone https://github.com/nicocarrero/cloud-provider-data-platform.git
```

### 2. Abrir el notebook

Abre el siguiente notebook en **Google Colab**:

```text
datalake/proyecto.ipynb
```

### 3. Configurar el entorno

El notebook requiere acceso al Data Lake y a un bundle de conexión de AstraDB
(`secure-connect-db-cloudprovider.zip`).

⚠️ No se incluye en este repositorio por motivos de seguridad. Genera/descarga el tuyo
desde el panel de AstraDB y colócalo localmente antes de ejecutar el notebook.

```text
datalake/
├── landing/
├── bronze/
├── silver/
├── gold/
└── quarantine/
```

### 4. Ejecutar el notebook

Ejecuta las secciones **en orden**:

1. **Configuración inicial**
2. **Ingesta Landing → Bronze**
3. **Transformación Bronze → Silver**
4. **Transformación Silver → Gold**
5. **Consultas / Visualización**

## 📁 Estructura del proyecto

```text
cloud-provider-data-platform/
│
├── README.md
├── README.en.md
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

## ⚙️ Conceptos de Ingeniería de Datos

* Arquitectura Lambda
* Arquitectura Medallion
* ETL / ELT
* Procesamiento Batch
* Structured Streaming
* Calidad de datos
* Enriquecimiento de datos
* Deduplicación de datos
* Detección de anomalías
* Data Marts analíticos
* Data Lake
* Serving Layer
* NoSQL / Cassandra

## 🎥 Presentación del proyecto

[Ver en YouTube](https://youtu.be/ER9ghQQsOKs)

## 📌 Proyecto académico

Desarrollado para **Minería de Datos II – ISTEA**.