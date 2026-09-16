---
tags:
  - linux
  - desarrollo
  - git
  - control-versiones
created: 2026-09-16
---

# Git

> [!abstract] Control de versiones con Git
> Git es el sistema de control de versiones distribuido más utilizado. Permite rastrear cambios en código y colaborar con otros desarrolladores.

---

## Configuración Inicial

```bash
git config --global user.name "Tu Nombre"
git config --global user.email "tu@email.com"
git config --global core.editor "code --wait"  # Usar VS Code
git config --global init.defaultBranch main    # Rama por defecto
git config --list                              # Ver configuración
```

---

## Crear y Clonar Repositorios

| Comando | Descripción |
|---------|-------------|
| `git init` | Inicializa un repositorio local |
| `git clone <url>` | Clona un repositorio remoto |
| `git clone <url> <carpeta>` | Clona en una carpeta específica |
| `git clone --depth 1 <url>` | Clona solo el último commit |

---

## Flujo Básico de Trabajo

```bash
git status                  # Ver estado actual
git add .                   # Agregar todos los cambios
git add <archivo>           # Agregar archivo específico
git commit -m "mensaje"     # Crear commit
git push                    # Subir al remoto
git pull                    # Descargar del remoto
```

### Convención de Mensajes de Commit

| Tipo | Uso | Ejemplo |
|------|-----|---------|
| `feat:` | Nueva funcionalidad | `feat: agregar login` |
| `fix:` | Corrección de bug | `fix: error en formulario` |
| `docs:` | Documentación | `docs: actualizar README` |
| `style:` | Formato (sin cambio lógico) | `style: sangría correcta` |
| `refactor:` | Reestructurar código | `refactor: dividir componente` |
| `test:` | Agregar tests | `test: unit tests para auth` |
| `chore:` | Tareas de mantenimiento | `chore: actualizar dependencias` |

---

## Ramas (Branches)

| Comando | Descripción |
|---------|-------------|
| `git branch` | Lista ramas locales |
| `git branch -a` | Lista todas las ramas (incluyendo remotas) |
| `git branch <nombre>` | Crea una nueva rama |
| `git checkout <nombre>` | Cambia a otra rama |
| `git checkout -b <nombre>` | Crea y cambia a una nueva rama |
| `git switch <nombre>` | Cambia de rama (alternativa moderna) |
| `git switch -c <nombre>` | Crea y cambia (alternativa moderna) |
| `git branch -d <nombre>` | Elimina rama local |
| `git branch -D <nombre>` | Elimina rama forzadamente |
| `git push origin <rama>` | Sube rama al remoto |
| `git push origin --delete <rama>` | Elimina rama remota |

---

## Historial y Estado

| Comando | Descripción |
|---------|-------------|
| `git status` | Estado del repositorio |
| `git log` | Historial completo de commits |
| `git log --oneline` | Historial compacto |
| `git log --graph` | Muestra ramas gráficamente |
| `git log -n 5` | Últimos 5 commits |
| `git log --author="nombre"` | Commits de un autor |
| `git diff` | Cambios sin staging |
| `git diff --staged` | Cambios en staging |
| `git diff rama1..rama2` | Diferencia entre ramas |

---

## Deshacer Cambios

| Comando | Descripción | ⚠️ Peligro |
|---------|-------------|------------|
| `git checkout -- <archivo>` | Descarta cambios | Seguro |
| `git restore <archivo>` | Descarta cambios (moderno) | Seguro |
| `git reset HEAD <archivo>` | Quita del staging | Seguro |
| `git restore --staged <archivo>` | Quita del staging (moderno) | Seguro |
| `git reset --soft HEAD~1` | Deshace commit, conserva cambios | Seguro |
| `git reset --mixed HEAD~1` | Deshace commit y staging | Moderado |
| `git reset --hard HEAD~1` | Deshace todo | ⚠️ Peligroso |
| `git stash` | Guarda cambios temporalmente | Seguro |
| `git stash pop` | Recupera cambios guardados | Seguro |

> [!warning] `git reset --hard` elimina cambios permanentemente. Usa con precaución.

---

## Repositorio Remoto

| Comando | Descripción |
|---------|-------------|
| `git remote add origin <url>` | Conecta con remoto |
| `git remote -v` | Lista remotos configurados |
| `git push -u origin <rama>` | Sube y establece tracking |
| `git fetch` | Descarga cambios sin fusionar |
| `git pull origin <rama>` | Descarga y fusiona |
| `git pull --rebase` | Reaplica commits sobre nuevos cambios |

---

## Tags (Etiquetas)

```bash
git tag v1.0.0                        # Crea tag ligero
git tag -a v1.0.0 -m "Mensaje"       # Crea tag anotado
git push origin v1.0.0                # Sube tag específico
git push origin --tags                # Sube todos los tags
git tag -d v1.0.0                     # Elimina tag local
git push origin --delete v1.0.0       # Elimina tag remoto
```

---

## Comandos Útiles

```bash
git blame <archivo>           # Muestra quién modificó cada línea
git shortlog -sn              # Resume commits por autor
git reflog                    # Historial de acciones (recuperación)
git cherry-pick <commit>      # Aplica un commit específico
git rebase <rama>             # Reaplica commits sobre otra rama
git merge <rama>              # Fusiona una rama en la actual
```

---

## Ver También

- [[09 - Búsqueda]] - Buscar en archivos
- [[11 - Docker]] - Contenedores

---

**Última actualización:** 2026-09-16
