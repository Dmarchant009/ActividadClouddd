# Actividad_15_11_Jona_Dani
Proyecto de Aplicación PHP + MariaDB con Docker Compos

Prerrequisitos

Para poder ejecutar este proyecto, necesitarás tener instalado el siguiente software en tu máquina:

Git: Para clonar el repositorio.

Docker Desktop: (o Docker Engine + Docker Compose) Para construir y correr los contenedores.

Cómo Ejecutar el Proyecto

Sigue estos pasos para levantar la aplicación:

1. Clonar el Repositorio

Abre tu terminal y clona este repositorio en tu computadora:

git clone [https://github.com/Dmarchant009/ActividadClouddd.git](https://github.com/Dmarchant009/ActividadClouddd.git)


2. Navegar a la Carpeta

Entra a la carpeta que acabas de clonar:

cd ActividadClouddd

3. Construir e Iniciar los Contenedores

Este es el comando principal. Usamos --build para asegurarnos de que se construya la imagen de PHP personalizada con los drivers de MySQL que necesita.

docker compose up -d --build


Docker descargará las imágenes, construirá tu Dockerfile de app-php, creará la red app-cloud, el volumen dbcloud, y arrancará los contenedores db-cloud y web-cloud.

4. Esperar el Arranque

El contenedor web-cloud no arrancará hasta que el healthcheck de db-cloud (el SELECT 1) sea exitoso. Esto puede tardar entre 15 y 30 segundos.

Verificación

Una vez que los contenedores estén corriendo:

Abre tu navegador web.

Visita la dirección: http://localhost:8080

Deberías ver una página con el título "Nombres del Grupo (desde la Base de Datos)" y la lista de "Dani Marchant" y "Jona Rojas" cargada desde la base de datos.

Si ves un error, espera 10 segundos más y refresca la página.

Comandos Útiles

Detener la Aplicación

Para detener y eliminar los contenedores (pero sin borrar la base de datos):

docker compose down

Reiniciar y Borrar la Base de Datos

El archivo init.sql (que crea la tabla nombres) solo se ejecuta la primera vez que se crea el volumen de la base de datos.

Si quieres borrar la base de datos por completo y forzar que init.sql se ejecute de nuevo (para empezar de cero), debes usar el comando down con la bandera -v (de "volúmenes"):

docker compose down -v


Estructura del Proyecto



