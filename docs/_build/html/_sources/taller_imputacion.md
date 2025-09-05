# Taller de Imputación

## 1. Exploración inicial
- Carga, `head()`, `info()`, `describe()`.
- Identificar variables numéricas y categóricas.

## 2. Detección de valores faltantes
- Tabla con conteo y %.
- Gráfico de barras por variable con nulos.
- Visualización de patrón (matrix/correlación de faltantes).

## 3. Clasificación del mecanismo de ausencia
- Hipótesis MCAR/MAR/MNAR por variable con justificación breve.

## 4. Imputación
- Numéricas: Mediana, KNN (k=5), Iterative/Regresión (ejemplos).
- Categóricas: Moda, imputación por grupo si aplica.

## 5. Evaluación
- Comparar distribuciones antes/después: KS, t-test/Mann–Whitney.
- Normalidad (Shapiro en muestras).
- Comentarios sobre sesgos introducidos.
