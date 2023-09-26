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

Creamos un formato HTML dentro de la carpeta htdocs, que previamente ubicamos como montaje en nuestro servidor.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="stylesheet" href="style.css">
    <title>Document</title>
</head>
<body>
    <h1 class="titulo">
        Hola Mundo
    </h1>
    <div>
        <img src="https://bestpsb.files.wordpress.com/2022/03/mono-loco.png?w=340" alt="" srcset="">
    </div>
</body>
</html>
```

### 6. Crea otro contenedor 'dam_web2' con el mismo volumen y a otro puerto, por ejemplo 9080.

Para esto, repetimos los pasos realizados en el apartado 4. Con la diferencia que en la extensión de la variable *"-p"*, usaremos 9080:80

>`docker run -dit --name dam_web2 -p 9080:80 -v /home/dam2/Documentos/SXE/SXE_Boletin2/htdocs:/usr/local/apache2/htdocs httpd:2.4`

Ademas de esto, podemos observar que la extensión *"--name"* permite cambiar el nombre.

> [!WARNING]  
> De no cambiar el nombre, creara un error por el conflicto de tener dos contenedores en el cual uno esta en uso, independiente de que se encuentre en otro puerto.