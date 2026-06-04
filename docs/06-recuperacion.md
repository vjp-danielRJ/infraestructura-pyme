# Plan de Recuperación ante Desastres

## 1. Objetivos

- **RTO (Recovery Time Objective):** Máximo 4 horas de inactividad.
- **RPO (Recovery Point Objective):** Pérdida máxima de datos de 24 horas.

## 2. Escenarios de fallo y procedimientos

### 2.1 Caída del servidor Apache

1. Comprobar el estado del servicio:
```bash
   systemctl status apache2
```
2. Intentar reiniciar:
```bash
   systemctl restart apache2
```
3. Si no arranca, revisar logs:
```bash
   journalctl -xe | grep apache2
```
4. Si persiste, restaurar configuración desde backup:
```bash
   cp /var/backups/pyme/apache2.conf /etc/apache2/apache2.conf
   systemctl restart apache2
```

### 2.2 Corrupción o pérdida de base de datos

1. Parar el servicio MySQL:
```bash
   systemctl stop mysql
```
2. Restaurar el último backup disponible:
```bash
   mysql -u root -p nombre_bd < /var/backups/pyme/backup_ultimo.sql
```
3. Arrancar MySQL y verificar:
```bash
   systemctl start mysql
   mysql -u root -p -e "SHOW DATABASES;"
```

### 2.3 Acceso SSH bloqueado

1. Acceder a la máquina por consola física o panel del proveedor.
2. Comprobar el estado del firewall:
```bash
   ufw status
```
3. Si el puerto 22 está bloqueado:
```bash
   ufw allow 22/tcp
   ufw reload
```

### 2.4 Servidor completamente caído

1. Reiniciar la máquina desde el panel del proveedor.
2. Verificar que todos los servicios arrancan automáticamente:
```bash
   systemctl status apache2 mysql ssh
```
3. Si algún servicio no arranca, seguir los procedimientos anteriores.

## 3. Localización de backups

| Tipo | Ruta | Frecuencia |
|---|---|---|
| Base de datos | `/var/backups/pyme/bd/` | Diaria (02:00) |
| Archivos web | `/var/backups/pyme/web/` | Semanal (domingos) |
| Configuración Apache | `/var/backups/pyme/apache2.conf` | Tras cada cambio |

## 4. Prueba del plan

Se recomienda realizar una prueba de recuperación cada 3 meses simulando cada escenario en un entorno de pruebas.