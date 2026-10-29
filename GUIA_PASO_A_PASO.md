# Guía paso a paso — Práctica 6 (Windows, VS Code, Docker y GitHub)

> No necesitas crear los archivos manualmente: están incluidos en este proyecto.

## Paso 1. Descomprimir y abrir en VS Code

1. Extrae `Practica-6-Nginx-Docker.zip` en una carpeta que encuentres fácilmente, por ejemplo `Documentos`.
2. Abre VS Code.
3. Ve a **Archivo > Abrir carpeta** y elige **Practica-6-Nginx-Docker** (la carpeta que contiene `docker-compose.yml`).
4. Asegúrate de ver `src/index.html`, `docker-compose.yml` y `README.md` en el explorador izquierdo.
5. Abre la terminal en **Terminal > Nuevo terminal**. En Windows puede salir **PowerShell**; está bien.

## Paso 2. Comprobar programas

Abre Docker Desktop y espera a que indique que el motor está funcionando. En la terminal de VS Code, ejecuta cada comando por separado:

```powershell
docker --version
docker compose version
git --version
```

Si `git` no se reconoce, instala Git for Windows y reinicia VS Code antes de continuar. Si Docker no conecta con su motor, abre Docker Desktop.

## Paso 3. Levantar Nginx

En la terminal, dentro de la carpeta principal del proyecto:

```powershell
docker compose up -d
```

- `up` crea e inicia el servicio declarado en Compose.
- `-d` lo mantiene ejecutándose en segundo plano.
- La primera vez, Docker puede descargar la imagen Nginx.

**No necesitas crear un Dockerfile:** esta práctica usa directamente una imagen existente de Nginx.

## Paso 4. Comprobar que funciona

Ejecuta:

```powershell
docker compose ps
```

Deberías ver un servicio `nginx` activo (`Up`) y un puerto similar a `0.0.0.0:8080->80/tcp`.

Abre en tu navegador:

**http://localhost:8080**

Debe aparecer la página con **¡Hola Mundo!**.

Puedes consultar los logs con:

```powershell
docker compose logs nginx
```

Y comprobar el HTTP en PowerShell con:

```powershell
curl.exe -I http://localhost:8080
```

Una respuesta `HTTP/1.1 200 OK` indica que Nginx está respondiendo.

## Paso 5. Capturas de pantalla recomendadas

Toma capturas reales de:

1. **VS Code:** estructura del proyecto y `docker-compose.yml` abierto.
2. **Terminal:** resultado de `docker compose ps` con el contenedor funcionando.
3. **Navegador:** `http://localhost:8080` mostrando **¡Hola Mundo!**.
4. **GitHub:** archivos del repositorio una vez publicados.

## Paso 6. Crear el repositorio público en GitHub

1. Inicia sesión en **https://github.com**.
2. Haz clic en **+** > **New repository**.
3. Escribe exactamente este nombre (o el que prefieras): `Practica-6-Nginx-Docker`.
4. Marca **Public**.
5. **No** marques las opciones de agregar README, .gitignore o licencia, porque el proyecto ya incluye los primeros dos.
6. Pulsa **Create repository**.
7. Copia tu nombre de usuario de GitHub para el comando de conexión.

## Paso 7. Subir desde la terminal de VS Code

Con la terminal abierta en la carpeta del proyecto, ejecuta los siguientes comandos **uno a uno**:

```powershell
git init
git add .
git commit -m "Practica 6: servidor Nginx con Docker Compose"
git branch -M main
git remote add origin https://github.com/TU_USUARIO/Practica-6-Nginx-Docker.git
git push -u origin main
```

**Reemplaza `TU_USUARIO` por tu usuario real de GitHub.** Si escogiste otro nombre de repositorio, reemplaza también `Practica-6-Nginx-Docker` en la URL.

> Si Git solicita configurar tu identidad antes del `commit`, escribe estos dos comandos (con tus propios datos) y vuelve a ejecutar el `commit`:
>
> ```powershell
> git config --global user.name "Tu Nombre"
> git config --global user.email "tu-correo-de-github@ejemplo.com"
> ```

GitHub puede abrir una ventana del navegador para autorizar el acceso. Inicia sesión y completa la autorización correspondiente. No publiques contraseñas ni tokens en el código.

## Paso 8. Verificar y entregar

1. Entra a `https://github.com/TU_USUARIO/Practica-6-Nginx-Docker` con tu usuario correcto.
2. Verifica que se vean `src`, `docker-compose.yml`, `README.md` y la guía.
3. Comprueba que el repositorio dice **Public**.
4. Copia la URL del repositorio (la dirección **sin** `.git`, si lo prefieres).
5. Pega esa URL pública en el foro de la práctica.

**Ejemplo de mensaje para el foro:**

> Práctica 6 completada: servidor web Nginx con Docker Compose. Repositorio público: https://github.com/TU_USUARIO/Practica-6-Nginx-Docker

## Paso 9. Apagar el servidor después de las capturas

```powershell
docker compose down
```

Para iniciarlo de nuevo:

```powershell
docker compose up -d
```

## Problemas frecuentes

**Aparece `port is already allocated` o el 8080 está ocupado.**

- Edita `docker-compose.yml` y cambia `"8080:80"` por `"8081:80"`.
- Ejecuta `docker compose up -d` de nuevo.
- Abre `http://localhost:8081`.

**Aparece un error de conexión con el motor de Docker.**

- Abre Docker Desktop y comprueba que está ejecutándose. Luego repite `docker compose up -d`.

**Aparece la página predeterminada de Nginx en vez de tu HTML.**

- Comprueba que la terminal está en la carpeta que contiene `docker-compose.yml`.
- Comprueba que existe `src/index.html` y que la ruta de volumen es `./src:/usr/share/nginx/html:ro`.
- Intenta actualizar el navegador con Ctrl + F5.

**`git commit` no sabe quién eres.**

- Configura `user.name` y `user.email` como se indica en el Paso 7.

**`remote origin already exists`.**

- Comprueba `git remote -v`. Si apunta a una URL incorrecta, actualízala con:

```powershell
git remote set-url origin https://github.com/TU_USUARIO/Practica-6-Nginx-Docker.git
```

**GitHub devuelve un error de permisos al subir.**

- Asegúrate de iniciar sesión en la cuenta correcta y de tener permisos sobre el repositorio. Los tokens personales no se escriben en el README ni se suben a GitHub.

## Lista de verificación final

- [ ] La carpeta `src` contiene `index.html`.
- [ ] `docker-compose.yml` monta `./src` en `/usr/share/nginx/html`.
- [ ] `docker compose up -d` se ejecuta sin error.
- [ ] `docker compose ps` muestra Nginx activo.
- [ ] `http://localhost:8080` muestra «¡Hola Mundo!» (o 8081 si cambiaste el puerto).
- [ ] El repositorio en GitHub es público.
- [ ] La URL pública está publicada en el foro.
