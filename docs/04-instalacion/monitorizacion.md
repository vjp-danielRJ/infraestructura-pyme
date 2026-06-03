# Monitorización del Sistema

## Herramienta elegida: Netdata

Netdata es una herramienta de monitorización en tiempo real ligera y de fácil instalación.

## Instalación

```bash
bash <(curl -Ss https://my-netdata.io/kickstart.sh)
```

## Métricas monitorizadas

| Métrica | Umbral de alerta |
|---------|-----------------|
| CPU | >80% durante 5 min |
| RAM | >90% |
| Disco | >85% |
| Red | >100 Mbps |

## Acceso al panel

- URL: `http://192.168.1.10:19999`
- Solo accesible desde red interna

## Alertas

Las alertas se configuran en `/etc/netdata/health.d/`
y se envían por email al administrador.