Actividad DAD - Docker Tutorial
Fecha: 05/05/2026
Autor: Sanchez Martin
Materia: DAD

ejem01 - Contenedor con Apache + PHP
Descripción
Se creó una imagen Docker (usando Podman) basada en php:8.2-apache que copia una página web simple y expone el puerto 80.

Pasos realizados
Creación del Dockerfile:

text
FROM php:8.2-apache
RUN apt-get update && apt-get install -y vim
COPY src/ /var/www/html
EXPOSE 80
Construcción de la imagen:

text
podman build -t miapache-php .
Ejecución del contenedor:

text
podman run -dit --name miapache-php -p 5555:80 miapache-php
Edición del index.html desde dentro del contenedor usando nano:

text
podman exec -it miapache-php /bin/bash
cd /var/www/html
nano index.html
Capturas
Las capturas de pantalla se encuentran dentro de la carpeta ejem01/capturas/:

terminal-vi.png - Edición con nano dentro del contenedor

navegador.png - Página web funcionando en navegador

ejem02 - Script run.sh
Comandos ejecutados manualmente
Los comandos del script run.sh se ejecutaron uno por uno en PowerShell:

text
podman rm -f miapache-php
podman rmi -f miapache-php
podman build -t miapache-php .
podman run -dit --name miapache-php -p 5555:80 miapache-php
Explicación de cada comando
podman rm -f miapache-php: Elimina el contenedor si existe (forzado)

podman rmi -f miapache-php: Elimina la imagen si existe (forzado)

podman build -t miapache-php .: Construye una nueva imagen

podman run -dit --name miapache-php -p 5555:80 miapache-php: Ejecuta el contenedor en segundo plano

Resultado
El contenedor se reconstruyó y volvió a funcionar correctamente en http://localhost:5555.

Captura
La captura de pantalla de los comandos ejecutados se encuentra en ejem01/capturas/comandos-run-sh.png

ejem03 - Portabilidad de scripts .sh
Pregunta
¿Qué inconvenientes tiene correr scripts de SO (.sh) en diferentes plataformas?

Respuesta
No son nativos en Windows: Requieren WSL, Git Bash o PowerShell para ejecutarse

Comandos específicos de Unix/Linux: rm -f, chmod +x no existen en Windows puro

Rutas diferentes: Linux usa /, Windows usa \

Permisos de ejecución: chmod +x no funciona en Windows

Dependencias externas: El script asume que podman o docker están instalados

Mejor práctica: Usar docker-compose.yml o podman-compose.yml para entornos multiplataforma
