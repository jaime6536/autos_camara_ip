Resumen del Proyecto

El sistema permite:

Conectarse a una cámara IP vía RTSP o HTTP.

Detectar autos en tiempo real.

Identificar el color predominante del vehículo.

Extraer una captura recortada del auto.

Calcular el nivel de confianza de la detección.

Registrar un historial completo de autos detectados.

Mostrar todo en un Dashboard Web usando Flask.

Arquitectura General

Cámara IP

Procesamiento (Python + OpenCV/YOLO)

Detector de autos

Identificador de color

Captura del auto

Registro del historial

Servidor Flask

Dashboard Web

Requisitos

Software

Python 3.8 o superior

OpenCV

Flask

Numpy

Cámara IP

Debe entregar video por RTSP o HTTP.

Hardware recomendado

Mini PC (Intel N100, Ryzen 3, Intel i5 o superior).

Cámaras recomendadas: Reolink RLC, Hikvision ColorVu, Dahua WizSense.

Detección de Autos

Modo básico (HaarCascade)

Rápido y simple.

Útil para prototipos.

Modo avanzado (YOLOv8 / YOLOv11)

Alta precisión.

Recomendado para uso real y situaciones de baja iluminación.

Detección de Color

El sistema analiza el área recortada del vehículo y clasifica colores comunes, como:

Rojo

Azul

Blanco

Negro

Otros tonos (gris, verde, etc.)

Se puede mejorar con técnicas más avanzadas si se requiere más precisión.

Captura del Auto

La captura del auto es una imagen recortada exclusivamente del vehículo detectado.
Se guarda como archivo para verificación, auditoría y evidencia.

Ejemplo de ruta:

data/images/auto_2025-04-15_13-22-15.jpg

Nivel de Confianza

Representa qué tan seguro está el modelo de que el objeto detectado es un vehículo.
Permite filtrar detecciones dudosas.

Más de 0.90: muy confiable

0.70 a 0.90: confiable

Menos de 0.50: débil o no recomendado

Historial de Detecciones

Cada detección almacena:

Hora

Color

Nivel de confianza

Ruta de la captura

Opcionalmente se pueden añadir tipo de vehículo, cámara de origen o información adicional.

Dashboard Web en Flask

Incluye:

Streaming en vivo

Se visualiza el video procesado con las detecciones dibujadas.

Tabla de historial

Actualizada en tiempo real con la información de cada auto detectado.

Interfaz moderna y limpia

Basada en HTML y CSS.

Estilo minimalista y oscuro.

Estructura modular

Facilita añadir filtros, buscadores, gráficos y nuevas funciones.

Estructura del Proyecto
car-color-detector/
│
├── app.py
├── detector.py
├── haarcascade_car.xml
│
├── static/              → estilos
├── templates/           → interfaz web
│
├── data/                → capturas y base de datos
│   ├── images/
│   └── detections.db
│
├── config/              → parámetros de cámara
│   └── camera_config.yaml
│
└── README.md

Flujo de Funcionamiento

Se abre la transmisión de la cámara IP.

Cada frame del video es procesado.

Se detectan vehículos.

Se recorta el auto y se obtiene su captura.

Se identifica el color.

Se calcula el nivel de confianza.

Se registra la detección en el historial.

El dashboard web muestra el video procesado y la tabla de detecciones.

Recomendaciones

Utilizar RTSP para reducir el retraso.

Mantener la cámara estable y con buen ángulo.

Usar cámaras ColorVu para detección de color nocturna.

Para máxima precisión, preferir YOLOv8/YOLOv11.

Posibles Extensiones

Gráficos estadísticos (con Chart.js).

Soporte para múltiples cámaras.

Exportación del historial a CSV o Excel.

Detección de marca y modelo del vehículo.

Reconocimiento de patentes via OCR.

Panel analítico avanzado estilo Grafana.


