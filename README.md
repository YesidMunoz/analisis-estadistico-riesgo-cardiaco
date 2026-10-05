# Análisis estadístico de factores de riesgo cardíaco

Análisis exploratorio y pruebas de hipótesis en Python sobre un conjunto de datos de **8.763 pacientes** con variables de salud cardiovascular. El objetivo es determinar si existen diferencias estadísticamente significativas en colesterol, frecuencia cardíaca, ejercicio, IMC y horas de sueño entre **hombres y mujeres**, **fumadores y no fumadores**, y **personas con y sin riesgo de infarto**.

Proyecto del curso Probabilidad y Estadística · Bioingeniería · Universidad de Antioquia (2025-2).

## Metodología

1. **Análisis exploratorio:** diagramas de cajas y bigotes para datos atípicos, media, mediana, forma de la distribución y nivel de variabilidad de cada variable.
2. **Verificación de supuestos:**
   - Normalidad con la prueba de **Kolmogorov-Smirnov**.
   - Homogeneidad de varianzas con la prueba de **Levene**.
3. **Transformación de variables:** como varias variables siguen una distribución uniforme (donde Box-Cox no funciona), se usó `QuantileTransformer` de scikit-learn para llevarlas a una distribución normal.
4. **Prueba de hipótesis:**
   - **Prueba t para dos muestras** cuando los supuestos se cumplieron tras la transformación.
   - **U de Mann-Whitney** (no paramétrica) cuando no se logró la normalidad.

## Resultados

Valores p obtenidos (nivel de significancia α = 0,05):

| Variable | Hombres vs. mujeres | Fumadores vs. no fumadores | Con vs. sin riesgo de infarto |
| --- | --- | --- | --- |
| Colesterol | 0,8914 (t) | 0,1214 (U) | 0,9893 (U) |
| Frecuencia cardíaca | 0,3079 (U) | 0,2490 (U) | 0,6802 (U) |
| Horas de ejercicio por semana | 0,9890 (t) | 0,9997 (t) | 0,9960 (t) |
| IMC | 0,9947 (t) | 0,9978 (t) | 0,9971 (t) |
| Horas de sueño por día | 0,6096 (U) | 0,6089 (U) | 0,0838 (U) |

*(t) prueba t · (U) U de Mann-Whitney*

**Conclusión:** en ninguna comparación se rechaza la hipótesis nula, es decir, no se encontraron diferencias estadísticamente significativas entre los grupos. Las distribuciones casi uniformes de las variables y la ausencia de diferencias sugieren que el conjunto de datos podría ser sintético, por lo que estos resultados no deberían extrapolarse a la población real.

## Tecnologías

Python · pandas · NumPy · SciPy · statsmodels · scikit-learn · Matplotlib · seaborn · Jupyter

## Cómo ejecutarlo

```
pip install -r requirements.txt
jupyter notebook analisis_riesgo_cardiaco.ipynb
```

## Datos

[Heart Attack Risk Prediction Dataset](https://www.kaggle.com/datasets/iamsouravbanerjee/heart-attack-prediction-dataset), disponible públicamente en Kaggle.

## Autor

**Dumar Yesid Londoño Muñoz** · Estudiante de Ingeniería Biomédica, Universidad de Antioquia · [GitHub](https://github.com/YesidMunoz)
