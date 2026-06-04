# Planificación del Proyecto

## Fases del proyecto

| Fase | Descripción | Responsable | Estado |
|---|---|---|---|
| 1 | Análisis de requisitos | Daniel Rubio | ✅ Completado |
| 2 | Diseño de infraestructura | Daniel Mateos | ✅ Completado |
| 3 | Instalación servidor web y BD | Daniel Mateos | ✅ Completado |
| 4 | Configuración SSH y firewall | Daniel Mateos | ✅ Completado |
| 5 | Monitorización y backups | Daniel Rubio | ✅ Completado |
| 6 | Guía de operación | Daniel Rubio | ✅ Completado |
| 7 | Plan de recuperación | Daniel Rubio | ✅ Completado |
| 8 | Balanceador HAProxy | Ambos | ✅ Completado |

## Cambio de alcance: HAProxy

El cliente solicitó la incorporación de un balanceador de carga HAProxy para distribuir el tráfico entre dos servidores Apache, mejorando la disponibilidad y el rendimiento del sistema.

### Impacto en la infraestructura
- Se añade HAProxy como punto de entrada del tráfico web
- Se requiere un segundo servidor Apache (192.168.1.11)
- La configuración de firewall se actualiza para permitir tráfico al balanceador
- Se añaden tareas de mantenimiento específicas para HAProxy