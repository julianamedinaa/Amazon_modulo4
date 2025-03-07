#  *Modulo4* 

### *Nombres:*
1. DANIEL SANIN RAMIREZ
2. JULIANA MEDINA GUERREO
3. JESSICA VIVIANA MARTINEZ MARIN
4. ANDRES FELIPE GARCIA TURRIAGO

# 

## *Amazon Polarity Dataset - Análisis de Sentimientos*

- *Fuente del Dataset*:
  El dataset completo está disponible en *Hugging Face*: https://huggingface.co/datasets/SetFit/amazon_polarity

### Descripción

El *Amazon Polarity Dataset* es un conjunto de datos de clasificación de texto que contiene reseñas de productos de Amazon etiquetadas como *positivas (1)* o *negativas (0)*. 

Este dataset se utiliza comúnmente en tareas de *análisis de sentimientos* en Procesamiento de Lenguaje Natural (NLP). El dataset fue extraído de revisiones de productos de Amazon y transformado en una tarea de clasificación binaria.

## *Características del Dataset*
- *Número total de reseñas utilizadas: **200* (extraídas de train y test)
- *90% para entrenamiento* 
- *10% para prueba*

- *Etiquetas*:
  - 1: Reseña positiva
  - 0: Reseña negativa
- *Columnas disponibles*:
  - label: (0 = negativo, 1 = positivo)
  - title: Título de la reseña
  - text: Cuerpo de la reseña
  - split: Indica si pertenece a train o test

#
Para abordar este problema, existen diversos modelos de aprendizaje automático que pueden entrenarse con los datos disponibles, cada uno con sus propias ventajas y desventajas.

Uno de los modelos más utilizados para este tipo de tarea es la *Regresión Logística*, la cual se emplea en problemas de clasificación binaria porque su salida es una probabilidad. Para lograr esto, utiliza la función sigmoide, que transforma la salida en un valor entre 0 y 1, lo que permite asignar una categoría a cada reseña. Sus ventajas son la simplicidad y eficiencia cuando los datos son linealmente separables, es decir, cuando existe una frontera clara entre las clases. Sin embargo, su desventaja es que no maneja bien relaciones no lineales en los datos, lo que puede afectar su desempeño si las reseñas contienen patrones más complejos.

Otra opción adecuada para el análisis de sentimientos es el modelo de *Máquinas de Soporte Vectorial (SVM)*, que encuentra un hiperplano óptimo para separar las clases en el espacio de características. Lo interesante de este modelo es que puede utilizar diferentes núcleos para adaptar la clasificación a datos no lineales, como el núcleo RBF (Radial Basis Function) o el polinomial. SVM es particularmente útil en el procesamiento de textos, ya que funciona bien cuando se combinan con técnicas como TF-IDF para representar las palabras de las reseñas en forma numérica. Su principal ventaja es que logra una clasificación robusta incluso en datos complejos, pero su desventaja radica en que puede ser computacionalmente costoso, especialmente cuando el volumen de datos es grande.

Por otro lado, los *Árboles de Decisión* ofrecen un enfoque diferente, basado en la división de los datos en ramas según ciertas condiciones en las características, lo que forma una estructura similar a un árbol. Este modelo es especialmente útil porque es fácil de interpretar, lo que permite visualizar de manera clara cómo se toman las decisiones en la clasificación de las reseñas. Además, los árboles de decisión pueden capturar relaciones no lineales en los datos. Sin embargo, presentan una desventaja importante: tienden a sobreajustarse si no se aplica un proceso de poda o regularización adecuado, lo que puede afectar su capacidad de generalización en datos nuevos.

### Metricas de Regresion logistica ###
![image](https://github.com/user-attachments/assets/ca6894e6-c9d4-4509-a55c-043543e4fba5)

### Curva de aprendizaje de Regresion logistica ###
![image](https://github.com/user-attachments/assets/1b4f934d-2538-4f02-8f56-6f649fc650e0)


### Metricas de evaluacion SVM ###
![image](https://github.com/user-attachments/assets/cfc5689a-0c82-4f12-a5a3-2ad12bc61064)

### Curva de aprendizaje de SVM ###
![image](https://github.com/user-attachments/assets/f0fcba5c-7635-4f0d-b6d6-0fbb8fd4bc3e)


### Metricas de evaluacion Arbol de decision ###
![image](https://github.com/user-attachments/assets/4bbd13fc-02db-48d3-88c7-5495e746fc38)

### Curva de aprendizaje de Arbol de decision ###
![image](https://github.com/user-attachments/assets/8b66d5c6-5af7-415f-b877-7acb991e2150)




## Conclusiones del Proyecto

La implementación de la regresión logística junto con la vectorización TF-IDF ha demostrado ser una solución efectiva para la clasificación de sentimientos en el conjunto de datos de reseñas de Amazon, logrando un modelo con alta precisión y capacidad de generalización para diferenciar opiniones positivas y negativas. Sin embargo, presenta limitaciones en la detección de sarcasmo e ironía, lo que puede afectar la interpretación de algunas reseñas. Como bien se dijo, la regresion logisitica es un buen punto de partida, pero su variabilidad en la curva de aprendizaje sugiere que se pondría mejora su generalizacion. En comparacion, la precision parece ser silimar en los tres modelos, lo que sugiere que todos estan desempeñadose de manera comparable en terminos de clasificaicon general. La limpieza y normalización de los datos textuales, incluyendo la conversión a minúsculas, la eliminación de caracteres especiales y espacios redundantes, fueron claves para mejorar la calidad de los datos y el desempeño del modelo. Además, la integración de MLflow permitió un seguimiento eficiente de los experimentos, facilitando la comparación de configuraciones y asegurando la reproducibilidad de los resultados. 

## Consideraciones a mejorar ##

- El modelo de Árbol de Decisión entrenado con el criterio de "gini", una profundidad máxima de 5 y una semilla aleatoria de 42 proporciona un equilibrio entre interpretabilidad y rendimiento. Sin embargo, para mejorar su desempeño, se podrían probar otras configuraciones como aumentar max_depth para capturar más patrones complejos, cambiar el criterio a "entropy" para evaluar mejor la pureza de los nodos, y ajustar min_samples_split o min_samples_leaf para evitar el sobreajuste. También, técnicas como la poda post-entrenamiento o el uso de modelos ensamblados como Random Forest podrían mejorar la generalización del modelo.

- El modelo de Support Vector Machine (SVM) entrenado con un kernel lineal y un parámetro de regularización 
𝐶=1.0 ofrece una buena capacidad de generalización en datos linealmente separables. Sin embargo, para mejorar su rendimiento, se podrían probar otros valores de C para encontrar el mejor equilibrio entre sesgo y varianza, así como utilizar kernels más complejos como rbf o poly en caso de que los datos no sean linealmente separables. Además, la optimización de hiperparámetros mediante búsqueda en cuadrícula (GridSearchCV) o búsqueda aleatoria (RandomizedSearchCV) podría ayudar a encontrar la configuración más óptima del modelo.


- A pesar de los buenos resultados obtenidos, se pueden explorar técnicas avanzadas como modelos basados en redes neuronales o transformers para mejorar la precisión y la capacidad de generalización, mientras que la ampliación del conjunto de datos con más ejemplos podría reducir sesgos y aumentar la robustez del sistema.  Este enfoque es escalable y adaptable a otros dominios, como el análisis de opiniones en redes sociales o la detección de tendencias de mercado, convirtiéndolo en una herramienta valiosa para diversas aplicaciones.


