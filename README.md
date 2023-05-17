# DockerGuide --

1. Montar la imagen de MariaDB con el tag jammy, publicar en el puerto 3306 del contenedor con el puerto 3306 de nuestro equipo, colocarle el nombre al contenedor de world-db (--name world-db) y definir las siguientes variables de entorno:

	*MARIADB_USER=example-user
	*MARIADB_PASSWORD=user-password
	*MARIADB_ROOT_PASSWORD=root-secret-password
	*MARIADB_DATABASE=world-db


2. Descargar Imagen de Docker Hub con el siguiente comando 
	*docker pull mariadb:latest

3. Generar container con el siguiente Comando
	*docker container run -dp 3306:3306 --name world-db --env MARIADB_USER=example-user --env MARIADB_PASSWORD=example-password --env MARIADB_ROOT_PASSWORD=root-secret-password --env MARIADB_DATABASE=world-db mariadb 


***-----------TIPOS DE VOLUMENES-------------**

1. Named Volumes	Este es el volumen más usado. 
	*Crear un nuevo volumen*
		*docker volume create todo-db*
2. Listar los volúmenes creados
	*docker volume ls*
3. Inspeccionar el volumen específico 
	*docker volume inspect todo-db*
4. Remueve todos los volúmenes no usados
	*docker volume prune* 
5. Remueve uno o más volúmenes especificados
	*docker volume rm VOLUME_NAME*
6. Usar un volumen al correr un contenedor
	*docker run -v todo-db:/etc/todos getting-started Se debe verificar en la documentación de cada DB donde guarda los datos* 
	*Ej. *docker container run -dp 3306:3306 --name world-db --env MARIADB_USER=example-user --env MARIADB_PASSWORD=example-password --env MARIADB_ROOT_PASSWORD=root-secret-password --env MARIADB_DATABASE=world-db mariadb \
			--volume world-db:/var/lib/mysql* 


***----------Container Networking------------**

Regla de oro:

Si dos o más contenedores están en la misma red, podrán hablar entre sí. Si no lo están, no podrán

1. Ver comandos de network
	*docker network*
2. Crear una nueva red
	*docker network create todo-app*
3. Listar todas las redes creadas
	*docker network ls*
4. Inspeccionar una red
	*docker network inspect <NAME o ID>*
5. Borrar todas las redes no usadas
	*docker network prune*
6. Correr una imagen y unirla a la red

	*Ej. *docker container run -dp 3306:3306 --name world-db --env MARIADB_USER=example-user --env MARIADB_PASSWORD=example-password --env MARIADB_ROOT_PASSWORD=root-secret-password --env MARIADB_DATABASE=world-db mariadb \
			--volume world-db:/var/lib/mysql \
			--network todo-app* 









	
