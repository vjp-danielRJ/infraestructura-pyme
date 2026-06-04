# Revisión del Proyecto

## Autores
- Daniel Rubio
- Daniel Mateos

## 1. ¿Qué conflictos tuvisteis y cómo los resolvisteis?

Durante el proyecto nos encontramos con dos conflictos de merge:

- **Conflicto 1 (Sesión 2):** Ambos editamos la misma tabla de versiones en `02-diseno.md`. Lo resolvimos manualmente eligiendo la versión más actualizada de Apache (2.4.60) e integrando la fila de Certbot que había añadido uno de los dos.

- **Conflicto 2 (Sesión 3):** Ambos modificamos `ssh-firewall.md` con contenido incompatible. Esta vez lo resolvimos usando `git rebase` en lugar de merge, combinando las reglas UFW de ambos en una versión final coherente.

## 2. ¿Qué comandos Git usasteis más?

| Comando | Uso |
|---|---|
| `git checkout -b` | Crear nuevas ramas de trabajo |
| `git add` / `git commit` | Guardar cambios con mensajes descriptivos |
| `git push` / `git pull` | Sincronizar con el repositorio remoto |
| `git pull --rebase` | Resolución del segundo conflicto |
| `git push --force-with-lease` | Subir rama tras rebase |

## 3. ¿Qué haríais diferente en un próximo proyecto?

- Comunicarnos mejor antes de editar los mismos archivos para evitar conflictos innecesarios.
- Hacer `git pull` de main más frecuentemente para mantener las ramas actualizadas.
- Escribir mensajes de commit más detallados desde el principio.
- Dividir mejor las tareas desde el inicio para no pisar el trabajo del otro.

## 4. ¿Cómo os funcionó el intercambio de roles?

El intercambio de roles fue útil porque nos obligó a revisar y entender el trabajo del compañero en profundidad. Al tener que modificar archivos que no habíamos creado nosotros, aprendimos a leer documentación técnica ajena y a mantener la coherencia del proyecto. También generó situaciones reales de colaboración como los conflictos de merge.