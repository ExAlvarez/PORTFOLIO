# 🦠 Análisis de Malware e Ingeniería Reversa

Este trabajo documenta el análisis estático y dinámico de un ejecutable sospechoso basado en una versión modificada de PuTTY. El objetivo fue identificar modificaciones en el binario, analizar su comportamiento, detectar mecanismos de ejecución y determinar el tipo de malware mediante distintas herramientas de análisis.

## Puntos Clave del Proyecto
* **Análisis del Ejecutable:** Identificación de arquitectura, hash, fecha de compilación, secciones, strings e imports relevantes del archivo.
* **Análisis de Comportamiento:** Ejecución controlada del malware y análisis de la actividad generada mediante Procmon, identificando la creación de procesos y threads asociados al payload.
* **Análisis de Red:** Captura y análisis del tráfico mediante Wireshark y TCPView para identificar conexiones sospechosas e infraestructura de comunicación.
* **Identificación del Payload:** Detección de un payload ejecutado mediante PowerShell, utilizando Base64/Gzip y técnicas destinadas a ocultar su ejecución.
* **Identificación del C2:** Detección del dominio bonus2.corporatebonusapplication.local como infraestructura de comunicación utilizada por el malware.
* **Clasificación:** Identificación del archivo como un troyano con características de Dropper, debido a su apariencia de software legítimo y utilización de PowerShell para ejecutar el payload.
