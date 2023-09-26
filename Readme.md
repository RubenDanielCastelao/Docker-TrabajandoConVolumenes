# Instrucciones para Configurar Contenedores Docker con Apache HTTP Server

## 1-.Descarga la imagen 'httpd' y comprueba que está en tu equipo.

Para descargar la imagen 'httpd', se usara este comando:

```bash
docker pull httpd
```

Y se comprobara que esta en el equipo con el siguiente:

```bash
docker images
```

## 2-.Crea un contenedor con el nombre 'dam_web1'.

Crearemos un contenedor de nombre 'dam_web1' utilizando la imagen 'httpd', mediante este comando:

```bash
docker run -di -p 8000:80 --name dam_web1 httpd
```

## 3-.Si quieres poder acceder desde el navegador de tu equipo, ¿qué debes hacer?

Se daran los puertos al contenedor utilizando la opción `-p` al crear el contenedor. En el ejemplo anterior, hemos expuesto el puerto 80 del contenedor al puerto 8000 de tu equipo.

Luego buscaremos la ip de nuestro equipo y la introduciremos en el buscador de la siguiente forma:

```bash
http://tuIP:8000
```

## 4-.Utiliza bind mount para que el directorio del Apache2 'htdocs' esté montado en un directorio que tú elijas.

Usaremos bind mount para montar el directorio del Apache2 'htdocs' en el directorio que desees, de esta forma:

```bash
docker run -di -p 8000:80 -v /home/dam2/Documentos/XSE/HTML:/usr/local/apache2/htdocs/ --name dam_web1 httpd
```

En este caso usaremos un directorio llamado `HTML`.

## 5-.Realiza un 'hola mundo' en HTML y comprueba que accedes desde el navegador.

Crea un archivo HTML simple llamado 'index.html' con el contenido 'Hola Mundo' y colocalo en la carpeta anteriormente indicada, luego accede utilizando la URL http://localhost:8000 y deberías ver la página 'Hola Mundo'.

Este es el HTML usado en este caso:

```html
<html>
    <body>
        <h1>Hola mundo!</h1>
    </body>
</html>
```

## 6-.Crea otro contenedor 'dam_web2' con el mismo volumen y a otro puerto, por ejemplo, 9080.

Para crear un segundo contenedor 'dam_web2' con el mismo volumen y en el puerto 9080, ejecuta el siguiente comando:

```bash
docker run -di -p 9080:80 -v /home/dam2/Documentos/XSE/HTML:/usr/local/apache2/htdocs/ --name dam_web2 httpd
```

## 7-.Comprueba que los dos servidores 'sirven' la misma página, es decir, cuando consultas en el navegador:

Abrimos el navegador con ambos puertos, tal como en el ejemplo inferior, y vemos que en ambos se muestra el mismo 'Hola mundo!'.

- http://tuIP:9080
- http://tuIP:8000

## 8-.Realiza modificaciones de la página y comprueba que los dos servidores 'sirven' la misma página

Igual que en la anterior tarea, simplemente modificaremos el HTML y accederemos a los 2 puertos, revisando así que ambas paginás hayan sufrido las modificaciones del HTML.