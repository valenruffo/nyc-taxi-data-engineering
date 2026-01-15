# 🚖 NYC Taxi ETL Pipeline & Analysis

## 📌 Descripción del Proyecto
Este proyecto consiste en un pipeline de **Ingeniería de Datos** end-to-end para procesar, limpiar y analizar datos de viajes de taxis amarillos en Nueva York (Dataset de Agosto 2025). 

El objetivo principal fue transformar datos crudos en insights de negocio valiosos, identificando patrones de rentabilidad y comportamiento de la demanda.

## 🛠️ Tecnologías y Herramientas
* **Lenguaje:** Python 3.10
* **Procesamiento Big Data:** PySpark (SparkSession, DataFrames, SparkSQL)
* **Análisis y Visualización:** Pandas, Matplotlib
* **Entorno:** Google Colab
* **Formato de Datos:** Parquet (Columnar) y CSV

## ⚙️ Arquitectura del Pipeline (ETL)

### 1. Extract (Extracción)
* Ingesta de datos masivos desde fuentes públicas (AWS S3) en formato **Parquet**.
* Ingesta de tablas dimensionales (Zonas/Barrios) en formato **CSV**.

### 2. Transform (Transformación)
* **Limpieza de Datos:** Filtrado de outliers (viajes de 0 minutos, tarifas negativas, distancias nulas).
* **Manejo de Fechas:** Conversión de Unix Timestamps para cálculo preciso de duración de viajes.
* **Feature Engineering:** Creación de nuevas métricas de negocio:
    * `duration_minutes`: Duración exacta del viaje.
    * `usd_per_mile`: Métrica de rentabilidad por milla recorrida.
    * `tiempo_humano`: Formato legible para reportes.

### 3. Load (Carga)
* Enriquecimiento de datos mediante **Joins** con la tabla de zonas geográficas.
* Almacenamiento de los datos procesados ("Silver Table") en formato parquet para optimizar futuras consultas.

## 📊 Insights y Resultados Clave
Tras procesar más de **2.5 millones de registros**, el análisis reveló:
* **Zonas más rentables:** Los aeropuertos (JFK, LaGuardia) generan las propinas promedio más altas.
* **Patrones de pago:** Se filtraron pagos en efectivo para analizar propinas reales registradas en tarjeta.
* **Calidad de datos:** Se detectaron y limpiaron inconsistencias en los registros de tiempo y distancia.

## 🚀 Cómo ejecutar este proyecto
Este proyecto está diseñado para correr en Google Colab o cualquier entorno local con Spark instalado.
1.  Clonar el repositorio.
2.  Abrir el archivo `.ipynb` en Jupyter o Colab.
3.  Ejecutar las celdas secuencialmente (el script descarga automáticamente los datasets necesarios).

---
*Proyecto realizado por [Tu Nombre] - [Año]*
