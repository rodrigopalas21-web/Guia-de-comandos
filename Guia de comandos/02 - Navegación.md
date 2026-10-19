---
tags:
  - linux
  - basico
  - navegacion
created: 2026-09-16
---

# Navegación

> [!abstract] Moverse por el sistema de archivos
> Conocer dónde estás y cómo llegar a otros directorios es fundamental para trabajar en Linux.

---

## Comandos Principales

| Comando | Descripción | Ejemplo |
|---------|-------------|---------|
| `pwd` | Muestra el directorio actual | `pwd` → `/home/usuario` |
| `ls` | Lista archivos y carpetas | `ls -la` |
| `cd` | Vuelve al directorio raíz | `cd` |
| `cd <carpeta>` | Entra a una carpeta específica | `cd Documentos` |
| `cd ..` | Sube un nivel de directorio | `cd ..` |
| `cd ~` | Vuelve al home del usuario | `cd ~` |
| `cd -` | Vuelve al directorio anterior | `cd -` |

---

## Opciones de `ls`

```bash
ls          # Lista básica
ls -l       # Formato largo (permisos, tamaño, fecha)
ls -la      # Incluye archivos ocultos
ls -lh      # Tamaños legibles (KB, MB, GB)
ls -lt      # Ordenado por fecha (más reciente primero)
ls -lS      # Ordenado por tamaño
ls -R       # Lista recursiva (incluye subcarpetas)
```

---

## Estructura del Sistema de Archivos

| Directorio | Descripción |
|------------|-------------|
| `/` | Raíz del sistema |
| `/home` | Directorio personal de los usuarios |
| `/etc` | Archivos de configuración del sistema |
| `/var` | Datos variables (logs, caché) |
| `/tmp` | Archivos temporales |
| `/usr` | Programas y bibliotecas del sistema |
| `/bin` | Ejecutables esenciales del sistema |
| `/sbin` | Ejecutables del sistema (admin) |

---

## Navegación Avanzada

```bash
cd ~/Documentos/proyectos    # Ruta absoluta desde home
cd ../../                    # Subir dos niveles
cd ../otra_carpeta           # Subir y entrar a otra carpeta
```

> [!tip] Usa `Tab` para autocompletar nombres de archivos y carpetas.

---

## Ver También

- [[01 - Iniciar WSL]] - Configuración inicial
- [[09 - Búsqueda]] - Encontrar archivos

---

**Última actualización:** 2026-09-16
