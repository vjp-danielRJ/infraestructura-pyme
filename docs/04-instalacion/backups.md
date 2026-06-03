# Política de Copias de Seguridad

## Estrategia

Combinación de mysqldump para bases de datos y rsync para archivos.

## Scripts de backup

### Backup de base de datos
```bash
#!/bin/bash
DATE=$(date +%Y%m%d)
mysqldump -u root -p --all-databases > /backups/db_$DATE.sql
gzip /backups/db_$DATE.sql
```

### Backup de archivos web
```bash
#!/bin/bash
rsync -avz /var/www/html/ /backups/web/
```

## Programación con cron

```bash
# Backup diario a las 2:00 AM
0 2 * * * /scripts/backup-db.sh
# Backup semanal archivos web domingo 3:00 AM
0 3 * * 0 /scripts/backup-web.sh
```

## Rotación de backups

| Tipo | Retención |
|------|-----------|
| Diario | 7 días |
| Semanal | 4 semanas |
| Mensual | 6 meses |

## Ubicación

- Local: `/backups/`
- Remoto: servidor secundario via rsync