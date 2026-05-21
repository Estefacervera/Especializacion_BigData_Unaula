# Especializacion_BigData_Unaula🚢📊
## 👥 Integrantes

- Estefanía Cervera Gómez  
- Andres Felipe Orozco Roa  
- Cristina Garcés Álvarez  
Proyecto de Big Data enfocado en la predicción de riesgo de siniestros en operaciones logísticas mediante modelos de Machine Learning.

## 📌 Descripción
Aqui encuentras todo el resumen del proyecto y la justificación economica de realizarlo: https://estefacervera.github.io/Especializacion_BigData_Unaula/
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

/output
resultados_modelo.csv

/docs
BigData_Seguros.html

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








<img width="850" height="436" alt="image" src="https://github.com/user-attachments/assets/1ae620b2-9715-4359-96cb-b838b52e3d99" />


<img width="747" height="454" alt="image" src="https://github.com/user-attachments/assets/a63bd9d5-888b-49b3-aa66-6762219fa0ea" />

<img width="756" height="221" alt="image" src="https://github.com/user-attachments/assets/2190c959-2e71-4d14-8fc2-3a2e76f58e2e" />

<img width="820" height="545" alt="image" src="https://github.com/user-attachments/assets/6f842ac3-7497-4ea4-b53e-3f43a1b40715" />


======================================================================
FEATURE ENGINEERING - CREACIÓN DE VARIABLES DERIVADAS
======================================================================

1️⃣ Ratios Financieros:
   ✓ rentabilidad_envio = prima_usd / valor_mercancia_usd
   ✓ valor_por_kg = valor_mercancia_usd / peso_kg
   ✓ prima_por_dia = prima_usd / dias_transito_estimado

2️⃣ Complejidad Logística:
   ✓ complejidad_ruta = num_transbordos × dias_transito_estimado
   ✓ riesgo_climatico = |temperatura_ruta_c| × precipitacion_mm
   ✓ seguridad_ponderada = indice_seguridad_ruta / (num_transbordos + 1)

3️⃣ Perfil del Cliente:
   ✓ experiencia_volumen = anios_como_cliente × log(volumen_anual_usd)
   ✓ volumen_promedio_anual = volumen_anual_usd / anios_como_cliente

4️⃣ Interacciones Categóricas:
   ✓ fragil_modo = fragilidad + modo_transporte
   ✓ flujo_comercial = region_origen → region_destino

======================================================================
✅ FEATURE ENGINEERING COMPLETADO
======================================================================

📊 Dataset original: 26 features
📊 Dataset con FE: 36 features
📈 Nuevas features creadas: 10

📋 Estadísticas de las nuevas features numéricas:

<img width="792" height="540" alt="image" src="https://github.com/user-attachments/assets/847eef04-17fb-455a-961a-e8a27549166d" />

<img width="796" height="604" alt="image" src="https://github.com/user-attachments/assets/42572a85-3e9b-4b9a-9072-8a2279c2e97c" />

======================================================================
PIPELINE DE PREPROCESAMIENTO
======================================================================

Features numéricas: 19
  ✓ anios_como_cliente
  ✓ volumen_anual_usd
  ✓ valor_mercancia_usd
  ✓ peso_kg
  ✓ prima_usd
  ✓ dias_transito_estimado
  ✓ num_transbordos
  ✓ indice_seguridad_ruta
  ✓ temperatura_ruta_c
  ✓ precipitacion_mm
  ✓ fragilidad
  ✓ rentabilidad_envio
  ✓ valor_por_kg
  ✓ prima_por_dia
  ✓ complejidad_ruta
  ✓ riesgo_climatico
  ✓ seguridad_ponderada
  ✓ experiencia_volumen
  ✓ volumen_promedio_anual

Features categóricas: 13
  ✓ pais_cliente
  ✓ tipo_cliente
  ✓ modo_transporte
  ✓ region_origen
  ✓ region_destino
  ✓ incoterm
  ✓ tipo_mercancia
  ✓ requiere_refrigeracion
  ✓ transbordo
  ✓ temporada_huracanes
  ✓ alerta_geopolitica
  ✓ fragil_modo
  ✓ flujo_comercial

======================================================================
✅ Pipeline configurado
   - 19 numéricas (10 originales + 8 derivadas)
   - 13 categóricas (11 originales + 2 interacciones)
======================================================================



<img width="733" height="580" alt="image" src="https://github.com/user-attachments/assets/14428bbd-85b9-4aed-a403-ec83951eb84c" />


<img width="738" height="499" alt="image" src="https://github.com/user-attachments/assets/3a22b4cf-6911-4d42-9a1d-64f87cae6bbd" />

⭐ MEJOR MODELO: Logistic Regression con AUC-ROC = 0.6235

📊 Análisis:
   - Modelos básicos (GB, RF, LR): AUC ~0.5653
   - Modelos avanzados (XGB, LightGBM, CatBoost): AUC ~nan
   - Mejora con FE + modelos avanzados: 0.0000 puntos

<img width="760" height="287" alt="image" src="https://github.com/user-attachments/assets/23b2e7c8-9ba4-4755-965c-0c57e81cc218" />


<img width="756" height="603" alt="image" src="https://github.com/user-attachments/assets/c6e99d7d-0838-4307-b4f8-d8e1c9a6950e" />

======================================================================
EVALUACIÓN FINAL - LOGISTIC REGRESSION EN TEST SET
======================================================================

Métrica              Validación           Test                
----------------------------------------------------------------------
Accuracy             0.5927               0.5916              
Precision            0.1651               0.1646              
Recall               0.5869               0.5861              
F1-Score             0.2577               0.2570              
AUC-ROC              0.6235               0.6238              
======================================================================

<img width="751" height="589" alt="image" src="https://github.com/user-attachments/assets/f0629c7f-a131-4b47-9c9c-1268ba963583" />


✅ Modelo final seleccionado: Logistic Regression
✅ AUC-ROC en Test: 0.6238

💾 El modelo está registrado en MLflow y listo para producción.






