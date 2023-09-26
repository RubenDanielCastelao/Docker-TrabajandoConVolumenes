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

