# Oxford-IIIpet---clasificador
Este proyecto clasifica imágenes de diferentes razas de mascotas utilizando un modelo preentrenado (ResNet50) y Gradio para la interfaz de predicción.
"https://www.robots.ox.ac.uk/~vgg/data/pets/"

readme_content = """
Clasificador de Razas de Mascotas - Oxford-IIIT Pet Dataset

Este repositorio contiene el código y los archivos necesarios para entrenar y desplegar un modelo de clasificación de razas de mascotas usando el Oxford-IIIT Pet Dataset. El modelo utiliza ResNet50, un modelo preentrenado en ImageNet, que se ajusta para clasificar entre 37 razas de gatos y perros. Además, la interfaz de usuario ha sido implementada usando Gradio para facilitar la carga de imágenes y mostrar los resultados de la clasificación.

Contenido

- Descripción del Proyecto
- Características del Dataset
- Arquitectura del Modelo
- Entrenamiento y Evaluación
- Despliegue
- Requisitos
- Instrucciones de Uso
- Conclusiones y Limitaciones
- Trabajos Futuros

Descripción del Proyecto

Este proyecto tiene como objetivo entrenar un modelo de deep learning capaz de clasificar imágenes de gatos y perros en 37 diferentes razas. Utilizamos el Oxford-IIIT Pet Dataset para entrenar y ajustar un modelo ResNet50 preentrenado, y luego desplegamos la interfaz de predicción usando Gradio.

Características del Dataset

El Oxford-IIIT Pet Dataset contiene:

- Imágenes: Aproximadamente 200 imágenes por cada una de las 37 razas (25 razas de gatos y 12 razas de perros).
- Anotaciones: Cada imagen está etiquetada con la raza de la mascota, y contiene anotaciones de bounding box para la región de la cabeza, así como segmentaciones a nivel de píxel que separan el fondo y el objeto principal.
- Clases: Las imágenes de gatos comienzan con una letra mayúscula y las de perros con una letra minúscula.

Estructura del Dataset

- images/: Carpeta con todas las imágenes.
- annotations/: Contiene anotaciones de bounding box (XML) y segmentaciones de imágenes (trimaps).
- list.txt: Contiene la lista de todas las imágenes y sus respectivas clases.
- trainval.txt y test.txt: Divisiones en entrenamiento y prueba.

Arquitectura del Modelo

Usamos ResNet50 como modelo base preentrenado, eliminando la última capa densa y añadiendo nuevas capas personalizadas para ajustar el número de clases a las 37 razas del dataset.

Preprocesamiento

- Redimensionamiento de imágenes: Las imágenes fueron redimensionadas a 256x256 píxeles.
- Normalización: Los valores de los píxeles se normalizaron dividiéndolos por 255.
- Aumentación de datos: Aplicamos técnicas como rotación, desplazamiento y zoom para incrementar la variabilidad y evitar el sobreajuste.

Entrenamiento del Modelo

- Modelo preentrenado: Se utilizó ResNet50 preentrenado en ImageNet.
- Fine-tuning: Ajustamos las capas superiores de ResNet50 durante el entrenamiento, utilizando un optimizador Adam y una tasa de aprendizaje reducida.
- Hiperparámetros:
  - Batch size: 32
  - Learning rate: 0.0001
  - Épocas: 30

Evaluación del Modelo

Evaluamos el modelo en un conjunto de prueba separado y monitoreamos métricas como la precisión y pérdida. También implementamos ReduceLROnPlateau para reducir dinámicamente la tasa de aprendizaje cuando no se observan mejoras.

Despliegue

El modelo fue desplegado utilizando Gradio para crear una interfaz interactiva que permite al usuario cargar imágenes y recibir la predicción de la raza de la mascota.

Además, el despliegue fue realizado tanto en Google Colab (para un enlace temporal) como en Hugging Face Spaces para un acceso permanente.

Requisitos

Librerías

- tensorflow
- gradio
- matplotlib
- seaborn
- numpy
- Pillow

