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

## Resultados y Observaciones
- **AdaBoost**: Excelente ajuste en entrenamiento (R² ≈ 0.99), pero severo sobreajuste → mal desempeño en prueba (MAPE > 400%).  
- **CatBoost**: Capta parcialmente la estructura (R² train ≈ 0.77) pero falla en la generalización y en la cola de la distribución de `charges`.  
- **Huber Regressor**: Métricamente da el MAPE “más bajo” comparado con otros, pero las predicciones quedan demasiado contraídas, con R² negativo y mala forma en la distribución.  

En conclusión, los experimentos muestran que:
1. La **asimetría y dispersión de la variable `charges`** (cola larga) dificulta el modelado.
2. **MAPE no es estable** con valores pequeños de `charges`, lo que infló los resultados.
