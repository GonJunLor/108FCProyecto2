# Fundamentos de contenerización
## Actividad 2. Modificar un sitio web en ejecución.

Paso 1. Partimos de la imagen construida en la actividad anterior
* Como no tengo la imagen vuelvo a construirla y compruebo que se ha creado correctamente:
```
sudo docker image build --tag 108fcproyecto2:1.0 .
sudo docker images
```
Paso 2. Ejecutar el contenedor en el puerto 8080, con el nombre actividad2, es importante montar el directorio actual del host en el directorio /usr/share/nginx/html/ dentro del contenedor
```
sudo docker container run -d -p 8080:80 --name 108fcproyecto2 -v "$PWD":/usr/share/nginx/html 108fcproyecto2:1.0
```
* Comprobamos que se ha creado correctamente
```
sudo docker container ls
```

Paso 3. Comprobación: http://localhost:8080
```
http://localhost:8080
```

Paso 4. Se pide modificar el fichero index.html desde el host.
* Modifico el index.html desde visual studio code y comprueba que se actualizan los cambios

Paso 5. Se ha producido cambios, http://localhost:8080

## Crear y subir imagen a dockerHub
* Creamos la imagen del contenedor editado y comprobamos que se ha creado
```
sudo docker commit 108fcproyecto2 108fcproyecto2:1.0
docker images
```
* Guardamos la imagen en un archivo .tar
```
sudo docker save -o 108fcproyecto2version2.tar 108fcproyecto2:1.0 
```
* Iniciamos sesión en dockerHub con el navegador.
```
sudo docker login
```
* Creamos el repositorio 108fcproyecto2 en dockerHub desde su web
* Creamos una etiqueta a la imagen que vamos a subir
```
sudo docker tag 108fcproyecto2:1.0 gonjunlor/108fcproyecto2:1.0
```
* Subimos la imagen a dockerHub
```
sudo docker push gonjunlor/108fcproyecto2:1.0
```
* Enlace a la imagen del proyecto2 en dockerHub
```
https://hub.docker.com/layers/gonjunlor/108fcproyecto2/1.0/images/sha256-f28b7c4b150451e20ddd9c94c80916f660aac71ae50100a8da439dd37209b2c4
```