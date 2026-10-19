---
tags:
  - linux
  - wsl
  - basico
created: 2026-09-16
---

# Iniciar WSL

> [!info] Windows Subsystem for Linux (WSL)
> Permite ejecutar un entorno Linux completo directamente desde Windows sin necesidad de máquina virtual ni dual boot.

---

## Comando Básico

```bash
wsl -d Debian --cd /home
```

| Parámetro | Descripción |
|-----------|-------------|
| `-d Debian` | Especifica la distribución a iniciar |
| `--cd /home` | Establece el directorio de inicio |

---

## Distribuciones Disponibles

```bash
wsl --list --verbose    # Lista distribuciones instaladas
wsl --list --online     # Lista distribuciones disponibles para instalar
```

> [!tip] Puedes usar `-d Ubuntu`, `-d Fedora` o cualquier otra distribución que tengas instalada.

---

## Comandos Útiles de WSL

| Comando | Descripción |
|---------|-------------|
| `wsl` | Inicia la distribución por defecto |
| `wsl -d <distribución>` | Inicia una distribución específica |
| `wsl --shutdown` | Detiene todas las instancias de WSL |
| `wsl --update` | Actualiza WSL a la última versión |
| `wsl --status` | Muestra el estado actual de WSL |

---

## Volver al Directorio Actual desde Windows

```bash
wsl --cd "C:\Users\Admin\Desktop"
```

> [!note] Esto inicia WSL directamente en el directorio de Windows especificado.

---

## Ver También

- [[02 - Navegación]] - Moverse por el sistema de archivos
- [[13 - Combinar con Windows]] - Integración con Windows

---

**Última actualización:** 2026-09-16
