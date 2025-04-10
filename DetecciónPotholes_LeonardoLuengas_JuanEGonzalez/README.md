# Reporte Parcial 2
Realizado por Juan Esteban Gonzalez y Leonardo Luengas para la clase de Introducción a la Visión por Computadora de la carrera de Matemáticas Aplicadas y Ciencias de la Computación.

## ⚠️IMPORTANTE⚠️
Para correr el notebook es **necesario** subir un archivo "kaggle.json" que tenga las credenciales de kaggle para poder usar la API y traer el dataset con el que vamos a trabajar. La segunda celda de código
  ```
    from google.colab import files
    files.upload()
  ```
recibe este archivo y no va a correr el resto del notebook hasta que se suban las credenciales.
## Resumen del Proyecto
Este proyecto busca entrenar un modelo de Aprendizaje No Supervizado en la detección de huecos en calles y carreteras. El objetivo del modelo es determinar si dentro de una imagen de una calle o una carretera hay algún tipo de hueco. Para esto utilizamos un dataset de 681 imágenes donde alrededor del 50% (329 imágenes) de las imágenes corresponden a calles con huecos y el resto de las imágenes (352 imágenes) corresponden a calles sin huecos. Este dataset se encuentra en el siguiente [url](https://www.kaggle.com/datasets/atulyakumar98/pothole-detection-dataset).

Implementamos un modelo de Gaussian Mixture con dos componentes correspondientes a cada clase del problema de detección de huecos. Después de optimizar los hiperparámetros del modelo, estos fueron los resultados:
|                |precision  |  recall | f1-score  | support|
|----------------|----------|----------|-----------|--------|
|          0    |   0.62  |    0.74  |    0.68  |     116|
|           1    |   0.66   |   0.52   |   0.58     |  109|
|    accuracy    |          |          |   0.64   |    225|
|   macro avg     |  0.64    |  0.63   |   0.63      | 225|
|weighted avg     |  0.64    |  0.64    |  0.63     |  225|


A continuación discutiremos a profundidad estos resultados.

## Desarrollo del Proyecto
