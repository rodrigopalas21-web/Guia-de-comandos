---
tags:
  - linux
  - intermedio
  - procesos
created: 2026-09-16
---

# Procesos

> [!abstract] Gestionar procesos en ejecución
> Cómo ver, controlar y administrar los procesos que se ejecutan en el sistema.

---

## Ver Procesos

| Comando | Descripción |
|---------|-------------|
| `ps` | Lista procesos de la sesión actual |
| `ps aux` | Lista todos los procesos del sistema |
| `ps -ef` | Lista completa con PPID |
| `ps -u <usuario>` | Procesos de un usuario específico |
| `top` | Monitor de procesos en tiempo real |
| `htop` | Monitor mejorado (si está instalado) |
| `pgrep <nombre>` | Busca PID por nombre del proceso |

---

## Información de Procesos

```bash
ps aux
```

| Columna | Significado |
|---------|-------------|
| `USER` | Usuario propietario |
| `PID` | Identificador del proceso |
| `%CPU` | Uso de CPU |
| `%MEM` | Uso de memoria |
| `COMMAND` | Nombre del comando |

---

## Matar Procesos

| Comando | Descripción |
|---------|-------------|
| `kill <PID>` | Termina un proceso (señal SIGTERM) |
| `kill -9 <PID>` | Fuerza la terminación (SIGKILL) |
| `kill -15 <PID>` | Termina limpiamente (SIGTERM) |
| `killall <nombre>` | Termina todos los procesos con ese nombre |
| `pkill <nombre>` | Termina procesos por nombre |

> [!tip] Intenta primero `kill <PID>` antes de usar `kill -9`. La señal normal permite al proceso cerrar limpiamente.

---

## Prioridad de Procesos

```bash
nice -n 10 comando         # Ejecuta con baja prioridad
nice -n -10 comando        # Ejecuta con alta prioridad (requiere root)
renice -n 10 -p <PID>      # Cambia prioridad de un proceso en ejecución
```

---

## Background y Foreground

| Comando | Descripción |
|---------|-------------|
| `<comando> &` | Ejecuta en segundo plano |
| `Ctrl + Z` | Pausa el proceso actual |
| `bg` | Reanuda el proceso pausado en background |
| `fg` | Trae un proceso de background a foreground |
| `jobs` | Lista procesos en background |
| `fg %<número>` | Trae un proceso específico a foreground |

---

## Systemd (Servicios)

```bash
systemctl status <servicio>     # Estado del servicio
systemctl start <servicio>      # Inicia el servicio
systemctl stop <servicio>       # Detiene el servicio
systemctl restart <servicio>    # Reinicia el servicio
systemctl enable <servicio>     # Habilita al iniciar sistema
systemctl disable <servicio>    # Deshabilita al iniciar sistema
systemctl list-units --type=service  # Lista todos los servicios
```

---

## Uso de Recursos

```bash
free -h              # Uso de memoria RAM
df -h                # Uso de disco
du -sh /carpeta     # Tamaño de una carpeta
uptime               # Tiempo encendido y carga
vmstat 1             # Estadísticas de memoria y CPU
```

---

## Ver También

- [[06 - Permisos]] - Control de acceso
- [[08 - Red]] - Comandos de red

---

**Última actualización:** 2026-09-16
