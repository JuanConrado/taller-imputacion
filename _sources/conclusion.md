# Conclusión preliminar

**Resumen del proceso:**  
1. Exploración inicial de las variables.  
2. Detección y visualización de los valores faltantes.  
3. Clasificación de los faltantes (MCAR, MAR, MNAR).  
4. Discusión sobre imputabilidad y riesgos de imputar.  
5. Aplicación de diferentes técnicas de imputación.  
6. Evaluación estadística de la imputación.  
7. Conclusión preliminar con tabla resumen.

---

## Hallazgos clave

- La mayoría de los faltantes no son MCAR, sino **MAR** o incluso **MNAR** en variables críticas como `puntuacion_credito`.  
- Para las numéricas, **KNN** y **mediana** fueron más adecuados que la media.  
- En categóricas, la **moda por grupo** reduce distorsión.  
- Para series temporales (`demanda`), la **interpolación lineal** fue más realista que forward fill.

---

## Conclusión preliminar

La siguiente tabla resume el análisis de los valores faltantes en la base `base_imputacion_mixta_1000.csv`:

| Variable            | % Nulos | Tipo de ausencia | Método sugerido       | ¿Preserva distribución? | Comentario |
|---------------------|---------|------------------|-----------------------|--------------------------|------------|
| ingresos            | 12%     | MAR/MNAR         | KNN o Regresión       | Sí (KNN se aproxima bien) | Se asocia a sexo y crédito; cuidado con sesgos. |
| gasto_mensual       | 25%     | MAR              | Mediana / Regresión   | Parcial (mediana mejor que media) | Relacionado con ingresos y segmento. |
| puntuacion_credito  | 50%     | MNAR?            | KNN (parcial) / Eliminar | No (ningún método preserva bien) | Muy alto % de nulos; sesgo probable. |
| estado_civil        | 35%     | MAR              | Moda por grupo        | Sí (condicional) | Depende de factores demográficos. |
| sexo                | 2%      | MCAR             | Moda                  | Sí | Muy pocos nulos, baja afectación. |
| edad                | 3%      | MCAR             | Mediana               | Sí | Distribución estable tras imputar. |
| altura_cm           | 8%      | MAR              | Mediana               | Sí | Sin distorsiones grandes. |
| nivel_educativo     | 10%     | MAR              | Moda                  | Sí | Moda conserva proporciones principales. |
| ciudad              | 5%      | MAR              | Moda                  | Sí | Asociada con crédito, pero % bajo. |
| demanda             | 15%     | MAR              | Interpolación / Regresión | Parcial | Forward fill crea tramos planos, interpolación es más realista. |

---

## Reflexión final

- El proceso permitió **identificar, clasificar, imputar y evaluar** los valores faltantes de manera sistemática.  
- Los métodos de imputación **más simples (media, moda)** funcionan en casos con pocos nulos, pero distorsionan en variables clave.  
- Métodos como **KNN** o **interpolación** resultaron más eficaces para mantener la distribución original.  
- Este análisis es crucial antes de aplicar modelos predictivos, ya que garantiza mayor robustez y menor sesgo en los resultados.  

