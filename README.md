# Actividad DAD - Docker Tutorial

**Fecha:** 05/05/2026  
**Autor:** [PONE TU NOMBRE ACÁ]  
**Materia:** DAD

## ejem01 - Contenedor con Apache + PHP

Se creó una imagen con Podman usando `php:8.2-apache`. La página web muestra el nombre del alumno.

### Capturas

![Edición con Vim dentro del contenedor](ejem01/capturas/terminal-vi.png)
![Página web en navegador](ejem01/capturas/navegador.png)

## ejem02 - Script run.sh

Los comandos del script `run.sh` se ejecutaron manualmente:

- `podman rm -f miapache-php` - Elimina el contenedor si existe
- `podman rmi -f miapache-php` - Elimina la imagen si existe
- `podman build -t miapache-php .` - Construye la imagen
- `podman run -dit --name miapache-php -p 5555:80 miapache-php` - Ejecuta el contenedor

## ejem03 - Portabilidad de scripts .sh

### ¿Qué inconvenientes tiene correr scripts de SO (`.sh`) en diferentes plataformas?

**Respuesta:**

1. **No son nativos en Windows** - Requieren WSL, Git Bash o PowerShell para ejecutarse.

2. **Dependencia de comandos Unix/Linux** - Comandos como `rm -f` o `chmod +x` no existen en Windows puro.

3. **Rutas diferentes** - Linux usa `/` mientras que Windows usa `\`.

4. **Permisos de ejecución** - El comando `chmod +x` no funciona en Windows.

5. **Instalación de dependencias** - El script asume que `podman` o `docker` están instalados y en el PATH.

6. **Mejor práctica** - Para entornos multiplataforma, es recomendable usar `docker-compose.yml` o `podman-compose.yml` en lugar de scripts de shell.

---
*Actividad completada con Podman en Windows*
