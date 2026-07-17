# Clasificador de Platos de Comida para FoodSnaps (Food101)

¡Bienvenido! Este repositorio contiene el desarrollo y entrenamiento de un modelo de Deep Learning capaz de clasificar con éxito **101 tipos distintos de platos de comida**, diseñado como solución al reto logístico y de contenido de la plataforma ficticia **FoodSnaps**.

## 📊 Contexto de Negocio & Reto
* **Situación:** FoodSnaps cuenta con más de 800 restaurantes activos, cada uno de los cuales sube un promedio de 12 platos nuevos por semana.
* **El Reto:** Desarrollar un modelo automatizado de visión por computadora que clasifique con éxito cada plato nuevo subido por los restaurantes para optimizar el etiquetado y la indexación en la plataforma.
* **Resultado Final:** El modelo desarrollado logra un **76% de precisión (Accuracy)** entre 101 clases diferentes de comida utilizando el popular dataset *Food101*.

---

## 🛠️ Enfoque Técnico y Arquitectura

El desarrollo se realizó utilizando **TensorFlow** y **Keras**, aprovechando técnicas de Aprendizaje por Transferencia (Transfer Learning):

1. **Dataset:** Food101 (75,750 imágenes de entrenamiento, 25,250 de validación).
2. **Arquitectura Base:** `ResNet50` preentrenada con ImageNet.
3. **Estrategia de Entrenamiento:**
   * **Feature Extraction (10 épocas):** Congelación de la base convolucional y entrenamiento exclusivo del nuevo clasificador acoplado (Learning Rate: 0.0017).
   * **Fine-Tuning (5 épocas):** Descongelamiento de las capas superiores de la red para ajustar los pesos fina y específicamente al dominio de alimentos (Learning Rate: 0.0001).
4. **Preprocesamiento:** Redimensión de imágenes a 224x224 píxeles y optimización del pipeline de datos con `tf.data` (Batch Size: 32).

---

## 📈 Resultados principales
* **Precisión global:** ~76% en el set de validación con las 101 clases.
* El pipeline incluye optimizaciones de callbacks como `EarlyStopping` y `ReduceLROnPlateau` para evitar el sobreajuste y asegurar la convergencia eficiente.

---

## 📂 Contenido del Repositorio
* `notebooks/`: Contiene el Jupyter Notebook principal con todo el proceso de carga, exploración de datos, ingeniería de características, entrenamiento del modelo y evaluación mediante matrices de confusión.

---

## 💻 Requisitos para Ejecución Local
Si deseas clonar este repositorio y ejecutar el notebook localmente o en Google Colab, asegúrate de contar con:
* TensorFlow 2.19.0+
* TensorFlow Datasets (`tfds`)
* Matplotlib, Pandas, NumPy, Seaborn, Scikit-learn
