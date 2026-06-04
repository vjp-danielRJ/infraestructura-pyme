# Instalación y Configuración del Servidor Web

## 1. Requisitos previos

- Ubuntu Server 22.04 instalado y actualizado
- Acceso root o usuario con sudo
- Conexión a internet

## 2. Instalación de Apache

```bash
apt update
apt install apache2 -y
```

Verificar que Apache está activo:
```bash
systemctl status apache2
```

Habilitar Apache para que arranque automáticamente:
```bash
systemctl enable apache2
```

## 3. Instalación de PHP

```bash
apt install php libapache2-mod-php php-mysql -y
```

Verificar la versión instalada:
```bash
php -v
```

## 4. Configuración del VirtualHost

Crear el directorio para la web de la PYME:
```bash
mkdir -p /var/www/pyme
chown -R www-data:www-data /var/www/pyme
```

Crear el archivo de configuración del VirtualHost:
```bash
nano /etc/apache2/sites-available/pyme.conf
```

Contenido del archivo:
```apache
<VirtualHost *:80>
    ServerName pyme.local
    ServerAdmin admin@pyme.local
    DocumentRoot /var/www/pyme

    <Directory /var/www/pyme>
        AllowOverride All
        Require all granted
    </Directory>

    ErrorLog ${APACHE_LOG_DIR}/pyme_error.log
    CustomLog ${APACHE_LOG_DIR}/pyme_access.log combined
</VirtualHost>
```

Activar el sitio y el módulo rewrite:
```bash
a2ensite pyme.conf
a2enmod rewrite
systemctl restart apache2
```

## 5. Verificación

Crear una página de prueba:
```bash
echo "<?php phpinfo(); ?>" > /var/www/pyme/index.php
```

Acceder desde el navegador a `http://IP-SERVIDOR` y comprobar que aparece la página de información de PHP.

## 6. Versiones instaladas

| Componente | Versión |
|---|---|
| Apache | 2.4.60 |
| PHP | 8.1 |
| libapache2-mod-php | 8.1 |

## 7. Configuración del Balanceador de Carga HAProxy

### 7.1 Instalación de HAProxy

```bash
apt update
apt install haproxy -y
```

Verificar que HAProxy está activo:
```bash
systemctl status haproxy
```

Habilitar HAProxy para arranque automático:
```bash
systemctl enable haproxy
```

### 7.2 Configuración básica

Editar el archivo de configuración:
```bash
nano /etc/haproxy/haproxy.cfg
```

Añadir la siguiente configuración al final del archivo:
frontend http_front
bind *:80
default_backend http_backbackend http_back
balance roundrobin
server servidor1 192.168.1.10:80 check
server servidor2 192.168.1.11:80 check

Reiniciar HAProxy para aplicar cambios:
```bash
systemctl restart haproxy
```

### 7.3 Verificación

Comprobar que HAProxy está distribuyendo el tráfico correctamente:
```bash
haproxy -c -f /etc/haproxy/haproxy.cfg
```

Acceder al panel de estadísticas de HAProxy:
`http://IP-SERVIDOR:8404/stats`