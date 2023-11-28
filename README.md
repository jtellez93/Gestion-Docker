### Gestión de Contenedores

1. Ejecutar un contenedor:
```
docker run nombre_imagen
```

2. Ejecutar un contenedor en segundo plano:
```
docker run -d nombre_imagen
```

3. Listar contenedores en ejecución:
```
docker ps
```

4. Listar todos los contenedores:
```
docker ps -a
```

5. Detener un contenedor en ejecución:
```
docker stop ID_o_nombre_contenedor
```

6. Iniciar un contenedor detenido:
```
docker start ID_o_nombre_contenedor
```

7. Eliminar un contenedor:
```
docker rm ID_o_nombre_contenedor
```

## Gestión de Imágenes

8. Listar imágenes locales:
```
docker images
```

9. Descargar una imagen desde Docker Hub:
```
docker pull nombre_imagen
```

10. Eliminar una imagen local:
```
docker rmi nombre_imagen
```

## Construcción de Imágenes

11. Construir una imagen desde un Dockerfile:
```
docker build -t nombre_imagen:etiqueta contexto_directorio
```

12. Ejemplo de construcción con Dockerfile:
```
docker build -t mi_aplicacion:latest.
```

## Redes Docker

13. Listar redes Docker:
```
docker network ls
```

14. Crear una red Docker:
```
docker network create nombre_red
```

15. Conectar un contenedor a una red:
```
docker network connect nombre_red nombre_contenedor
```

16. Inspeccionar una red Docker:
```
docker network inspect nombre_red
```



Estos son solo algunos de los comandos básicos de Docker. Puedes explorar más opciones y funcionalidades en la documentación oficial de Docker: [Docker Documentation](https://docs.docker.com/).

