# 🛠️ Administración de Servidores Linux y Servicios de Red

Este trabajo práctico documenta la implementación completa de un servidor GNU/Linux Debian dentro de un entorno virtualizado, siguiendo lineamientos específicos para la configuración del sistema operativo, servicios de red, almacenamiento, automatización y documentación. El proyecto permitió aplicar conocimientos fundamentales de administración de sistemas Linux, servicios esenciales, scripting y manejo de infraestructura a nivel servidor.

El trabajo se desarrolló en equipo y tuvo como objetivo aplicar de forma práctica los contenidos de la cursada, evidenciando dominio técnico, correcta ejecución de procedimientos y capacidad de defender las decisiones implementadas durante la actividad.

## Puntos Clave del Proyecto

* **Configuración del Entorno:** Importación de la máquina virtual Debian, blanqueo y cambio de contraseña de root, y definición del hostname del sistema.

* **Servicios Instalados:** Configuración de SSH con autenticación por clave pública/privada para root; despliegue de Apache con soporte PHP; instalación de MariaDB y carga de la base de datos provista.

* **Configuración de Red:** Asignación de una IP estática, definiendo parámetros de ADDRESS, NETMASK y GATEWAY para integrarse con la red física.

* **Almacenamiento:** Adición de un disco extra de 10 GB, particionado en dos unidades montadas automáticamente para alojar el sitio web y los backups. Adaptación de Apache para utilizar la nueva ubicación del contenido web.

* **Automatización y Backups:** Desarrollo del script backup_full.sh con validaciones, ayuda integrada y soporte para argumentos. Integración del script en cron para generar respaldos diarios y programados.

* **Entregables y Documentación:** Compresión y subida de los directorios del sistema al repositorio de GitHub, junto con un README detallado y un diagrama topológico de la solución implementada.
