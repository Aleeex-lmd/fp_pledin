---
title: "Práctica: IC/DC con Jenkins"
---

El objetivo de esta práctica es el desarrollo gradual de un Pipeline que vaya realizando tareas sobre el repositorio de una aplicación.

La aplicación con la que vamos a trabajar será tu fork de la aplicación django Polls. Como hemos visto esta aplicación que implementa el tutorial de Django tiene implementado un módulo de pruebas.

Vamos a construir el Pipeline en varias fases:

## Ejercicio 1: Testeo de la aplicación

Vamos a comenzar a crear un pipeline, que realice las siguientes tareas:

1. Clone el repositorio.
2. Instale los requerimientos python.
3. Realice los tests al programa.

Este pipeline se tiene que ejecutar sobre la imagen `python:3`. Otras consideraciones:

* Este pipeline se disparará cuando observe un cambio en el repositorio. Esta comprobación se hará cada minuto.

{% capture notice-text %}
## Entrega

1. Una captura de pantalla donde se vea la salida de un build que se ha ejecutado de manera correcta.
2. Modifica el código de la aplicación para que se produzca un fallo en el código. **Recuerda que para hacer fallar un test, no hay que tocar el fichero `test.py`. Los test no se pasan porque al modificar el código de la aplicación se dejan de cumplir las condiciones indicadas en los test.**
3. Una captura de pantalla donde se vea la salida de un build que se ha ejecutado con errores de testeo.
{% endcapture %}<div class="notice--info">{{ notice-text | markdownify }}</div>

## Ejercicio 2: Construcción de una imagen docker

Modifica el pipeline para que después de hacer el test sobre la aplicación, genere una imagen docker. tienes que tener en cuenta que los pasos para generar la imagen lo tienes que realizar en la máquina donde está instalado Jenkins. Tendrás que añadir las siguientes acciones:

1. Construir la imagen con el `Dockerfile` que tengas en el repositorio.
2. Subir la imagen a tu cuenta de Docker Hub.
3. Borrar la imagen que se ha creado.

Por lo tanto tienes que estudiar el apartado [Ejecución de un pipeline en varios runner](runner.html) para ejecutar el pipeline en dos runner:

* En el contenedor docker a partir de la imagen `python:3` los pasos del ejercicio1.
* En la máquina de Jenkins los pasos de este ejercicio.

Otras consideraciones:

* Cuando termine de ejecutar el pipeline te mandará un correo de notificación.
* El pipeline se guardará en un fichero `Jenkinsfile` en tu repositorio, y la configuración del pipeline hará referencia a él.

{% capture notice-text %}
## Entrega

1. Una captura de pantalla donde se vea la salida de un build que se ha ejecutado de manera correcta.
2. Una captura de pantalla de tu cuenta de Docker Hub donde se vea la imagen subida de último build.
3. Introduce un fallo en el `Dockerfile` y muestra la salida del build donde se produce el error.
4. Entrega la URL para ver el `Jenkinsfile`.
5. Pantallazo con el correo que has recibido de la ejecución del pipeline.
{% endcapture %}<div class="notice--info">{{ notice-text | markdownify }}</div>

## Ejercicio 3: Despliegue de la aplicación

Amplía el pipeline anterior para que tenga una última etapa donde se haga el despliegue de la imagen que se ha subido a Docker Hub en tu entorno de producción (VPS). Algunas pistas:

* Busca información de cómo hacer el despliegue a un servidor remoto (ssh, buscando algún plugin con esa funcionalidad,...)
* Si vas a hacer conexiones por ssh, tendrás que guardar una credencial en tu Jenkins con el nombre de usuario y contraseña.
* Para el despliegue deberá usar el fichero `docker-compose.yaml` que has generado en otras prácticas.
* Se deberá borrar el contenedor con la versión anterior, descargar la nueva imagen y crear un nuevo contenedor.

Otras consideraciones:

* Cambia el disparador del pipeline. Configáralo con un webhook de github, para que cada vez que se produce un push se ejecute el pipeline. Para que el webhook pueda acceder a tu Jenkins puedes usar [ngrok](https://ngrok.com/).

{% capture notice-text %}
## Entrega

1. Demustra al profesor como se realiza la IC/DC completo.
{% endcapture %}<div class="notice--info">{{ notice-text | markdownify }}</div>