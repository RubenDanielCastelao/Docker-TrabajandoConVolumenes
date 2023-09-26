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

