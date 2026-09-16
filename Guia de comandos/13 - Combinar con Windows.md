---
tags:
  - linux
  - wsl
  - windows
  - integracion
created: 2026-09-16
---

# Combinar con Windows

> [!abstract] Integración WSL con Windows
> Cómo aprovechar la integración entre Windows y Linux en WSL para trabajar de forma más eficiente.

---

## Abrir Aplicaciones de Windows desde Linux

| Comando | Descripción |
|---------|-------------|
| `explorer.exe .` | Abre Explorador en el directorio actual |
| `code .` | Abre VS Code en el directorio actual |
| `notepad.exe archivo.txt` | Abre archivo con Notepad |
| `start <archivo>` | Abre archivo con la app predeterminada |
| `powershell.exe` | Abre PowerShell |
| `cmd.exe` | Abre Command Prompt |

---

## Acceder a Archivos de Windows

```bash
# Acceder al disco C:
ls /mnt/c/

# Acceder al Escritorio
ls /mnt/c/Users/Admin/Desktop

# Acceder a Documentos
ls /mnt/c/Users/Admin/Documents

# Crear archivo en Windows
touch /mnt/c/Users/Admin/Desktop/nota.txt

# Copiar archivo desde Windows
cp /mnt/c/Users/Admin/Downloads/archivo.zip ./
```

---

## Acceder a Archivos de Linux desde Windows

```
\\wsl$\<distribucion>\<ruta>
```

### Ejemplos

```
\\wsl$\Debian\home\usuario
\\wsl$\Ubuntu\home\usuario\proyectos
```

### Pasos

1. Abre Explorador de Windows
2. Escribe `\\wsl$\Debian` en la barra de direcciones
3. Navega como cualquier carpeta de Windows

---

## Configurar VS Code con WSL

```bash
# Instalar extensión de WSL en VS Code
code --install-extension ms-vscode-remote.remote-wsl

# Abrir VS Code con WSL
code .

# Abrir archivo específico
code archivo.txt
```

> [!tip] Con la extensión WSL de VS Code, puedes usar todas las extensiones de Linux directamente en el editor de Windows.

---

## Compartir Variables de Entorno

```bash
# Variables de Windows disponibles en Linux
echo $BROWSER        # Navegador predeterminado de Windows
echo $DISPLAY        # Servidor X (para GUI)

# Variables de Linux en Windows
# Se pueden acceder desde PowerShell:
wsl echo $HOME
```

---

## Ejecutar Comandos de Linux desde PowerShell

```powershell
# Ejecutar un comando de Linux
wsl ls -la /home

# Ejecutar script de bash
wsl bash script.sh

# Ejecutar comando con pipes
wsl cat /etc/os-release | findstr "NAME"
```

---

## Ejecutar Comandos de Windows desde Linux

```bash
# Ejecutar PowerShell
powershell.exe -Command "Get-Process"

# Ejecutar cmd
cmd.exe /c "dir C:\Users"

# Ejecutar comandos con salida
powershell.exe -Command "(Get-Date).ToString()"
```

---

## Red entre Windows y Linux

```bash
# IP de Windows desde Linux
cat /etc/resolv.conf | grep nameserver | awk '{print $2}'

# IP de Linux desde Windows
wsl hostname -I

# Servicios accesibles entre ambos
# - Linux puede acceder a servicios de Windows en localhost
# - Windows puede acceder a servicios de Linux en localhost
```

---

## Instalar Herramientas de Windows en WSL

```bash
# Instalar utilidades de Windows
sudo apt install dos2unix      # Convertir saltos de línea
sudo apt install unzip         # Descomprimir archivos

# Convertir archivos Windows a Linux
dos2unix script.sh

# Convertir archivos Linux a Windows
unix2dos script.sh
```

---

## Gestión de WSL desde Windows

```powershell
# Listar distribuciones instaladas
wsl --list --verbose

# Actualizar WSL
wsl --update

# Detener todas las instancias
wsl --shutdown

# Exportar distribución
wsl --export Debian backup.tar

# Importar distribución
wsl --import MiLinux C:\WSL\Linux backup.tar

# Desregistrar distribución
wsl --unregister Debian
```

---

## Atajos Útiles

| Acción | Comando |
|--------|---------|
| Copiar de Linux a Windows | `cat archivo \| clip.exe` |
| Pegar de Windows a Linux | `echo $(Get-Clipboard) > archivo` |
| Abrir terminal en directorio actual | `explorer.exe .` |
| Ejecutar programa de Windows | `programa.exe &` |

> [!note] Algunas aplicaciones de Windows pueden no funcionar correctamente desde WSL (especialmente las que requieren GUI).

---

## Ver También

- [[01 - Iniciar WSL]] - Configuración de WSL
- [[12 - Atajos de Terminal]] - Atajos de teclado

---

**Última actualización:** 2026-09-16
