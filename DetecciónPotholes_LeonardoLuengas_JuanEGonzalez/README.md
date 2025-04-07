## README COÑO
# 🕳️ Proyecto de Detección de Huecos en las Vías

¡Epa! Este proyecto lo armamos pa' detectar huecos en las calles usando visión por computador. Sí, de esos huecos que parecen piscinas olímpicas cuando llueve, que uno esquiva como si estuviera jugando Mario Kart.

La idea es que el sistema vea una imagen o un video de una calle y te diga: "Mira, ahí hay un hueco". Todo eso gracias a modelos de inteligencia artificial que entrenamos con imágenes reales. Este proyecto es un granito de arena pa’ que en algún momento tengamos calles sin tantos tumbos.

---

## 📌 ¿Y cómo funciona la cosa?

Mira, te lo explico con calma:

1. **Reunimos imágenes de huecos**: buscamos y tomamos fotos de calles con huecos (de aquí y de afuera).
2. **Etiquetamos los huecos**: o sea, le decimos al sistema "esto que ves aquí es un hueco". Eso lo hacemos con programas como Roboflow o LabelImg.
3. **Entrenamos un modelo inteligente**: usamos un modelo que ya viene pre-entrenado (como YOLOv5 o YOLOv8) y lo afinamos con nuestras imágenes pa’ que aprenda a reconocer huecos como los nuestros.
4. **Probamos el modelo**: le pasamos imágenes nuevas y vemos si detecta bien los huecos.
5. **Listo pa’ usar**: puedes correrlo en imágenes, videos o incluso conectarlo a una cámara y que te avise si ve un hueco en tiempo real.

Todo esto lo hicimos en Python, y usamos herramientas como OpenCV y PyTorch/TensorFlow. El entrenamiento lo hicimos en Colab porque, bueno… las GPU no crecen en los árboles 😅

---

## 🛠️ Tecnologías Utilizadas

- Python 🐍
- OpenCV
- YOLOv5 / YOLOv8 (según el modelo que uses)
- Google Colab (pa’ aprovechar las GPU gratis)
- NumPy, Pandas, Matplotlib (los panas de siempre)

---

## 📂 ¿Cómo está organizado el proyecto?

