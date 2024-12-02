# desafioAI
Desafio para el ramo Inteligencia Artificial
# Predicción de Potencia Generada por Paneles Solares utilizando Redes Neuronales

Este proyecto implementa dos modelos de redes neuronales (Feedforward Neural Network y Red Neuronal Siamesa) para predecir la potencia generada por paneles solares en función de variables ambientales como radiación solar, temperatura ambiente y temperatura del panel. 

## Requisitos

Antes de comenzar, asegúrate de que se cumplan los siguientes requisitos:

1. Una cuenta activa en Google.
2. Archivo de datos en formato CSV con las siguientes columnas:
   - `Potencia`: Variable objetivo (salida).
   - `Radiacion`: Variable de entrada.
   - `Temperatura`: Variable de entrada.
   - `Temperatura panel`: Variable de entrada.
3. Conexión a internet para cargar los datos y ejecutar el entorno en Google Colab.

## Pasos para usar el código en Google Colab

1. **Abrir Google Colab**
   - Ve a [Google Colab](https://colab.research.google.com).

2. **Subir el archivo de código**
   - Copia y pega el código proporcionado en una nueva celda de código o sube un archivo con el script.

3. **Instalar las dependencias**
   - Si no están instaladas, el script incluye la instalación de TensorFlow con el siguiente comando:
     ```python
     !pip install tensorflow
     ```

4. **Cargar y preprocesar los datos**
   - El código solicita cargar un archivo CSV directamente desde el dispositivo local usando:
     ```python
     from google.colab import files
     uploaded = files.upload()
     ```
   - Asegúrate de cargar el archivo correcto. El nombre del archivo se detectará automáticamente y los datos se preprocesarán eliminando valores negativos y escalando las variables de entrada.

5. **Dividir los datos**
   - Los datos se dividen en conjuntos de entrenamiento (70%), validación (15%) y prueba (15%) automáticamente.

6. **Entrenamiento de los modelos**
   - El código incluye dos arquitecturas:
     - **Feedforward Neural Network (FFNN):** Una red neuronal totalmente conectada para regresión.
     - **Red Neuronal Siamesa:** Diseñada para trabajar con pares de datos.
   - Ambos modelos se entrenan usando técnicas como *early stopping* para evitar sobreajuste.

7. **Evaluación**
   - Los modelos se evalúan en el conjunto de prueba y generan métricas como MSE, MAE y R².

8. **Visualización de resultados**
   - El código genera gráficos para visualizar la pérdida de entrenamiento y validación por épocas:
     ```python
     def plot_training(history, title):
         plt.figure(figsize=(12, 5))
         plt.plot(history.history['loss'], label='Train Loss')
         plt.plot(history.history['val_loss'], label='Validation Loss')
         plt.title(title)
         plt.xlabel('Epochs')
         plt.ylabel('Loss')
         plt.legend()
         plt.show()
     ```

## Ejecución completa
1. Ejecuta cada celda del script secuencialmente.
2. Revisa la salida de cada celda para validar que no hay errores.
3. Analiza las métricas y gráficos generados para evaluar el desempeño de los modelos.

## Notas
- Asegúrate de que los datos cumplan con los requisitos de formato y columnas.
- Puedes personalizar los hiperparámetros de los modelos, como las capas, activaciones y tasa de aprendizaje, dentro de las funciones `create_ffnn` y `create_siamese`.

## Métricas de referencia
Los resultados obtenidos en el conjunto de datos de ejemplo se resumen de la siguiente manera:
- **FFNN:**
  - MSE: 2.8019
  - MAE: 0.9408
  - R²: 0.7531
- **Red Neuronal Siamesa:**
  - MSE: 11.2122
  - MAE: 2.8881
  - R²: 0.0942

## Contribuciones
Este proyecto fue desarrollado como parte de un análisis de potencia generada por paneles solares, demostrando el uso de técnicas avanzadas de redes neuronales para tareas de predicción.
