# Reporte Parcial 2
Realizado por Juan Esteban Gonzalez y Leonardo Luengas para la clase de Introducción a la Visión por Computadora de la carrera de Matemáticas Aplicadas y Ciencias de la Computación.

## ⚠️IMPORTANTE⚠️
Para correr el notebook es **necesario** subir un archivo "kaggle.json" que tenga las credenciales de kaggle para poder usar la API y traer el dataset con el que vamos a trabajar. La segunda celda de código
  ```python
    from google.colab import files
    files.upload()
  ```
recibe este archivo y no va a correr el resto del notebook hasta que se suban las credenciales.
## Resumen del Proyecto
Este proyecto busca entrenar un modelo de Aprendizaje No Supervizado en la detección de huecos en calles y carreteras. El objetivo del modelo es determinar si dentro de una imagen de una calle o una carretera hay algún tipo de hueco. Para esto utilizamos un dataset de 681 imágenes donde alrededor del 50% (329 imágenes) de las imágenes corresponden a calles con huecos y el resto de las imágenes (352 imágenes) corresponden a calles sin huecos. Este dataset se encuentra en la siguiente [URL](https://www.kaggle.com/datasets/atulyakumar98/pothole-detection-dataset).

Implementamos un modelo de Gaussian Mixture con dos componentes correspondientes a cada clase del problema de detección de huecos. Después de optimizar los hiperparámetros del modelo, estos fueron los resultados:
|                |precision  |  recall | f1-score  | support|
|----------------|----------|----------|-----------|--------|
|          0    |   0.69  |    0.75  |    0.72  |     112|
|           1    |   0.73   |   0.66   |   0.69     |  113|
|    accuracy    |          |          |   0.71   |    225|
|   macro avg     |  0.71    |  0.71   |   0.71      | 225|
|weighted avg     |  0.71    |  0.71    |  0.71     |  225|


A continuación discutiremos a profundidad estos resultados.

## Desarrollo del Proyecto
### Pipeline de Preprocesamiento
Nuestro pipeline de preprocesamiento consiste de 4 pasos.
1. ``DownScale()`` que se encarga de reducir el tamaño de todas las imágenes a 512x512 pixeles. Esto fue necesario dado que el tiempo de preprocesamiento para las imágenes con resolución original era demasiado largo y colapsaba la RAM del sistema.
2. ``ToGrayscale()`` que le aplica a las imágenes un filtro de blanco y negro.
3. ``GaussianBlur()`` que aplica un filtro gaussiano de kernle 5x5 y una desviación de 1. Encontramos que era necesario realizar este filtrado dado que la calle presentaba pequeñas irregularidades que hacían que el modelo no se enfocara en detectar el hueco. De esta forma, eliminamos el ruido dentro de la imágen sin eliminar los detalles importantes que queremos que el modelo identifique.
4. ``ApplyCanny()`` que aplica un filtro de Canny a las imágenes. Nuestro razonamiento detrás fue pensar en que el modelo tenía que detectar solamente la presencia de la *silueta* de un hueco, olvidando el resto de los detalles que pueden estar presentes en la escena.
### Pipeline de Feature Detection y Embedding
Nuestro pipeline de Feature Detection y Embedding solo implementa el algoritmo de SIFT para extraer los descriptores de la escena y el algoritmo de Bag of Visual Words para generar un embedding de menor dimensión (10) que capture las características comunes de las imágenes.

Para explorar este embedding utilizamos el algoritmo de PCA restrigindo a dos y tres componentes principales respectivamente para poder comprender la forma que tiene el embedding. N
