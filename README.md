# Proyecto ciencia de datos - Prediccion valor MCD
## Como ejecutar
Version de [Python 3.8.8](https://www.python.org/downloads/release/python-388/).

Cargar documento de requerimientos:
```
pip install -r requirements.txt
```
## Como funciona

### Analisis Factorial
Recibe como input 10 valores de 'Close' de acciones consideradas relevantes para el aumento o disminucion de MCD, en plazos de 1 mes de los ultimos 6 años, es decir, un total de 72 meses de datos.

Las acciones utilizadas fueron extraidas de [Yahoo Finance](https://finance.yahoo.com/) y son las siguientes:

-   SYY
-	JBSAY
-	IP
-	YUM
-	KHC
-	ADM
-	BG
-	HRL
-	TSN
-	XOM

Se realiza un analsis factorial de dichas acciones y se determina que acciones son representativas para el valor de MCD.

### Modelo Convolucional
Una vez definidas las acciones relevantes se elabora un modelo predictivo, recibe datos de series temporales en formato tridimensional.
Divide los datos en entrenamiento (80%) y prueba (20%).
La arquitectura incluye una capa Conv1D con 32 filtros para detectar patrones locales, seguida de Flatten para transformar a una dimensión, luego una capa densa de 64 neuronas con activación ReLU y una capa de salida con una sola neurona para predecir un valor continuo.
Se compila con optimizador Adam y pérdida MSE.
Entrena durante 50 épocas con batch size de 8.

### Resultados
En cuanto a los resultados, parecen prometedores. Se acerca bastante al valor esperado, con un aproximado de 0.58% de error.

```
1/1 [==============================] - 0s 27ms/step
Prediccion desescalada: 310.63
Prediccion esperada: 308.83
```