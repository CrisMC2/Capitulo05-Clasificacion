# Resumen

Este trabajo presenta los métodos de clasificación del capítulo 5 del libro *Practical Statistics for Data Scientists* (Bruce, Bruce y Gedeck, 2020). La clasificación es una tarea del aprendizaje supervisado en la que un modelo, entrenado con casos cuyo resultado ya se conoce, predice a qué categoría pertenece un caso nuevo. En general la respuesta es binaria (1 o 0) y el modelo entrega una probabilidad que se convierte en decisión mediante un punto de corte.

Se estudian tres métodos. Naive Bayes estima la probabilidad de cada clase a partir de las probabilidades de cada variable, bajo el supuesto de que las variables son independientes entre sí. El Análisis Discriminante busca la combinación lineal de variables que mejor separa a los grupos, a partir de la matriz de covarianza (discriminante lineal de Fisher). La Regresión Logística adapta la regresión lineal a una respuesta binaria mediante la función logit, se ajusta por máxima verosimilitud y se interpreta con odds ratios.

Para decidir qué tan bueno es un modelo no basta con contar los aciertos. Se presenta la matriz de confusión y las métricas que se derivan de ella (exactitud, precisión, recall, especificidad y F1), la curva ROC con su AUC, y la curva de precisión-recall y el lift, que resultan más informativos cuando las clases están desbalanceadas. Finalmente se revisan las estrategias para trabajar con una clase muy poco frecuente, como el fraude: submuestreo, sobremuestreo, ponderación de casos y ajuste del punto de corte.

La conclusión principal es que no existe un método ni una métrica universalmente mejor. La elección depende de la interpretabilidad que se necesite, del desbalance de las clases y del costo relativo de cada tipo de error.

**Palabras clave:** clasificación, Naive Bayes, análisis discriminante, regresión logística, matriz de confusión, curva ROC, datos desbalanceados.
