#  *Modulo4* 

### *Nombres:*
1. DANIEL SANIN RAMIREZ
2. JULIANA MEDINA GUERREO
3. JESSICA VIVIANA MARTINEZ MARIN
4. ANDRES FELIPE GARCIA TURRIAGO

# 

## *Amazon Polarity Dataset - Análisis de Sentimientos*


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

#
## Conclusiones del Proyecto

La implementación de la regresión logística junto con la vectorización TF-IDF ha demostrado ser una solución efectiva para la clasificación de sentimientos en el conjunto de datos de reseñas de Amazon, logrando un modelo con alta precisión y capacidad de generalización para diferenciar opiniones positivas y negativas. Sin embargo, presenta limitaciones en la detección de sarcasmo e ironía, lo que puede afectar la interpretación de algunas reseñas. La limpieza y normalización de los datos textuales, incluyendo la conversión a minúsculas, la eliminación de caracteres especiales y espacios redundantes, fueron claves para mejorar la calidad de los datos y el desempeño del modelo. Además, la integración de MLflow permitió un seguimiento eficiente de los experimentos, facilitando la comparación de configuraciones y asegurando la reproducibilidad de los resultados. 

A pesar de los buenos resultados obtenidos, se pueden explorar técnicas avanzadas como modelos basados en redes neuronales o transformers para mejorar la precisión y la capacidad de generalización, mientras que la ampliación del conjunto de datos con más ejemplos podría reducir sesgos y aumentar la robustez del sistema. 

Este enfoque es escalable y adaptable a otros dominios, como el análisis de opiniones en redes sociales o la detección de tendencias de mercado, convirtiéndolo en una herramienta valiosa para diversas aplicaciones.


- *Fuente del Dataset*:
  El dataset completo está disponible en *Hugging Face*: https://huggingface.co/datasets/SetFit/amazon_polarity

