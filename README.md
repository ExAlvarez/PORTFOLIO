# 🦠 **Análisis de Malware e Ingeniería Reversa**



Este trabajo documenta un proceso completo de análisis estático y dinámico de un archivo ejecutable sospechoso, utilizando técnicas de ingeniería reversa para identificar modificaciones en el binario, comportamientos maliciosos, mecanismos de ejecución y comunicación con infraestructura externa.


El análisis se realizó sobre una versión modificada de PuTTY, combinando el estudio de la estructura interna del ejecutable con herramientas de monitoreo y análisis de comportamiento como Procmon, Wireshark y TCPView. El objetivo fue determinar la naturaleza del malware, comprender su funcionamiento y obtener evidencia que permitiera identificar el mecanismo utilizado para ejecutar el payload y establecer comunicación con su infraestructura de control.



## **Puntos Clave del Proyecto**

* **Análisis del Ejecutable**: Identificación de la arquitectura I386, fecha de compilación y hash SHA-256 del archivo analizado, junto con el estudio de sus características internas.
* **Análisis de Secciones PE**: Inspección de las diferentes secciones del ejecutable y detección de un segundo conjunto de secciones .text, .idata, .rsrc y .reloc, evidencia de que el PuTTY original fue modificado mediante la incorporación de un módulo adicional.
* **Identificación de Strings Sospechosos**: Detección de comandos y funcionalidades asociadas a PowerShell, incluyendo ejecución sin perfil, ventana oculta y bypass de políticas de ejecución, además de un payload comprimido y codificado en Base64.
* **Análisis de Imports**: Identificación de librerías y funciones relevantes como SHELL32.dll, KERNEL32.dll y ADVAPI32.dll, destacando el uso de CreateThread para la ejecución del payload y mecanismos para lanzar procesos externos.
* **Detonación y Análisis Dinámico**: Ejecución controlada del malware para observar su comportamiento. Aunque el programa aparenta funcionar normalmente y muestra la configuración de PuTTY, durante la ejecución se observa la apertura momentánea de una consola de PowerShell.
* **Análisis con Procmon**: Monitoreo de aproximadamente 21.000 eventos relacionados con putty.exe, permitiendo identificar la creación del Thread 2576 mediante CreateThread y correlacionarlo con la ejecución del payload malicioso.
* **Análisis de Tráfico de Red**: Utilización de Wireshark para detectar una conexión TLS hacia www.wireshark.org, comportamiento que no corresponde a las funcionalidades nativas esperadas de PuTTY y que constituye evidencia adicional de la modificación del ejecutable.
* **Detección de Comportamiento de Connectivity Check**: El malware mantiene la conexión de PowerShell abierta hasta establecer comunicación con el entorno externo, abortando el proceso cuando no dispone de conectividad, comportamiento compatible con una verificación de conectividad antes de continuar con su ejecución.
* **Clasificación del Malware**: El archivo fue identificado como un troyano, debido a que se presenta como software legítimo para inducir al usuario a ejecutarlo. También presenta características de Dropper, ya que utiliza una conexión externa para obtener o ejecutar el payload malicioso.
* **Conclusiones**: El análisis permitió determinar que el ejecutable legítimo de PuTTY fue modificado para incorporar un módulo malicioso que ejecuta un payload mediante PowerShell, utiliza técnicas de evasión y establece comunicación con una infraestructura C2. El uso de PowerShell permite evitar la necesidad de incluir directamente un ejecutable malicioso dentro del archivo y dificulta la detección basada exclusivamente en firmas o hashes.

