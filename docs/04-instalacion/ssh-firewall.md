# Configuración de Acceso Remoto SSH y Firewall

## 1. Configuración de SSH

Verificar que SSH está instalado y activo:
```bash
systemctl status ssh
```

Si no está instalado:
```bash
apt install openssh-server -y
systemctl enable ssh
```

Editar la configuración de SSH para mayor seguridad:
```bash
nano /etc/ssh/sshd_config
```

Parámetros recomendados:
Port 22
PermitRootLogin no
PasswordAuthentication yes
MaxAuthTries 3

Reiniciar SSH para aplicar cambios:
```bash
systemctl restart ssh
```

## 2. Reglas UFW

Activar UFW:
```bash
ufw enable
```
L
Permitir SSH solo desde la red de la oficina:
```bash
ufw allow from 192.168.1.0/24 to any port 22
```

Permitir tráfico web:
```bash
ufw allow 80/tcp
ufw allow 443/tcp
```

## 3. Verificación del firewall

Comprobar las reglas activas:
```bash
ufw status verbose
```

Resultado esperado:
Status: active
To                         Action      From

22                         ALLOW       192.168.1.0/24
80/tcp                     ALLOW       Anywhere
443/tcp                    ALLOW       Anywhere