---
tags:
  - linux
  - intermedio
  - permisos
created: 2026-09-16
---

# Permisos

> [!abstract] Control de acceso a archivos
> Linux utiliza un sistema de permisos para controlar quién puede leer, escribir y ejecutar archivos.

---

## Estructura de Permisos

Cuando ejecutas `ls -l`, la salida muestra los permisos:

```
-rwxr-xr-- 1 usuario grupo 4096 sep 16 10:00 archivo.sh
│└┬┘└┬┘└┬┘
│  │  │  │
│  │  │  └─ Permisos de otros (other)
│  │  └──── Permisos de grupo (group)
│  └─────── Permisos de usuario (owner)
└────────── Tipo de archivo (- = archivo, d = directorio, l = enlace)
```

---

## Tabla de Permisos

| Permiso | Símbolo | Número | Significado |
|---------|---------|--------|-------------|
| Lectura | `r` | 4 | Leer contenido |
| Escritura | `w` | 2 | Modificar contenido |
| Ejecución | `x` | 1 | Ejecutar como programa |

---

## Cambiar Permisos con `chmod`

### Método Numérico (Octal)

```bash
chmod 755 archivo.sh    # rwxr-xr-x
chmod 644 archivo.txt   # rw-r--r--
chmod 600 archivo.sec   # rw-------
chmod 777 archivo.pub   # rwxrwxrwx
```

### Método Simbólico

```bash
chmod +x archivo.sh     # Agregar ejecución
chmod -w archivo.txt    # Quitar escritura
chmod u+r archivo.txt   # Agregar lectura al usuario
chmod g+w archivo.txt   # Agregar escritura al grupo
chmod o-x archivo.sh   # Quitar ejecución a otros
```

---

## Permisos Comunes

| Permiso | Número | Uso típico |
|---------|--------|------------|
| `rwxr-xr-x` | 755 | Scripts, ejecutables |
| `rw-r--r--` | 644 | Archivos de texto, configuración |
| `rw-------` | 600 | Archivos sensibles, contraseñas |
| `rwx------` | 700 | Directorio personal, scripts privados |
| `rwxrwxrwx` | 777 | ⚠️ Nunca usar (inseguro) |

---

## Dueño y Grupo

```bash
chown usuario archivo.txt           # Cambia el dueño
chown usuario:grupo archivo.txt    # Cambia dueño y grupo
chown -R usuario:grupo carpeta/    # Cambia recursivamente
chgrp grupo archivo.txt            # Cambia solo el grupo
```

---

## Permisos Especiales

| Permiso | Número | Descripción |
|---------|--------|-------------|
| `s` (setuid) | 4000 | Ejecuta con permisos del dueño |
| `s` (setgid) | 2000 | Ejecuta con permisos del grupo |
| `t` (sticky) | 1000 | Solo el dueño puede eliminar |

```bash
chmod u+s programa    # Setuid
chmod g+s carpeta/    # Setgid
chmod +t /tmp         # Sticky bit
```

---

## Ejemplos Prácticos

```bash
# Hacer ejecutable un script
chmod +x script.sh

# Proteger archivo de configuración
chmod 600 ~/.ssh/id_rsa

# Permitir lectura y escritura al grupo
chmod 660 archivo_compartido.txt

# Dar permisos completos al dueño, nada a otros
chmod 700 directorio_secreto/
```

> [!warning] `chmod 777` da acceso total a todos los usuarios. Evítalo por razones de seguridad.

---

## Ver También

- [[03 - Crear y Eliminar]] - Gestionar archivos
- [[05 - Editar Archivos]] - Editar archivos

---

**Última actualización:** 2026-09-16
