# Infraestructura PYME — Documentación LAMP

Repositorio de documentación técnica colaborativa para el despliegue de una infraestructura LAMP con monitorización y balanceo de carga, desarrollado como proyecto del módulo de Sistemas Informáticos.

## 👥 Autores

- Daniel Rubio — Documentalista de plataforma / operaciones
- Daniel Mateos — Documentalista de operaciones / plataforma

## 📋 Descripción del proyecto

Documentación completa del despliegue de una infraestructura LAMP (Linux, Apache, MySQL, PHP) para una PYME, incluyendo configuración de seguridad, monitorización, backups y balanceo de carga con HAProxy.

## 📁 Estructura del repositorio
infraestructura-pyme/
├── README.md
├── CHANGELOG.md
├── REVISION.md
├── docs/
│   ├── 01-analisis.md
│   ├── 02-diseno.md
│   ├── 03-planificacion.md
│   ├── 04-instalacion/
│   │   ├── servidor-web.md
│   │   ├── base-de-datos.md
│   │   ├── ssh-firewall.md
│   │   ├── monitorizacion.md
│   │   └── backups.md
│   ├── 05-operacion.md
│   └── 06-recuperacion.md

## 🛠️ Tecnologías documentadas

| Componente | Versión |
|---|---|
| Ubuntu Server | 22.04 LTS |
| Apache | 2.4.60 |
| PHP | 8.1 |
| MySQL | 8.0 |
| HAProxy | 2.6 |
| Netdata | Latest |
| Certbot | 2.9 |

## 📄 Documentación

| Documento | Descripción |
|---|---|
| [Análisis](docs/01-analisis.md) | Requisitos del cliente |
| [Diseño](docs/02-diseno.md) | Diagrama de red y componentes |
| [Planificación](docs/03-planificacion.md) | Fases del proyecto |
| [Servidor Web](docs/04-instalacion/servidor-web.md) | Instalación Apache y HAProxy |
| [Base de datos](docs/04-instalacion/base-de-datos.md) | Instalación MySQL |
| [SSH y Firewall](docs/04-instalacion/ssh-firewall.md) | Acceso remoto y UFW |
| [Monitorización](docs/04-instalacion/monitorizacion.md) | Netdata |
| [Backups](docs/04-instalacion/backups.md) | Copias de seguridad automáticas |
| [Operación](docs/05-operacion.md) | Guía de mantenimiento |
| [Recuperación](docs/06-recuperacion.md) | Plan de desastres |