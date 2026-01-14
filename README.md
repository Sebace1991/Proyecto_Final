🎬 Proyecto Final – Ingeniería de Datos con Databricks

Arquitectura Medallion | PySpark | Azure Databricks | GitHub

📌 Descripción general

Este proyecto implementa un pipeline ETL completo en Azure Databricks, utilizando PySpark y siguiendo la arquitectura Medallion (Raw, Bronze, Silver, Gold).
El objetivo es ingestar, transformar y modelar datos provenientes de múltiples datasets relacionados con películas, dejándolos listos para análisis y visualización.

El proyecto cumple con todas las condiciones establecidas en el enunciado del trabajo final del curso de Ingeniería de Datos con Databricks.

🎯 Objetivos del proyecto

Implementar un ETL usando PySpark

Aplicar la arquitectura Medallion

Utilizar Azure Data Lake Gen2 como almacenamiento

Conectarse a la capa Raw usando Managed Identity

Integrar múltiples datasets

Orquestar el pipeline usando Databricks Workflows (Job YAML)

Versionar el código en GitHub

Dejar los datos listos para consumo analítico

🧱 Arquitectura Medallion
RAW (ADLS Gen2)
   ↓
BRONZE (Datos limpios)
   ↓
SILVER (Datos integrados y con reglas de negocio)
   ↓
GOLD (Modelo analítico)

Capas:
🔹 RAW

Ingesta de archivos CSV desde ADLS Gen2

Sin transformaciones

Datos almacenados en formato Parquet

Acceso usando Managed Identity

No se utiliza DBFS ni Volumes

🔹 BRONZE

Normalización de nombres de columnas

Eliminación de duplicados

Conversión básica de tipos

Datos confiables pero sin lógica de negocio

🔹 SILVER

Integración de múltiples datasets

Joins por identificador de película

Aplicación de reglas de negocio

Dataset unificado y consistente

🔹 GOLD

Creación de datasets analíticos

Agregaciones y métricas

Datos listos para visualización y BI

📂 Datasets utilizados

Se utilizaron múltiples datasets públicos (Kaggle) relacionados con películas:

Movies.csv

FilmDetails.csv

MoreInfo.csv

PosterPath.csv

Estos datasets permiten cumplir con el requisito de mínimo dos insumos para el ETL.

🗂️ Estructura del repositorio
databricks-movies-project/
│
├── notebooks/
│   ├── raw/
│   │   └── ingest_raw_movies
│   ├── bronze/
│   │   └── bronze_movies
│   ├── silver/
│   │   └── silver_movies
│   └── gold/
│       └── gold_movies_analytics
│
├── workflows/
│   └── movies_etl_job.yml
│
├── config/
│   ├── dev.yml
│   └── prod.yml
│
└── README.md

⚙️ Tecnologías utilizadas

Azure Databricks

PySpark

Azure Data Lake Storage Gen2

Managed Identity

Databricks Workflows (Jobs)

GitHub

🔐 Seguridad y acceso

El acceso al Data Lake se realiza exclusivamente mediante Managed Identity

No se utilizan:

Storage keys

Secrets

DBFS

Volumes como capa Raw

Esto garantiza buenas prácticas de seguridad y cumplimiento del enunciado.

🔁 Orquestación del pipeline

El pipeline se orquesta usando un Databricks Job definido en YAML, que ejecuta las capas en el siguiente orden:

RAW – Ingesta

BRONZE – Limpieza

SILVER – Integración

GOLD – Analítica

El orden está controlado mediante dependencias entre tareas (depends_on).

📊 Resultados – Capa GOLD

La capa GOLD genera datasets analíticos como:

Métricas generales de películas (KPI)

Películas por género

Top películas por rating

Películas por año de lanzamiento

Estos datasets están listos para ser consumidos por:

Databricks SQL

Power BI

Herramientas de BI externas

🚀 Ejecución del proyecto
Opción 1 – Desde Databricks

Importar el Job YAML

Asignar un cluster existente

Ejecutar el workflow completo

Opción 2 – Desde GitHub

El código se encuentra versionado

El pipeline puede integrarse a procesos de CI/CD

✅ Cumplimiento de requisitos del proyecto
Requisito	Cumple
Arquitectura Medallion	✅
PySpark	✅
≥ 2 datasets	✅
Managed Identity	✅
No DBFS / Volumes en Raw	✅
ETL completo	✅
YAML de orquestación	✅
GitHub	✅
📌 Conclusión

Este proyecto demuestra la aplicación práctica de conceptos clave de Ingeniería de Datos, incluyendo:

Diseño de pipelines ETL

Buenas prácticas de seguridad

Arquitectura Medallion

Orquestación en Databricks

Preparación de datos para analítica

El resultado es un pipeline robusto, escalable y alineado con estándares reales de la industria.