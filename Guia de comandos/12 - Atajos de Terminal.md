---
tags:
  - linux
  - basico
  - productividad
created: 2026-09-16
---

# Atajos de Terminal

> [!abstract] Atajos de teclado esenciales
> Combinaciones de teclas que agilizan el trabajo diario en la terminal.

---

## Navegación del Cursor

| Atajo | Acción |
|-------|--------|
| `Ctrl + A` | Mueve cursor al inicio de la línea |
| `Ctrl + E` | Mueve cursor al final de la línea |
| `Ctrl + B` | Retrocede un carácter |
| `Ctrl + F` | Avanza un carácter |
| `Alt + B` | Retrocede una palabra |
| `Alt + F` | Avanza una palabra |

---

## Edición

| Atajo | Acción |
|-------|--------|
| `Ctrl + U` | Elimina desde el cursor hasta el inicio |
| `Ctrl + K` | Elimina desde el cursor hasta el final |
| `Ctrl + W` | Elimina la palabra anterior |
| `Alt + D` | Elimina la palabra siguiente |
| `Ctrl + Y` | Pega lo último eliminado |
| `Ctrl + _` | Deshacer |
| `Ctrl + T` | Intercambia caracteres |
| `Alt + T` | Intercambia palabras |

---

## Control de Terminal

| Atajo | Acción |
|-------|--------|
| `Ctrl + C` | Cancela el comando actual (SIGINT) |
| `Ctrl + D` | Cierra la terminal (EOF) |
| `Ctrl + Z` | Pausa el comando (envía a background) |
| `Ctrl + L` | Limpia la pantalla |
| `Ctrl + S` | Pausa la salida de la terminal |
| `Ctrl + Q` | Reanuda la salida pausada |

---

## Historial y Búsqueda

| Atajo | Acción |
|-------|--------|
| `↑` / `↓` | Navegar historial de comandos |
| `Ctrl + R` | Búsqueda inversa en historial |
| `Ctrl + G` | Cancela la búsqueda |
| `!!` | Repite el último comando |
| `!n` | Ejecuta comando n del historial |
| `!$` | Usa el último argumento del comando anterior |
| `!*` | Usa todos los argumentos del comando anterior |

---

## Autocompletado

| Atajo | Acción |
|-------|--------|
| `Tab` | Autocompleta comando o ruta |
| `Tab Tab` | Muestra todas las opciones disponibles |
| `Alt + ?` | Muestra ayuda de autocompletado |
| `Alt + *` | Inserta todas las opciones |

---

## Tareas

| Atajo | Acción |
|-------|--------|
| `Ctrl + J` | Nueva línea (como Enter) |
| `Ctrl + M` | Nueva línea (como Enter) |
| `Ctrl + O` | Ejecuta y muestra resultado |
| `Ctrl + X Ctrl + E` | Abre editor para el comando actual |

---

## Combinaciones Útiles

```bash
# Repetir último comando con sudo
sudo !!

# Usar último argumento
mkdir carpeta
cd !$          # Equivale a: cd carpeta

# Ejecutar y guardar salida
comando | tee archivo.txt        # Muestra en pantalla y guarda
comando > archivo.txt 2>&1       # Guarda todo (salida y errores)

# Buscar en historial y ejecutar
!!:gs/antiguo/nuevo   # Reemplaza texto en el último comando
```

---

## Tips Avanzados

> [!tip] Secuencias de escape útiles
> - `\n` - Nueva línea
> - `\t` - Tabulación
> - `\\` - Barra invertida literal
> - `\033[0m` - Reset de color ANSI

```bash
# Colores en terminal
echo -e "\e[31mTexto rojo\e[0m"
echo -e "\e[32mTexto verde\e[0m"
echo -e "\e[34mTexto azul\e[0m"
```

---

## Ver También

- [[01 - Iniciar WSL]] - Configuración inicial
- [[05 - Editar Archivos]] - Editores de terminal

---

**Última actualización:** 2026-09-16
