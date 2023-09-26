# Tarea trabajando con Volumenes

### **1. Descarga la imagen 'httpd' y comprueba que está en tu equipo:**

Para descargar la imagen, es necesario utilizar la web de [Docker](https://hub.docker.com/_/httpd).

Ubicando la imagen de 'httpd', descargaremos la ultima versión empleando el siguiente comando en el terminal:

> `$ docker run -dit --name dam_http -p 8080:80 httpd:2.4`

Al lanzar el siguiente comando, podemos verificar que la imagen fue instalada exitosamente con el siguiente comando:

>`docker image ls -a`

| REPOSITORY  | TAG | IMAGE ID | CREATED | SIZE |
|-------------|-----|----------|---------|------|
|httpd        |2.4  |7860e7628717|1 minute ago| 168MB|

### **2. Crea un contenedor con el nombre 'dam_httpd'**

Como bien vimos en el apartado anterior, utilizamos la variable *"--name"* para nombrar el contenedor.

Con el siguiente comando podemos verificar que el contenedor esta creado y en ejecución:

>`docker ps`

| CONTAINER ID  | IMAGE | COMMAND | CREATED | STATUS | PORTS | NAMES |
|---------------|-------|---------|---------|--------|------|-------|
|2fa4f100c08b   |httpd:2.4 | "httpd-foreground"| 2 minutes ago    | Up 2 minutes ago   | 0.0.0.0:80->80/tcp, :::80->80/tcp | dam_httpd |

### 3. Si quieres poder acceder desde el navegador de tu equipo, ¿qué debes hacer?

Se accede gracias a la IP del ordenador, además de añadir la extensión del puerto (en esta caso 8080).

>`10.0.9.82:8080`

### 4. Utiliza bid mount para que el directorio del apache2 'htdocs' este montado un directorio que tu elijas.

Con el uso del siguiente comando, debemos añadir primero la ruta absoluta de la carpeta en la que deseamos montar el *"htdocs* con la variable *"-v*, seguidamente la ruta donde está de manera predeterminada

>`docker run -dit --name dam_http -p 8080:80 -v /home/dam2/Documentos/SXE/SXE_Boletin2/htdocs:/usr/local/apache2/htdocs httpd:2.4`

### 5. Realiza un 'hola mundo' en HTML (usa Code) y comprueba que accedes desde el navegador.

