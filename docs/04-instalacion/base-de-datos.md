# Instalación y Configuración de la Base de Datos

## 1. Instalación de MySQL

```bash
apt update
apt install mysql-server -y
```

Verificar que MySQL está activo:
```bash
systemctl status mysql
```

Habilitar MySQL para arranque automático:
```bash
systemctl enable mysql
```

## 2. Configuración inicial de seguridad

Ejecutar el asistente de seguridad:
```bash
mysql_secure_installation
```

Opciones recomendadas:
- Establecer contraseña root: **Sí**
- Eliminar usuarios anónimos: **Sí**
- Deshabilitar acceso root remoto: **Sí**
- Eliminar base de datos de prueba: **Sí**
- Recargar privilegios: **Sí**

## 3. Creación de bases de datos

Acceder a MySQL:
```bash
mysql -u root -p
```

Crear la base de datos para la web:
```sql
CREATE DATABASE pyme_web CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;
```

Crear la base de datos para gestión interna:
```sql
CREATE DATABASE pyme_gestion CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;
```

## 4. Creación de usuarios

Crear usuario para la web:
```sql
CREATE USER 'web_user'@'localhost' IDENTIFIED BY 'contraseña_segura';
GRANT ALL PRIVILEGES ON pyme_web.* TO 'web_user'@'localhost';
```

Crear usuario para gestión interna:
```sql
CREATE USER 'gestion_user'@'localhost' IDENTIFIED BY 'contraseña_segura';
GRANT ALL PRIVILEGES ON pyme_gestion.* TO 'gestion_user'@'localhost';
```

Aplicar cambios:
```sql
FLUSH PRIVILEGES;
EXIT;
```

## 5. Verificación

Comprobar que las bases de datos se han creado correctamente:
```bash
mysql -u root -p -e "SHOW DATABASES;"
```

## 6. Versiones instaladas

| Componente | Versión |
|---|---|
| MySQL | 8.0 |