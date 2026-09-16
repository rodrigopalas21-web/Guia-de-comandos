---
tags:
  - linux
  - desarrollo
  - docker
  - contenedores
created: 2026-09-16
---

# Docker

> [!abstract] Contenedores e imágenes
> Docker permite empaquetar aplicaciones con todas sus dependencias en contenedores portables y aislados.

---

## Verificación e Instalación

```bash
docker --version          # Verifica versión instalada
docker info               # Información del sistema Docker
docker run hello-world    # Verifica que funciona correctamente
```

---

## Imágenes

| Comando | Descripción |
|---------|-------------|
| `docker images` | Lista imágenes descargadas |
| `docker pull <imagen>` | Descarga una imagen |
| `docker rmi <imagen>` | Elimina una imagen |
| `docker image prune` | Elimina imágenes sin usar |
| `docker image prune -a` | Elimina todas las imágenes no usadas |
| `docker tag <origen> <nuevo>` | Etiqueta una imagen |
| `docker push <imagen>` | Sube imagen al registro |

---

## Contenedores

### Crear y Ejecutar

| Comando | Descripción |
|---------|-------------|
| `docker run <imagen>` | Ejecuta un contenedor |
| `docker run -d <imagen>` | Ejecuta en segundo plano (detached) |
| `docker run -it <imagen> bash` | Ejecuta con terminal interactivo |
| `docker run -d -p 8080:80 <imagen>` | Mapea puertos |
| `docker run -d --name miweb <imagen>` | Asigna nombre al contenedor |
| `docker run -d -v /host:/container <imagen>` | Monta volumen |
| `docker run -d -e VAR=valor <imagen>` | Define variable de entorno |

> [!tip] `-p host:contenedor` mapea puertos. `-p 8080:80` significa que el puerto 8080 de Windows se redirige al 80 del contenedor.

### Gestionar Contenedores

| Comando | Descripción |
|---------|-------------|
| `docker ps` | Lista contenedores ejecutándose |
| `docker ps -a` | Lista todos los contenedores |
| `docker stop <contenedor>` | Detiene un contenedor |
| `docker start <contenedor>` | Inicia un contenedor detenido |
| `docker restart <contenedor>` | Reinicia un contenedor |
| `docker rm <contenedor>` | Elimina un contenedor |
| `docker rm -f <contenedor>` | Elimina forzadamente |
| `docker exec -it <contenedor> bash` | Entra al contenedor |
| `docker logs <contenedor>` | Muestra logs |
| `docker logs -f <contenedor>` | Sigue mostrando logs |
| `docker inspect <contenedor>` | Información detallada |

---

## Ejemplos Prácticos

```bash
# Servidor web Nginx
docker run -d --name web -p 8080:80 nginx

# Base de datos PostgreSQL
docker run -d --name db \
  -e POSTGRES_PASSWORD=secret \
  -v pgdata:/var/lib/postgresql/data \
  -p 5432:5432 \
  postgres

# Base de datos MySQL
docker run -d --name mysql \
  -e MYSQL_ROOT_PASSWORD=root123 \
  -e MYSQL_DATABASE=mibd \
  -v mysqldata:/var/lib/mysql \
  -p 3306:3306 \
  mysql

# Redis
docker run -d --name redis -p 6379:6379 redis

# PHP con Apache
docker run -d --name php -p 8080:80 -v $(pwd):/var/www/html php:apache
```

---

## Docker Compose

### Comandos

```bash
docker compose up -d              # Levanta servicios en background
docker compose down               # Detiene y elimina servicios
docker compose ps                 # Lista servicios
docker compose logs -f            # Muestra logs en tiempo real
docker compose logs -f <servicio> # Logs de un servicio específico
docker compose exec <srv> bash    # Entra a un servicio
docker compose build              # Reconstruye imágenes
docker compose pull               # Descarga imágenes actualizadas
docker compose restart            # Reinicia servicios
docker compose stop               # Detiene sin eliminar
docker compose start              # Inicia servicios detenidos
```

### Ejemplo de `docker-compose.yml`

```yaml
version: '3.8'

services:
  web:
    image: nginx:alpine
    ports:
      - "8080:80"
    volumes:
      - ./html:/usr/share/nginx/html
    depends_on:
      - api
    networks:
      - app-network

  api:
    build: ./api
    ports:
      - "3000:3000"
    environment:
      - DB_HOST=db
      - DB_PASSWORD=secret
    depends_on:
      - db
    networks:
      - app-network

  db:
    image: postgres:15
    environment:
      POSTGRES_PASSWORD: secret
      POSTGRES_DB: miapp
    volumes:
      - pgdata:/var/lib/postgresql/data
    networks:
      - app-network

volumes:
  pgdata:

networks:
  app-network:
    driver: bridge
```

---

## Volumenes

```bash
docker volume create <nombre>        # Crea volumen nombrado
docker volume ls                     # Lista volúmenes
docker volume inspect <nombre>       # Detalles del volumen
docker volume rm <nombre>            # Elimina volumen
docker volume prune                  # Elimina volúmenes sin usar
```

---

## Redes

```bash
docker network create <nombre>       # Crea red
docker network ls                    # Lista redes
docker network inspect <nombre>      # Detalles de red
docker network connect <red> <ctr>  # Conecta contenedor a red
docker network disconnect <red> <ctr> # Desconecta contenedor
```

---

## Limpieza

| Comando | Descripción |
|---------|-------------|
| `docker system prune` | Elimina contenedores, redes e imágenes sin usar |
| `docker system prune -a` | Limpieza profunda |
| `docker system prune --volumes` | Incluye volúmenes |
| `docker container prune` | Elimina contenedores detenidos |
| `docker image prune` | Elimina imágenes sin usar |
| `docker volume prune` | Elimina volúmenes sin usar |
| `docker network prune` | Elimina redes sin usar |

---

## Ver También

- [[10 - Git]] - Control de versiones
- [[08 - Red]] - Comandos de red

---

**Última actualización:** 2026-09-16
