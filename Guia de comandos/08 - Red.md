---
tags:
  - linux
  - intermedio
  - red
created: 2026-09-16
---

# Red

> [!abstract] Comandos de red y conectividad
> Herramientas para diagnosticar, configurar y monitorear la red en Linux.

---

## Conectividad

| Comando | Descripción | Ejemplo |
|---------|-------------|---------|
| `ping <host>` | Verifica conectividad | `ping google.com` |
| `ping -c 4 <host>` | Envía 4 paquetes y detiene | `ping -c 4 8.8.8.8` |
| `traceroute <host>` | Muestra ruta a un destino | `traceroute google.com` |
| `mtr <host>` | traceroute + ping continuo | `mtr google.com` |

---

## Configuración de Red

| Comando | Descripción |
|---------|-------------|
| `ip a` | Muestra interfaces y IPs |
| `ip r` | Muestra tabla de enrutamiento |
| `ip link show` | Lista interfaces de red |
| `ifconfig` | Alternativa clásica (puede no estar) |
| `nmcli` | Gestión con NetworkManager |

---

## DNS

| Comando | Descripción | Ejemplo |
|---------|-------------|---------|
| `nslookup <dominio>` | Consulta DNS | `nslookup google.com` |
| `dig <dominio>` | Consulta DNS detallada | `dig google.com` |
| `host <dominio>` | Resolución DNS simple | `host google.com` |

### Configurar DNS

```bash
# Editar archivo de resolución DNS
sudo nano /etc/resolv.conf

# Agregar servidor DNS
nameserver 8.8.8.8
nameserver 8.8.4.4
```

---

## Descargar Contenido

| Comando | Descripción | Ejemplo |
|---------|-------------|---------|
| `curl <url>` | Descarga contenido | `curl https://ejemplo.com` |
| `curl -O <url>` | Descarga archivo | `curl -O https://ejemplo.com/archivo.zip` |
| `wget <url>` | Descarga archivo | `wget https://ejemplo.com/archivo.zip` |
| `wget -c <url>` | Continúa descarga interrumpida | `wget -c url` |

---

## Puertos y Conexiones

| Comando | Descripción |
|---------|-------------|
| `netstat -tuln` | Muestra puertos abiertos |
| `ss -tuln` | Alternativa moderna a netstat |
| `lsof -i :<puerto>` | Qué proceso usa un puerto |
| `nmap <host>` | Escaneo de puertos |

```bash
# Ver qué procesos escuchan en puertos
sudo ss -tuln

# Verificar si un puerto está abierto
nc -zv google.com 443
```

---

## SSH (Secure Shell)

```bash
ssh usuario@host                    # Conexión básica
ssh -p 2222 usuario@host            # Puerto específico
ssh -i ~/.ssh/llave.pem user@host   # Con llave específica
scp archivo.txt user@host:/ruta/    # Copia archivo vía SSH
scp user@host:/archivo.txt ./       # Descarga archivo vía SSH
```

### Configurar SSH

```bash
# Generar llave SSH
ssh-keygen -t rsa -b 4096

# Copiar llave al servidor
ssh-copy-id user@host
```

---

## Firewall (UFW)

```bash
sudo ufw status             # Estado del firewall
sudo ufw enable             # Activar firewall
sudo ufw disable            # Desactivar firewall
sudo ufw allow 80           # Abrir puerto 80
sudo ufw allow 443          # Abrir puerto 443
sudo ufw deny 22            # Bloquear puerto 22
sudo ufw delete allow 80    # Eliminar regla
```

---

## Ver También

- [[07 - Procesos]] - Gestionar procesos
- [[11 - Docker]] - Red de contenedores

---

**Última actualización:** 2026-09-16
