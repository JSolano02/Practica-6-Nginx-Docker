# Práctica 6 — Servidor web Nginx con Docker Compose

## Objetivo

Ejecutar un servidor web **Nginx** en un contenedor Docker usando **Docker Compose**, mostrar un mensaje **¡Hola Mundo!** desde un archivo HTML local y publicar el código en un repositorio público de GitHub.

## Estructura

```text
Practica-6-Nginx-Docker/
├── src/
│   └── index.html
├── docker-compose.yml
├── .gitignore
├── GUIA_PASO_A_PASO.md
└── README.md
```

## Requisitos

- Docker Desktop instalado y **en ejecución**.
- VS Code.
- Git instalado (para subirlo desde la terminal).
- Cuenta de GitHub.

## Ejecutar el proyecto

Desde la carpeta principal, donde está `docker-compose.yml`, abre una terminal y escribe:

```powershell
docker compose up -d
```

El primer inicio puede descargar automáticamente la imagen oficial `nginx:stable-alpine`.

Comprueba el contenedor:

```powershell
docker compose ps
```

Abre **http://localhost:8080**. Debe aparecer el mensaje **¡Hola Mundo!**.

Para consultar los mensajes de Nginx:

```powershell
docker compose logs nginx
```

Para detener el contenedor:

```powershell
docker compose down
```

## Cómo funciona

En `docker-compose.yml`:

- `image: nginx:stable-alpine` usa una imagen oficial de Nginx.
- `ports: "8080:80"` expone en el puerto **8080** del PC el puerto **80** del contenedor.
- `./src:/usr/share/nginx/html:ro` monta el directorio local `src` en el directorio que Nginx sirve, en **solo lectura**.

**Importante:** abrir `localhost:8080` funciona después de iniciar Docker. Publicar el proyecto en GitHub **no** significa que la web quede alojada públicamente: GitHub almacenará el código y la configuración.

## Evidencias sugeridas para la entrega

1. En VS Code, estructura de carpetas y archivo `docker-compose.yml`.
2. En la terminal, salida de `docker compose ps` con el contenedor activo.
3. En el navegador, página **¡Hola Mundo!** en `http://localhost:8080`.
4. En GitHub, repositorio **Public** con los archivos cargados.

## Publicación

Consulta **[GUIA_PASO_A_PASO.md](GUIA_PASO_A_PASO.md)** para los pasos completos de VS Code, Docker y GitHub.
