# Twitter-Scrapping — Sentiment Analysis en Español  

El ejercicio implementa un flujo completo de *análisis de sentimientos* en mensajes cortos en español utilizando técnicas de *Procesamiento de Lenguaje Natural (NLP)* y algoritmos de *clasificación supervisada*.  

## Dataset  
El análisis se fundamenta en un conjunto de datos diseñado para el estudio de sentimientos en mensajes escritos en español, utilizando el dataset público [Sentiment Analysis in Spanish Tweets](https://www.kaggle.com/datasets/philipsanm/sentiment-analysis-in-spanish-tweets/data), que contiene *2590 registros* extraídos desde la red social Twitter.  

Cada registro incluye:  
- `user`: identificador del usuario que envió el mensaje corto.  
- `text`: mensaje en español.  
- `date`: fecha y hora del mensaje.  
- `emotion`: emoción del mensaje, una de 20 posibles emociones.  
- `sentiment`: sentimientos asociados y definidos según el Dataset y que contempla `{ joyful, mad, peaceful, powerful, sad, scared }`.  

## Metodología  
La metodología aplicada inicia con un proceso de preprocesamiento del texto que permite normalizar y preparar los mensajes antes de su vectorización y clasificación. A continuación, se describe cada etapa:  

1. **Preprocesamiento del texto**  
Para el análisis se realizaron las siguientes tareas:  
   - Eliminar campos que no son requeridos.  
   - Contar la frecuencia de las clases, columna `sentiment` y mostrarla en un gráfico.  
   - Conversión a minúsculas.  
   - Eliminación de caracteres no alfabéticos.  
   - Tokenización y eliminación de *stopwords* en español, basados en lista de stopwords publicada en [Stop words in 28 languages](https://www.kaggle.com/datasets/heeraldedhia/stop-words-in-28-languages) [5].  
   - Aplicación del *Snowball Stemmer* para español.  

2. **Vectorización**  
Los textos se transforman en representaciones numéricas utilizando la técnica *bag-of-words*, lo que permite a los algoritmos trabajar con los datos en un espacio vectorial.  

3. **Clasificación**  
El proceso utilizó tres algoritmos que son muy conocidos y usados en tareas de aprendizaje supervisado:  
   - *Naive Bayes*: clasificador probabilístico basado en el teorema de Bayes, eficiente para problemas de texto.  
   - *Regresión Logística*: modelo lineal que estima la probabilidad de pertenencia a una clase, ampliamente usado en clasificación binaria y multiclase.  
   - *Support Vector Machines (SVM)*: método robusto que busca maximizar los márgenes de separación entre clases en un espacio de alta dimensión.  

Cada modelo se aplica tanto al texto limpio como al texto reducido mediante *stemming*.  

4. **Evaluación**  
El desempeño de los modelos se midió bajo los siguientes criterios:  
   - División de datos: 75% entrenamiento / 25% prueba.  
   - Métricas: *accuracy, precisión, recall, F1-score*.  
   - Comparación entre seis experimentos y análisis del impacto del *stemming* en el rendimiento.  

## Resultados  
El análisis comparativo de los modelos permitió identificar los siguientes hallazgos principales:  

- *Mejor modelo*: SVM con texto limpio (accuracy ≈ 77%).  
- *Peor modelo*: Naive Bayes con texto stemmizado (accuracy ≈ 59%).  
- El *stemming* **no mejoró el rendimiento**, lo que confirma que en español puede distorsionar palabras y reducir la capacidad de clasificación.  

## Referencias bibliográficas  
[1] C. D. Manning, P. Raghavan, and H. Schütze, *Introduction to Information Retrieval*. Cambridge, U.K.: Cambridge Univ. Press, 2008.  
[2] S. Bird, E. Klein, and E. Loper, *Natural Language Processing with Python*. Sebastopol, CA, USA: O’Reilly Media, 2009.  
[3] F. Pedregosa et al., “Scikit-learn: Machine Learning in Python,” *J. Mach. Learn. Res.*, vol. 12, pp. 2825–2830, 2011.  
[4] P. San Martín, “Sentiment Analysis in Spanish Tweets,” Kaggle, 2020. [Online]. Available: https://www.kaggle.com/datasets/philipsanm/sentiment-analysis-in-spanish-tweets/data  
[5] H. Dedhia, “Stop words in 28 languages,” Kaggle, 2018. [Online]. Available: ht
