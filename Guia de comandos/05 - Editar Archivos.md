---
tags:
  - linux
  - basico
  - editores
created: 2026-09-16
---

# Editar Archivos

> [!abstract] Editar archivos desde terminal
> Herramientas disponibles para crear, ver y modificar archivos directamente desde la línea de comandos.

---

## Ver Contenido

| Comando | Descripción | Ejemplo |
|---------|-------------|---------|
| `cat <archivo>` | Muestra el contenido completo | `cat config.txt` |
| `head -n 10 <archivo>` | Muestra las primeras 10 líneas | `head -n 5 log.txt` |
| `tail -n 10 <archivo>` | Muestra las últimas 10 líneas | `tail -n 20 log.txt` |
| `tail -f <archivo>` | Muestra contenido en tiempo real | `tail -f /var/log/syslog` |
| `less <archivo>` | Visor paginado (navegar con ↑↓) | `less archivo.grande` |
| `more <archivo>` | Visor paginado básico | `more documento.txt` |

---

## Editores de Terminal

### Nano (Recomendado para principiantes)

```bash
nano archivo.txt
```

| Atajo | Acción |
|-------|--------|
| `Ctrl + O` | Guardar archivo |
| `Enter` | Confirmar nombre de archivo |
| `Ctrl + X` | Salir del editor |
| `Ctrl + K` | Cortar línea |
| `Ctrl + U` | Pegar línea |
| `Ctrl + W` | Buscar texto |
| `Ctrl + G` | Ayuda |

> [!info] Nano es el editor más fácil de usar. Ideal para ediciones rápidas.

### Vim / Vi

```bash
vim archivo.txt
```

| Modo | Acción |
|------|--------|
| `i` | Entrar en modo inserción |
| `Esc` | Salir del modo inserción |
| `:w` | Guardar |
| `:q` | Salir |
| `:wq` | Guardar y salir |
| `:q!` | Salir sin guardar |
| `dd` | Eliminar línea |
| `yy` | Copiar línea |
| `p` | Pegar |

> [!warning] Vim tiene una curva de aprendizaje pronunciada. Si eres nuevo, usa Nano.

### VS Code desde Terminal

```bash
code archivo.txt          # Abre un archivo
code .                    # Abre la carpeta actual
code archivo1.txt archivo2.txt  # Abre múltiples archivos
```

---

## Comparación de Editores

| Característica | Nano | Vim | VS Code |
|----------------|------|-----|---------|
| Facilidad de uso | ⭐⭐⭐ | ⭐ | ⭐⭐⭐ |
| Funcionalidades | Básicas | Avanzadas | Extensas |
| Curva de aprendizaje | Mínima | Pronunciada | Baja |
| Ideal para | Ediciones rápidas | Desarrolladores | Proyectos completos |

---

## Ver También

- [[06 - Permisos]] - Control de acceso a archivos
- [[12 - Atajos de Terminal]] - Atajos de teclado

---

**Última actualización:** 2026-09-16
