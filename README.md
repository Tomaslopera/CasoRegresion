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
- **WMAPE** (Weighted Mean Absolute Percentage Error)

## Resultados y Observaciones
- **Huber Regressor**
  - **WMAPE ≈ 51%** (el mejor entre los probados), R² ≲ 0.
  - **MAPE = 34%**
  - Gráfica: predicciones **muy contraídas** alrededor del centro; subestima la cola alta. “Mejora” el wMAPE al reducir errores grandes, pero a costa de **baja varianza** en ŷ.

- **CatBoost Regressor**
  - **wMAPE ≈ 51–52%**, R² ≲ 0 (similar a Huber).
  - Gráfica: distribución de ŷ **más angosta** y **desplazada a la izquierda** respecto a y; no captura bien primas altas.

- **Gradient Boosting Regressor**
  - **wMAPE ≈ 51–52%**, R² ≲ 0 (empatado con CatBoost).
  - Gráfica: patrón parecido a CatBoost; tendencia a **subestimar** en los tramos altos.

- **AdaBoost Regressor**
  - **wMAPE ≈ 71%** en prueba vs **≈ 0.1%** en entrenamiento → **sobreajuste severo**.
  - Gráfica: ajuste casi perfecto en train; en prueba las predicciones se comprimen y quedan **sesgadas a la baja**, aún así de las gráficas es de las mejores a considerar.

- **Extra Trees Regressor**
  - **wMAPE ≈ 77%**, R² ≈ 0.
  - Gráfica: ŷ claramente **subestima** la cola y concentra masa en el rango medio; peor desempeño relativo.

> **Conclusión:** Ningún modelo probó estar cerca del objetivo de **≤ 15% wMAPE**. Los mejores (Huber / CatBoost / Gradient Boosting) se sitúan alrededor de **≈ 51–52%**, mientras que AdaBoost y Extra Trees quedan por encima de **70%**.

