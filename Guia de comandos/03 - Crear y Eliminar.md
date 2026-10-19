---
tags:
  - linux
  - basico
  - archivos
created: 2026-09-16
---

# Crear y Eliminar

> [!abstract] Gestionar archivos y carpetas
> Cómo crear, eliminar y administrar archivos y directorios en Linux.

---

## Crear

| Comando | Descripción | Ejemplo |
|---------|-------------|---------|
| `mkdir <carpeta>` | Crea una carpeta | `mkdir proyectos` |
| `mkdir -p <ruta>` | Crea carpetas anidadas | `mkdir -p a/b/c` |
| `touch <archivo>` | Crea un archivo vacío | `touch nota.txt` |
| `touch <archivo1> <archivo2>` | Crea múltiples archivos | `touch a.txt b.txt c.txt` |

---

## Eliminar

| Comando | Descripción | Ejemplo |
|---------|-------------|---------|
| `rm <archivo>` | Elimina un archivo | `rm nota.txt` |
| `rm -i <archivo>` | Pide confirmación antes de eliminar | `rm -i nota.txt` |
| `rm -r <carpeta>` | Elimina una carpeta y su contenido | `rm -r proyectos` |
| `rm -ri <carpeta>` | Elimina con confirmación recursiva | `rm -ri proyectos` |
| `rm -f <archivo>` | Fuerza la eliminación sin confirmar | `rm -f archivo.tmp` |
| `rmdir <carpeta>` | Elimina una carpeta vacía | `rmdir carpeta_vacia` |

> [!warning] `rm -r` es irreversible. Siempre verifica antes de ejecutar este comando.

---

## Ejemplos Prácticos

```bash
# Crear estructura de proyecto
mkdir -p ~/proyectos/web/{src,public,docs}

# Crear múltiples archivos
touch ~/proyectos/web/src/{index.html,style.css,script.js}

# Eliminar archivos temporales
rm -f /tmp/*.tmp

# Eliminar carpeta con todo su contenido
rm -rf ~/proyectos/antiguos
```

---

## Consejos de Seguridad

> [!danger] Prácticas peligrosas
> - `rm -rf /` - Elimina todo el sistema (NUNCA ejecutar)
> - `rm -rf ~` - Elimina tu directorio personal completo
> - `rm -rf *` - Elimina todo en el directorio actual

> [!tip] Usa `rm -ri` en lugar de `rm -r` para tener confirmación antes de cada eliminación.

---

## Ver También

- [[04 - Copiar y Mover]] - Duplicar y trasladar contenido
- [[06 - Permisos]] - Control de acceso a archivos

---

**Última actualización:** 2026-09-16
