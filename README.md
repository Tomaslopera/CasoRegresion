# Caso Regresión: Predicción de Primas de Seguros

Este repositorio contiene el desarrollo de un proyecto de **tarifación en seguros**, cuyo objetivo es construir un modelo de machine learning capaz de **pronosticar el valor de la prima de un asegurado** con un **MAPE menor o igual al 15%**.

## Contexto del Caso
Como parte del equipo de tarifación de una aseguradora, se requiere un modelo de predicción de primas que permita apoyar las decisiones de negocio en la fijación de tarifas y en el análisis de riesgos.

El conjunto de datos proporcionado corresponde a asegurados individuales con información demográfica, de hábitos y costos médicos, de acuerdo con el siguiente diccionario:

| Variable  | Descripción |
|-----------|-------------|
| **age**   | Edad del asegurado |
| **sex**   | Género del asegurado |
| **bmi**   | Índice de masa corporal del asegurado |
| **children** | Número de hijos del asegurado |
| **smoker**   | El asegurado es o no fumador |
| **region**   | Región comercial a la que pertenece el asegurado |
| **charges**  | Valor de la prima del asegurado (variable objetivo) |

## Objetivo
Desarrollar, entrenar y evaluar diferentes modelos de regresión con el fin de:
- Identificar cuál logra el mejor desempeño predictivo.
- Alcanzar un error porcentual (MAPE) ≤ 15% en datos de prueba.
- Evaluar gráficamente y mediante métricas la calidad de las predicciones.

## Modelos ML
Se implementaron y evaluaron distintos algoritmos de regresión, incluyendo:

- **Linear Regression**
- **KNeighbors Regressor**
- **SVR**
- **Decision Tree Regressor**
- **Random Forest Regressor**
- **Adaptative Boosting Regressor**
- **Gradient Boosting Regressror**
- **CatBoost Regressor**
- **Huber Regressor**
- **LightGBM Regressor**
- **Bayesian Ridge**
- **Extra Trees Regressor**

Cada modelo fue evaluado utilizando métricas como:
- **R²** (coeficiente de determinación)
- **MAE** (Mean Absolute Error)
- **RMSE** (Root Mean Squared Error)
- **MAPE** (Mean Absolute Percentage Error)

## Conclusiones

A partir de los modelos evaluados se puede observar que los mejores resultados fueron obtenidos por **Árboles de Decisión, Bosques Aleatorios, Adaptative Boosting y Gradient Boosting**:

- **Árboles de Decisión:** MAPE ≈ **38%** en Train y Test.  
- **Bosques Aleatorios:** MAPE ≈ **37%** en Train y Test.  
- **Adaptative Boosting:** MAPE ≈ **0.01%** en Train y **15%** en Test. Cumple con la hipótesis planteada, pero evidencia un **sobreajuste considerable**.  
- **Gradient Boosting:** MAPE ≈ **11%** en Train y **17%** en Test. Aunque no cumple con la hipótesis del 15%, resulta el **modelo más balanceado**.  

Según los resultados, se determina que **Gradient Boosting** es el modelo más adecuado, dado que presenta un mejor balance entre entrenamiento y prueba, y se aproxima al umbral de error establecido.

