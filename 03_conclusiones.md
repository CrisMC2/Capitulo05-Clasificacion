# Conclusiones

El estudio de los métodos de clasificación presentados en este capítulo permite extraer conclusiones sobre su importancia, efectividad y usos más frecuentes en la práctica del análisis de datos.

---

## Importancia de la clasificación en ciencia de datos

La clasificación es una de las tareas más comunes del aprendizaje supervisado. Su relevancia radica en que permite automatizar decisiones binarias que antes dependían exclusivamente del criterio humano, haciéndolo de forma rápida, reproducible y basada en evidencia. Los tres métodos estudiados —Naive Bayes, Análisis Discriminante y Regresión Logística— ofrecen distintos enfoques para un mismo problema: asignar cada caso a la clase más probable a partir de sus características observadas.

Una contribución transversal de este capítulo es que los modelos no se limitan a etiquetar casos como 0 o 1. Todos producen **probabilidades**, lo que permite ajustar el punto de corte según el costo de cada tipo de error. Esta flexibilidad es clave en contextos donde el costo de un falso negativo (no detectar un fraude, no diagnosticar una enfermedad) es mucho mayor que el de un falso positivo, o viceversa.

---

## Efectividad de cada método

### Naive Bayes
- Se apoya directamente en el **Teorema de Bayes** para calcular la probabilidad posterior de cada clase dado el valor de los predictores.
- Supone que las variables predictoras son **independientes entre sí**, lo que rara vez se cumple en la realidad. Sin embargo, el modelo suele comportarse bien en la práctica a pesar de esa simplificación.
- Es especialmente eficiente con datos de alta dimensionalidad como texto (correo electrónico, reseñas).
- Su principal limitación es precisamente el supuesto de independencia: si dos variables están fuertemente correlacionadas, el modelo puede sobreestimar o subestimar probabilidades.

### Análisis Discriminante Lineal (LDA)
- Es el clasificador estadístico más antiguo y uno de los más interpretables.
- Busca la combinación lineal de los predictores que **maximiza la separación entre grupos** (cociente de variación entre grupos versus variación dentro de grupos).
- En el ejemplo de préstamos con dos variables, alcanzó una exactitud del **62.9%**, identificando correctamente el 59% de los préstamos morosos y el 66.6% de los pagados.
- Supone que los datos siguen una distribución normal y que todos los grupos comparten la misma matriz de covarianza. El Análisis Discriminante Cuadrático (QDA) relaja ese segundo supuesto, aunque en el ejemplo no ofreció mejora significativa (62.4%).
- Hoy es menos utilizado que en su época de apogeo, pero sigue siendo útil para seleccionar variables y como introducción conceptual a técnicas más modernas.

### Regresión Logística
- Es uno de los métodos de clasificación **más populares** por su velocidad de cálculo y la facilidad de interpretar sus resultados.
- Transforma la probabilidad a través del **logit** (log odds) para construir un modelo lineal en una escala sin límites, y luego regresa al espacio de probabilidades con la función sigmoide.
- Los coeficientes se interpretan directamente como **odds ratios**: por ejemplo, en el conjunto de préstamos, los destinados a pequeños negocios tienen 3.4 veces más odds de impago que los de tarjeta de crédito; los prestatarios con el mejor puntaje tienen 100 veces menos riesgo que los peores.
- El modelo se ajusta por **Máxima Verosimilitud** (MLE), un proceso iterativo sin solución cerrada, lo que lo diferencia de la regresión lineal.
- El modelo de préstamos obtuvo un **AUC de 0.69**: mejor que el azar, pero en el rango "débil-aceptable", lo que indica que el problema de clasificación de riesgo crediticio tiene una complejidad inherente que ningún método sencillo resuelve completamente.

---

## Evaluación: más allá de contar aciertos

Un hallazgo central de este capítulo es que la **exactitud (accuracy) es una métrica insuficiente** para evaluar clasificadores, especialmente cuando las clases están desbalanceadas. Un modelo que siempre prediga "pagado" en un dataset donde el 81% de los préstamos se pagan tendría una exactitud del 81% sin haber aprendido nada útil.

Las herramientas correctas son:

| Herramienta | Cuándo usarla |
|---|---|
| **Precisión y Recall** | Cuando importa el tipo de error (FP vs. FN) |
| **F1-score** | Para comparar modelos con una sola cifra balanceada |
| **Curva ROC y AUC** | Para evaluar el modelo en todos los puntos de corte |
| **Curva Precisión-Recall** | Cuando la clase positiva es rara |
| **Lift** | Cuando los recursos para actuar son limitados |

La elección de la métrica no es técnica sino de negocio: depende de qué tipo de error es más costoso en el problema concreto.

---

## Datos desbalanceados

En la mayoría de aplicaciones reales, la clase de interés (fraude, mora, enfermedad) es la más rara. Las estrategias para manejar este problema son:

- **Submuestreo:** reduce los registros de la clase mayoritaria. En el ejemplo de préstamos, equilibrar al 50/50 cambió las predicciones de 0.39% de mora (con datos completos) a aproximadamente el 50%, mucho más realista.
- **Sobremuestreo y SMOTE:** genera nuevos ejemplos sintéticos de la clase minoritaria por interpolación.
- **Ponderación de clases:** penaliza más los errores sobre la clase rara durante el entrenamiento.
- **Ajustar el punto de corte:** la opción más simple; bajar el umbral de 0.5 a 0.3 captura más casos positivos a costa de más falsas alarmas.

---

## Usos comunes

| Método | Aplicaciones típicas |
|---|---|
| **Naive Bayes** | Filtros de spam, detección de phishing, clasificación de texto, diagnóstico médico asistido |
| **Análisis Discriminante** | Evaluación de riesgo crediticio, clasificación de especies, diagnóstico clínico por biomarcadores, segmentación de clientes |
| **Regresión Logística** | Scoring de crédito, detección de fraude, predicción de abandono de clientes (churn), modelos epidemiológicos binarios |

---

## Reflexión final

Los tres métodos estudiados son complementarios, no competidores. El Análisis Discriminante es útil como punto de partida y para seleccionar variables. La Regresión Logística ofrece el mejor balance entre interpretabilidad y rendimiento para datos mixtos. Naive Bayes destaca en problemas con muchas variables y datos textuales. En la práctica, la elección depende del tipo de datos, del tamaño del dataset, de los supuestos que se está dispuesto a aceptar y, sobre todo, del costo relativo de cada tipo de error en el contexto del problema.
