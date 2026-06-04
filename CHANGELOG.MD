# Changelog

Todos los cambios relevantes del proyecto se documentan en este archivo.

## [1.0.0] - 2026-06-04
### Añadido
- Balanceador de carga HAProxy (`servidor-web.md`)
- Tareas de mantenimiento de HAProxy (`05-operacion.md`)
- Diagrama de red actualizado con HAProxy (`02-diseno.md`)
- Planificación actualizada con nueva fase (`03-planificacion.md`)
- Issue #1 gestionado: "Añadir balanceador HAProxy a la infraestructura"
- README.md completo con estructura y tecnologías
- Archivo REVISION.md con reflexión del equipo
### Cambiado
- Versión del proyecto a v1.0.0

## [0.3.0] - 2026-06-04
### Añadido
- Guía de operación y mantenimiento diario (`05-operacion.md`)
- Plan de recuperación ante desastres (`06-recuperacion.md`)
- Actualización del CHANGELOG

## [0.2.0] - 2026-05-28
### Añadido
- Documentación de monitorización con Netdata
- Política de backups con mysqldump y rsync
### Cambiado
- Tabla de versiones actualizada (Apache 2.4.60, Certbot añadido)
### Fix
- Conflicto resuelto en `02-diseno.md` durante revisión cruzada

## [0.1.0] - 2026-05-21
### Añadido
- Estructura inicial del repositorio
- README.md con descripción del proyecto
- Análisis de requisitos del cliente (`01-analisis.md`)
- Diseño de la infraestructura (`02-diseno.md`)
- Primera versión de monitorización y backups