# Gestión de Contenedores

## Ejecución
Ejecutar un contenedor:
```
docker run nombre_imagen
```
Ejecutar un contenedor en segundo plano:
```
docker run -d nombre_imagen
```
Para acceder a un servicio de un contenedor desde fuera del contenedor, se debe mapear el puerto del contenedor al puerto del host, esto utilizando la opción `-p` al ejecutar el contenedor.
```
docker run -p 8000:8000 imagename:tag
```
Esto mapeará el puerto 8000 del host al puerto 8000 del contenedor. Luego, acceder al servicio desde el navegador o herramienta de cliente de API utilizando la dirección `http://localhost:8000` o la dirección IP de la máquina.

## Administracion de contenedores
Listar contenedores en ejecución:
```
docker ps
```
Listar todos los contenedores:
```
docker ps -a
```
Detener un contenedor en ejecución:
```
docker stop ID_o_nombre_contenedor
```
Iniciar un contenedor detenido:
```
docker start ID_o_nombre_contenedor
```
Eliminar un contenedor:
```
docker rm ID_o_nombre_contenedor
```

# Gestión de Imágenes

## Administracion de imagenes
Listar imágenes locales:
```
docker images
```
Descargar una imagen desde Docker Hub:
```
docker pull nombre_imagen
```
Eliminar una imagen local:
```
docker rmi nombre_imagen
```

## Construcción de Imágenes
Construir una imagen desde un Dockerfile:
```
docker build -t nombre_imagen:etiqueta contexto_directorio
```
Ejemplo de construcción con Dockerfile:
```
docker build -t mi_aplicacion:latest .
```

# Redes Docker
## Administracion de redes
Listar redes Docker:
```
docker network ls
```
Crear una red Docker:
```
docker network create nombre_red
```
Conectar un contenedor a una red:
```
docker network connect nombre_red nombre_contenedor
```
Inspeccionar una red Docker:
```
docker network inspect nombre_red
```

# Zona horaria Docker
## Ver zona horaria
Verificar la zona horaria del sistema dentro del contenedor
```
docker exec -it CONTAINER_ID date
```
## Actualizar informacion de zona horaria
El proceso puede variar según la distribución de Linux utilizada en la imagen del contenedor. Por ejemplo, si estás utilizando una imagen basada en Debian/Ubuntu, puedes ejecutar:
```
docker exec -it CONTAINER_ID apt-get update
docker exec -it CONTAINER_ID apt-get install -y tzdata
```
Luego, configura la zona horaria:
```
docker exec -it CONTAINER_ID dpkg-reconfigure tzdata
```
## Configuración de la Zona Horaria en el Dockerfile
```
FROM python:3.11.5

# Configura la zona horaria
ENV TZ=America/Bogota
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone

WORKDIR /usr/bin/app

# ... (resto del Dockerfile)
```
Esta configuración establece la zona horaria directamente en la imagen durante el proceso de construcción.

Estos son solo algunos de los comandos básicos de Docker. Puedes explorar más opciones y funcionalidades en la documentación oficial de Docker: [Docker Documentation](https://docs.docker.com/).

