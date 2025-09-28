🐳 Proyecto Dockerizado con Nginx
Este repositorio explica cómo desplegar un proyecto web en un contenedor Docker que ya está creado y ejecutando Nginx. El proceso incluye copiar el proyecto desde tu máquina local al contenedor y cambiar el archivo principal index.html por otro archivo existente (ventaentradas.html) directamente dentro del contenedor.

📦 Requisitos
Contenedor Docker con Nginx ya creado y en ejecución

Proyecto local con el archivo ventaentradas.html

Docker instalado y acceso a terminal

🚀 Pasos para desplegar el proyecto
1. Identificar el contenedor
Primero, obtén el nombre o ID del contenedor Nginx:

bash
docker ps
Ejemplo de salida:

Código
CONTAINER ID   IMAGE         NAME           PORTS
abc123def456   nginx:latest  mi-nginx       0.0.0.0:8080->80/tcp

2. Copiar el proyecto al contenedor
Supongamos que tu proyecto está en ~/misitio. Copia todos los archivos al directorio donde Nginx sirve contenido (por defecto /usr/share/nginx/html):

bash
docker cp ~/misitio/. mi-nginx:/usr/share/nginx/html/
Reemplaza mi-nginx por el nombre real de tu contenedor.

3. Renombrar el archivo HTML dentro del contenedor
Accede al contenedor mediante:

bash
docker exec -it mi-nginx(nombre o ID de del contenedor) sh
Una vez dentro, navega al directorio de Nginx:

sh
cd /usr/share/nginx/html
Renombra el archivo ventaentradas.html a index.html:

sh
mv ventaentradas.html index.html
Sal del contenedor:

sh
exit
4. Verificar en el navegador
Abre tu navegador y accede a:

Código
http://localhost:8080 o dentro de Docker, pulsa en el puerto
Deberías ver el contenido de ventaentradas.html como página principal.
