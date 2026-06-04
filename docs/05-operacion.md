# Guía de Operación y Mantenimiento

## 1. Tareas diarias

- Comprobar el estado del servidor Apache:
```bash
  systemctl status apache2
```
- Verificar que MySQL está activo:
```bash
  systemctl status mysql
```
- Revisar logs de errores de Apache:
```bash
  tail -n 50 /var/log/apache2/error.log
```

## 2. Tareas semanales

- Revisar el espacio en disco:
```bash
  df -h
```
- Comprobar actualizaciones de seguridad:
```bash
  apt update && apt list --upgradable
```
- Verificar los backups automáticos en `/var/backups/pyme/`

## 3. Tareas mensuales

- Aplicar actualizaciones del sistema:
```bash
  apt upgrade -y
```
- Revisar usuarios con acceso SSH:
```bash
  cat /etc/passwd | grep -v nologin
```
- Rotar manualmente los logs si es necesario:
```bash
  logrotate -f /etc/logrotate.conf
```

## 4. Monitorización

- Acceder al panel de Netdata: `http://IP-SERVIDOR:19999`
- Comprobar alertas activas en el panel
- Revisar uso de CPU, RAM y red

## 5. Contacto de soporte

| Responsable | Rol | Contacto |
|---|---|---|
| Daniel Rubio | Administrador de sistemas | admin@pyme.local |
| Daniel Mateos | Administrador de plataforma | plataforma@pyme.local |

## 6. Mantenimiento del Balanceador HAProxy

### Tareas diarias
- Comprobar el estado de HAProxy:
```bash
  systemctl status haproxy
```
- Revisar logs de HAProxy:
```bash
  tail -n 50 /var/log/haproxy.log
```
- Verificar que los servidores backend están activos en el panel de estadísticas:
  `http://IP-SERVIDOR:8404/stats`

### Tareas semanales
- Revisar el balance de carga entre servidores
- Comprobar que no hay servidores marcados como caídos
- Revisar el archivo de configuración por si hay cambios pendientes:
```bash
  haproxy -c -f /etc/haproxy/haproxy.cfg
```

### Procedimiento ante caída de HAProxy
1. Intentar reiniciar el servicio:
```bash
   systemctl restart haproxy
```
2. Si no arranca, revisar logs:
```bash
   journalctl -xe | grep haproxy
```
3. Restaurar configuración desde backup:
```bash
   cp /var/backups/pyme/haproxy.cfg /etc/haproxy/haproxy.cfg
   systemctl restart haproxy
```