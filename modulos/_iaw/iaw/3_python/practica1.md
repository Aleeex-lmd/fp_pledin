---
title: "Práctica 1 / 2: Instalación/migración de aplicaciones web Python"
---

## Entorno de desarrollo 

Vamos a desplegar la aplicación del tutorial de django. Utiliza una máquina de openstack como entorno de desarrollo.

Vamos a configurar tu equipo como entorno de desarrollo para trabajar con la aplicación, para ello:

* Realiza un fork del repositorio de GitHub: [https://github.com/josedom24/django_tutorial](https://github.com/josedom24/django_tutorial).
* Crea un entorno virtual de python3 e instala las dependencias necesarias para que funcione el proyecto.
* Comprueba que vamos a trabajar con una base de datos sqlite. ¿Qué fichero tienes que consultar? ¿Cómo se llama la base de datos que vamos a crear?
* Crea la base de datos. A partir del modelo de datos se crean las tablas de la base de datos.
* Crea un usuario administrador.
* Ejecuta el servidor web de desarrollo y entra en la zona de administración (`/admin`) para comprobar que los datos se han añadido correctamente.
* Crea dos preguntas, con posibles respuestas.
* Comprueba en el navegador que la aplicación está funcionando, accede a la url `/polls`.
* Configura el servidor web apache2 con el módulo wsgi para servir la página web. 

{% capture notice-text %}
En este momento, muestra al profesor la aplicación funcionando. Entrega una documentación resumida donde expliques los pasos fundamentales para realizar esta tarea. Y pantallazos que demuestren que la aplicación está funcionando. 
{% endcapture %}<div class="notice--info">{{ notice-text | markdownify }}</div>

## Entorno de producción

Vamos a realizar el despliegue de nuestra aplicación en un entorno de producción, para ello vamos a utilizar nuestro VPS, sigue los siguientes pasos:

* Clona tu repositorio en el VPS.
* Crea un entorno virtual e instala las dependencias de tu aplicación.
* Instala el módulo que permite que python trabaje con mysql: 

		(env)$ pip install mysqlclient

* Crea una base de datos y un usuario en mysql.
* Configura la aplicación para trabajar con mysql, para ello modifica la configuración de la base de datos en el archivo `settings.py`:

		DATABASES = {
		    'default': {
		        'ENGINE': 'django.db.backends.mysql',
		        'NAME': 'myproject',
		        'USER': 'myprojectuser',
		        'PASSWORD': 'password',
		        'HOST': 'localhost',
		        'PORT': '',
		    }
		}

* Crea una copia de seguridad de la base de datos. Ten en cuenta que en el entorno de desarrollo vas a tener una base de datos sqlite, y en el entorno de producción una mariadb, por lo tanto es recomendable para hacer la copia de seguridad y recuperarla con los comandos: `python manage.py dumpdata` y `python manage.py loaddata`, para [más información](https://coderwall.com/p/mvsoyg/django-dumpdata-and-loaddata).
* Configura el servidor de aplicaciones uwsgi, creando una unidad de systemd como hicimos en el taller 2 y configura nginx como proxy inverso para servir la aplicación.
* Debes asegurarte que el contenido estático se está sirviendo: ¿Se muestra la imagen de fondo de la aplicación? ¿Se ve de forma adecuada la hoja de estilo de la zona de administración?
* Desactiva en la configuración el modo debug a False. Para que los errores de ejecución no den información sensible de la aplicación.
* La página web debe ser accesible usando https, en la URL: `https://python.tudominio.algo`.
* Muestra la página funcionando. En la zona de administración se debe ver de forma adecuada la hoja de estilo.

{% capture notice-text %}
En este momento, muestra al profesor la aplicación funcionando. Entrega una documentación resumida donde expliques los pasos fundamentales para realizar esta tarea y pantallazos donde se vea que todo está funcionando. 
{% endcapture %}<div class="notice--info">{{ notice-text | markdownify }}</div>

