---
title: "Taller 2: Creación de un clúster DRBD + OCFS2"
---

## ¿Qué vas a aprender en este taller?

* Configurar un clúster DRBD Single-primary.
* Configurar un clúster DRBD Dual-primary.
* Usar los sistemas de ficheros OCFS2 o GFS2 para que el clúster funcione de forma adecuada.

## ¿Qué tienes que hacer?

Configura un escenario con dos máquinas. Cada una tiene que tener dos discos adicionales (tamaño 2Gb para que la sincronización sea rápida).

* Crea dos recursos DRBD: `wwwdata` y `dbdata`. Cada uno utilizarán uno de los discos de cada máquina.
* Configura en modo Single-primary el recurso `wwwdata`. 
    * Una vez creado y sincronizado el recurso, formatéalo con XFS.
    * Monta el recurso en el nodo primario y crea un fichero. ¿Se puede montar en el secundario?
    * Desmonta el recurso.
    * Cambia los roles, pon primario el que era secundario, y secundario el primario. 
    * Monta el recurso en el que ahora es primario y comprueba que existe el fichero creado anteriormente.
* Configura en modo Dual-primary el recurso `dbdata`.
    * Una vez creado y sincronizado el recurso, configúralo en modo Dual-primary.
    * Crea un clúster OCFS2.
    * Crea un volumen OCFS2 en el recurso (`mkfs.ocfs2`).
    * Monta en los nodos el recurso, y prueba a escribir en los dos al mismo tiempo.
{% capture notice-text %}
## ¿Qué tienes que entregar?

1. La salida del comando `drbdadm status wwwdata`.
2. Prueba de funcionamiento del modo Single-primary.
3. La salida del comando `drbdadm status dbdata`.
4. Prueba de funcionamiento del modo Dual-primary.
5. Muestra al profesor el funcionamiento del modo Dual-primary.

{% endcapture %}<div class="notice--info">{{ notice-text | markdownify }}</div>		
