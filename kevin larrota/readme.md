1. Comandos Docker utilizados

docker --version

docker-compose --version

docker images

docker-compose up -d

mysql -u root -p

docker stop mysql_db

docker start mysql_db

docker rm mysql_db

docker rmi mysql:8.0



---

2. Descripción de cada paso

Paso 1: Creación del archivo docker-compose.yml
Este archivo se genera para indicarle a Docker qué imagen debe usar (en este caso, MySQL), además del nombre del contenedor, las credenciales y el puerto. De esta manera, la configuración se realiza de forma automática.

Paso 2: Iniciar el contenedor
Desde la terminal se ejecuta el comando:
docker-compose up -d
Con esto, Docker descarga la imagen de MySQL (si no está disponible) y levanta el contenedor con la base de datos lista para su uso.

Paso 3: Comprobar su funcionamiento
Para verificar que todo esté en orden se usa:
docker ps
Este comando muestra si el contenedor de MySQL se encuentra ejecutándose correctamente.

Paso 4: Acceder al contenedor
Para ingresar al entorno del contenedor se utiliza:

docker exec -it mysql_db bash  
mysql -u root -p

Una vez dentro, se puede interactuar directamente con la base de datos MySQL.

Paso 5: Realizar pruebas en la base de datos
Dentro del entorno MySQL se pueden crear bases de datos y tablas, por ejemplo:

CREATE DATABASE empresa;  
USE empresa;  
CREATE TABLE empleados (id INT AUTO_INCREMENT PRIMARY KEY, nombre VARCHAR(100));

Paso 6: Detener el contenedor
Cuando se termina la sesión de trabajo, se puede detener el contenedor con:
docker-compose down
Y si se desea eliminar los datos almacenados:
docker-compose down -v


---

3. Conclusiones u observaciones finales

Docker permite crear y manejar bases de datos sin necesidad de instalarlas directamente en el sistema operativo.
Los contenedores se implementan y eliminan de forma rápida y sencilla.
Gracias a los volúmenes, los datos pueden conservarse incluso después de eliminar el contenedor.
En general, Docker es una herramienta eficiente y profesional para gestionar bases de datos en entornos de desarrollo, ya que con pocos comandos se obtiene un sistema funcional, ideal tanto para la práctica como para el trabajo colaborativo.