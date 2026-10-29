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



Consulta **[GUIA_PASO_A_PASO.md](GUIA_PASO_A_PASO.md)** para los pasos completos de VS Code, Docker y GitHub.
