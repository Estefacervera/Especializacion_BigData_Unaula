# Especializacion_BigData_Unaula🚢📊
## https://estefacervera.github.io/Especializacion_BigData_Unaula/
## 👥 Integrantes

- Estefanía Cervera Gómez  
- Andres Felipe Orozco Roa  
- Cristina Garcés Álvarez  
Proyecto de Big Data enfocado en la predicción de riesgo de siniestros en operaciones logísticas mediante modelos de Machine Learning.

## 📌 Descripción

Este proyecto desarrolla un sistema predictivo capaz de estimar la probabilidad de riesgo de un cliente basado en su comportamiento histórico.

Se procesan más de 1 millón de registros utilizando Apache Spark en Databricks, implementando una arquitectura tipo Medallion (Bronze, Silver, Gold).

## 🧠 Modelos utilizados

- Logistic Regression
- Random Forest
- Gradient Boosting

## ⚙️ Arquitectura

1. Ingesta de datos (CSV)
2. Procesamiento en Databricks (PySpark)
3. Modelo Medallion:
   - Bronze: datos crudos
   - Silver: limpieza y transformación
   - Gold: features para ML
4. Modelado predictivo
5. Generación de score de riesgo
6. Visualización

## 📊 Resultados

- Precisión del modelo: ~86%
- Reducción esperada de siniestralidad: -25%
- Score de riesgo generado por cliente

## 📁 Estructura del repositorio

/notebooks
modelo_riesgo.ipynb

/data
dataset.csv

/images


/docs
BigData_Seguros.html (index.html)

## 🚀 Cómo ejecutar

1. Cargar dataset en Databricks (El dataset base con las polizas y las caracteristicas de dada una se encuentra aqui https://drive.google.com/file/d/1AeZxGuWV9LCOMQI-d_OSXnzqUSd1MrYh/view?usp=sharing)
2. Ejecutar notebook de ingesta
3. Ejecutar transformación (Bronze → Silver → Gold)
4. Entrenar modelo
5. Generar predicciones

## 📌 Tecnologías

- Databricks
- PySpark
- Delta Lake
- Power BI
- Python








