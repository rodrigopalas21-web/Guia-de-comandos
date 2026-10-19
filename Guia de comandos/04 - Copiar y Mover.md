---
tags:
  - linux
  - basico
  - archivos
created: 2026-09-16
---

# Copiar y Mover

> [!abstract] Duplicar y trasladar contenido
> Cómo copiar, mover y renombrar archivos y carpetas en Linux.

---

## Copiar

| Comando | Descripción | Ejemplo |
|---------|-------------|---------|
| `cp <origen> <destino>` | Copia un archivo | `cp archivo.txt copia.txt` |
| `cp -r <origen> <destino>` | Copia una carpeta completa | `cp -r carpeta1/ carpeta2/` |
| `cp -i <origen> <destino>` | Pide confirmación si existe destino | `cp -i archivo.txt destino/` |
| `cp -v <origen> <destino>` | Muestra progreso de copia | `cp -v *.txt backup/` |
| `cp -u <origen> <destino>` | Copia solo si el origen es más reciente | `cp -u src/* dst/` |

---

## Mover / Renombrar

| Comando | Descripción | Ejemplo |
|---------|-------------|---------|
| `mv <origen> <destino>` | Mueve un archivo | `mv archivo.txt /home/` |
| `mv <viejo> <nuevo>` | Renombra un archivo | `mv.txt nuevo.txt` |
| `mv -i <origen> <destino>` | Pide confirmación antes de sobrescribir | `mv -i archivo.txt destino/` |
| `mv -v <origen> <destino>` | Muestra progreso de movimiento | `mv -v *.log /var/log/` |

---

## Ejemplos Prácticos

```bash
# Copiar archivo manteniendo permisos
cp -p archivo.txt backup/

# Copiar todos los archivos .txt a una carpeta
cp *.txt ~/Documentos/

# Renombrar archivo
mv proyecto_v1.txt proyecto_final.txt

# Mover múltiples archivos a una carpeta
mv archivo1.txt archivo2.txt ~/Documentos/

# Mover todos los .log a una carpeta de logs
mv /var/log/*.log ~/logs_backup/
```

---

## Diferencia entre `cp` y `mv`

| Aspecto | `cp` | `mv` |
|---------|------|------|
| Origen | Se mantiene | Se elimina |
| Espacio | Duplica contenido | Traslada contenido |
| Rendimiento | Más lento (copia datos) | Más rápido (solo cambia ruta) |

> [!tip] `mv` es más rápido porque solo cambia la ubicación del archivo, no copia los datos.

---

## Ver También

- [[03 - Crear y Eliminar]] - Gestionar archivos y carpetas
- [[06 - Permisos]] - Control de acceso a archivos

---

**Última actualización:** 2026-09-16
