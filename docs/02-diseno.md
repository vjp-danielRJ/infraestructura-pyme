# Diseño de Infraestructura

## Diagrama de red
Internet → Firewall (UFW) → Servidor Apache (80/443) → MySQL (3306)
## Tabla de componentes

| Componente | Versión | Función |
|------------|---------|---------|
| Ubuntu Server | 22.04 LTS | Sistema operativo base |
| Apache | 2.4.59 | Servidor web |
| Certbot para SSL | 2.1 | Servidor web |
| PHP | 8.1 | Procesamiento servidor |
| MySQL | 8.0 | Base de datos |
| UFW | - | Firewall |

## Direccionamiento IP

| Dispositivo | IP |
|-------------|-----|
| Servidor web | 192.168.1.10 |
| Base de datos | 192.168.1.11 |
| Gateway | 192.168.1.1 |