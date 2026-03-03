# Detección de Postura con MediaPipe y Control de LEDs con Arduino

Este proyecto utiliza el modelo **Pose Landmark Detection** de MediaPipe para identificar si una persona está de pie o sentada, enviando una señal a un Arduino para controlar indicadores físicos (LEDs).

## 1. Análisis del Código y Funciones Relevantes
* **MediaPipe Pose:** Se utiliza para obtener las coordenadas (landmarks) de los puntos clave del cuerpo.
* **Procesamiento de Coordenadas:** Las funciones más relevantes analizan la posición de la cadera (`HIP`) respecto a las rodillas (`KNEE`) o la altura total para determinar el estado.
* **Comunicación Serial:** Se emplea la librería `pyserial` (o similar) para enviar datos del script de Python al Arduino.

## 2. Lógica de Detección (Etiquetado)
Se desarrolló una lógica basada en umbrales de coordenadas $y$. 
* Si la distancia vertical entre la cadera y el talón es mayor a $X$, la etiqueta muestra **"Parado"**.
* De lo contrario, la etiqueta cambia a **"Sentado"**.

## 3. Integración con Arduino
El hardware reacciona en tiempo real:
* **Persona parada:** Arduino recibe el carácter '1' -> Enciende **LED Rojo**.
* **Persona sentada:** Arduino recibe el carácter '0' -> Enciende **LED Verde**.

## 4. Requisitos
* Python 3.x
* MediaPipe, OpenCV, PySerial
* Arduino IDE (para cargar el sketch al microcontrolador)
