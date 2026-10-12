# Proyecto de Búsqueda Visual para Retail (Multimodal AI)

## Descripción del proyecto
Este proyecto implementa un prototipo de motor de búsqueda visual para comercio electrónico. Utilizando inteligencia artificial multimodal, el sistema permite clasificar productos (como relojes, llantas y audífonos) a partir de una fotografía sin necesidad de entrenamiento previo (Zero-Shot Classification). Se analizan y comparan tres modelos preentrenados de Hugging Face (CLIP, ViT y ResNet) para evaluar el trade-off entre eficiencia (latencia) y precisión.

## Entorno de ejecución
- **Plataforma:** Google Colab
- **Hardware:** GPU Tesla T4 (Acelerador por hardware)
- **Lenguaje:** Python 3
- **Librerías principales:** `transformers`, `torch`, `pandas`, `scikit-learn`, `Pillow` (ver `requirements.txt`)

## Pasos de ejecución
1. Clonar este repositorio o descargar los archivos.
2. Subir el cuaderno que se encuentra en la carpeta `notebooks` a Google Colab.
3. Asegurarse de habilitar el entorno de ejecución de GPU T4 en Colab (Entorno de ejecución > Cambiar tipo de entorno).
4. Configurar el token de Hugging Face en los "Secrets" de Colab bajo el nombre `HF_TOKEN`.
5. Ejecutar las celdas secuencialmente. El script se encargará de generar el dataset automáticamente y ejecutar las inferencias.

## Conclusiones
Se seleccionó CLIP como modelo inicial debido a su facilidad de implementación y a que permite clasificar imágenes sin realizar un entrenamiento previo. Esta característica lo convierte en una alternativa conveniente para pequeñas y medianas empresas que buscan validar una solución de búsqueda visual sin asumir, desde el comienzo, los costos y la complejidad de un proceso de fine-tuning (ajuste del modelo con datos propios). Aunque su tiempo de ejecución podría aumentar conforme crezca la demanda, CLIP representa un punto de partida adecuado para poner en funcionamiento el prototipo y apoyar la recopilación de imágenes reales, categorías, predicciones y correcciones realizadas por los usuarios o responsables del catálogo. Posteriormente, estos datos revisados y etiquetados podrían utilizarse para adaptar un modelo más eficiente, como ResNet-50, que mostró un menor tiempo de respuesta. De esta manera, la solución podría evolucionar de forma gradual: primero se aprovecharía la flexibilidad de CLIP para validar el caso de uso y construir un conjunto de datos propio y, después, se utilizaría esa información para realizar el fine-tuning de ResNet-50, evaluar nuevamente sus métricas y determinar si ofrece una mejor relación entre velocidad y precisión para atender un mayor volumen de solicitudes.