---
title: Servidor de correo en los servidores de clase
---

## Ejercicio 1: Envío local, entre usuarios del mismo servidor

Instala y configura un servidor de correo en `apolo`. El nombre del sistema de correo será tu nombre de dominio `tudominio.gonzalonazareno.org`.

Utilizando la utilidad `mail` manda un correo desde un usuario del servidor a otro usuario del servidor. El usuario destinatario debe leer el correo con el mismo programa.

## Ejercicio 2: Envío de correo desde usuarios del servidor a correos de internet

Configura tu servidor de correo para que use como relay el servidor de correo de nuestra red `babuino-smtp`. Con la utilidad `mail` envía un correo a tu cuenta personal de gmail, hotmail,... 

Muestra el log del sistema donde se comprueba que el correo se ha enviado con éxito.

Comprueba las cabeceras del correo que has recibido e indica donde vemos los servidores por los que ha pasado el correo.

## Ejercicio 3: Recibir correos desde internet a usuarios del servidor

En este ejercicio debes responder desde tu cuenta de correo personal al correo que recibiste en el ejercicio anterior. Recuerda que para que todo funcione debes indicarle al profesor el nombre de tu dominio para que configure de manera adecuada el parámetro `relay_domains` en `babuino-smtp`. Además debes configurar de manera adecuada el registro MX de tu servidor DNS.

Muestra el log del sistema donde se comprueba que el correo se ha recibido con éxito.


## Ejercicio 4: Recepción de correo electrónico usando nuestro servidor de correos

## Ejercicio 5: Envío de correo electrónico usando nuestro servidor de correos

