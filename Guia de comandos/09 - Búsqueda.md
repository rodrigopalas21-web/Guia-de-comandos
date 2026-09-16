---
tags:
  - linux
  - intermedio
  - busqueda
created: 2026-09-16
---

# Búsqueda

> [!abstract] Encontrar archivos y contenido
> Herramientas para localizar archivos por nombre, contenido o propiedades en el sistema.

---

## Buscar Archivos

| Comando | Descripción | Ejemplo |
|---------|-------------|---------|
| `find <ruta> -name "<nombre>"` | Busca por nombre exacto | `find /home -name "config.txt"` |
| `find <ruta> -name "*<patrón>"` | Busca por patrón | `find . -name "*.log"` |
| `find <ruta> -type f` | Solo archivos | `find /var -type f` |
| `find <ruta> -type d` | Solo directorios | `find /home -type d` |
| `find <ruta> -mtime -7` | Modificados en últimos 7 días | `find . -mtime -7` |
| `find <ruta> -size +100M` | Archivos mayores a 100MB | `find / -size +100M` |
| `find <ruta> -empty` | Archivos vacíos | `find . -empty` |

---

## Buscar Contenido en Archivos

| Comando | Descripción | Ejemplo |
|---------|-------------|---------|
| `grep "<texto>" <archivo>` | Busca texto en un archivo | `grep "error" log.txt` |
| `grep -r "<texto>" <dir>` | Busca recursivamente | `grep -r "TODO" src/` |
| `grep -i "<texto>" <archivo>` | Ignora mayúsculas/minúsculas | `grep -i "error" log.txt` |
| `grep -n "<texto>" <archivo>` | Muestra número de línea | `grep -n "error" log.txt` |
| `grep -c "<texto>" <archivo>` | Cuenta ocurrencias | `grep -c "error" log.txt` |
| `grep -v "<texto>" <archivo>` | Invierte la búsqueda | `grep -v "debug" log.txt` |

---

## Buscar Comandos

| Comando | Descripción | Ejemplo |
|---------|-------------|---------|
| `which <comando>` | Ruta de un comando | `which python` |
| `whereis <comando>` | Ubicación de binario, fuente y man | `whereis git` |
| `type <comando>` | Tipo de comando | `type ls` |

---

## Buscar en Historial

```bash
history                     # Muestra todo el historial
history | grep "docker"     # Busca en historial
!n                          # Ejecuta comando n del historial
!!                          # Repite último comando
```

---

## Expresiones Regulares (Básico)

| Patrón | Significado | Ejemplo |
|--------|-------------|---------|
| `.` | Cualquier carácter | `grep "a.b" archivo` |
| `*` | Cero o más repeticiones | `grep "ab*" archivo` |
| `^` | Inicio de línea | `grep "^Error" log.txt` |
| `$` | Fin de línea | `grep "fin$" log.txt` |
| `[]` | Rango de caracteres | `grep "[0-9]" archivo` |
| `\b` | Límite de palabra | `grep "\berror\b" archivo` |

---

## Combinaciones Útiles

```bash
# Encontrar y ejecutar comando en cada archivo
find . -name "*.txt" -exec grep -l "buscar" {} \;

# Encontrar archivos grandes y ordenar
find / -size +100M -exec ls -lh {} \; 2>/dev/null | sort -k5 -h

# Buscar y eliminar archivos temporales
find . -name "*.tmp" -delete

# Buscar archivos modificados hoy
find . -type f -newermt "2026-09-16"
```

---

## Ver También

- [[02 - Navegación]] - Moverse por el sistema
- [[10 - Git]] - Buscar en repositorios

---

**Última actualización:** 2026-09-16
