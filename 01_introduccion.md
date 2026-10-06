# Introducción

Todos los días se toman decisiones que se reducen a elegir entre dos opciones: aprobar o rechazar un préstamo, marcar un correo como spam o dejarlo en la bandeja de entrada, saber si un cliente seguirá usando un servicio o lo abandonará. En ciencia de datos, este tipo de problema se llama **clasificación**, y es una de las tareas más comunes y útiles del análisis de datos.

La clasificación forma parte del **aprendizaje supervisado**. Esto quiere decir que primero se entrena un modelo con datos de los que ya conocemos el resultado (por ejemplo, préstamos que sabemos si se pagaron o no) y después se usa ese modelo para predecir el resultado de casos nuevos, cuyo desenlace todavía no conocemos. Normalmente la respuesta es binaria, es decir, solo tiene dos valores posibles, que se representan como 1 y 0. Aunque también existen problemas con más de dos categorías, como el filtro de Gmail que separa los correos en "Principal", "Social" o "Promociones".

Una idea importante del capítulo es que la mayoría de los modelos no entregan solo una etiqueta, sino una **probabilidad**: qué tan probable es que un caso pertenezca a la clase que nos interesa. Para convertir esa probabilidad en una decisión se usa un **punto de corte**. Por ejemplo, si el corte es 0.5 y el modelo calcula que un préstamo tiene una probabilidad de 0.7 de no pagarse, lo clasificamos como "no pagado". Si subimos el punto de corte, el modelo será más exigente y marcará menos casos como 1; si lo bajamos, marcará más.

## Importancia y aplicaciones

Los métodos de clasificación son importantes porque permiten automatizar decisiones que antes dependían solo del criterio de una persona, y hacerlo de forma rápida y con base en datos. Algunas aplicaciones comunes son:

- **Finanzas:** evaluar el riesgo de que un cliente no pague un crédito y detectar transacciones fraudulentas.
- **Salud:** apoyar el diagnóstico de enfermedades a partir de exámenes y síntomas.
- **Marketing:** predecir qué clientes responderán a una campaña o cuáles podrían dejar la empresa.
- **Seguridad informática:** identificar correos de spam o intentos de phishing.

## Métodos que se estudian

En este trabajo se revisan tres métodos clásicos de clasificación, junto con las herramientas para evaluarlos:

1. **Naive Bayes:** usa probabilidades y supone que las variables son independientes entre sí.
2. **Análisis Discriminante:** busca la combinación de variables que mejor separa a los grupos.
3. **Regresión Logística:** adapta la regresión lineal para predecir la probabilidad de un resultado de sí o no.

Además, se explica cómo medir si un modelo clasifica bien (no basta con contar los aciertos) y qué hacer cuando una de las clases es mucho menos frecuente que la otra, como ocurre con el fraude.

## Objetivos

**Objetivo general:** describir y aplicar los principales métodos de clasificación presentados en el capítulo 5 del libro *Practical Statistics for Data Scientists*.

**Objetivos específicos:**

1. Explicar el funcionamiento de Naive Bayes, el Análisis Discriminante y la Regresión Logística.
2. Aplicar estos métodos a un mismo conjunto de datos de préstamos usando Python.
3. Evaluar los modelos con métricas como la matriz de confusión, la sensibilidad, la precisión y la curva ROC.
4. Revisar estrategias para trabajar con datos desbalanceados.

## Estructura del trabajo

El desarrollo se divide en cinco partes. Las tres primeras presentan los métodos de clasificación: Naive Bayes (2.1), Análisis Discriminante (2.2) y Regresión Logística (2.3). La sección 2.4 explica cómo evaluar y comparar estos modelos, y la sección 2.5 trata las estrategias para datos desbalanceados. Al final se presentan las conclusiones y la bibliografía consultada.
