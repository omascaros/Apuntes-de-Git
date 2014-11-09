
	APUNTES DE GIT
=======================

1. INSTALACIÓN Y CONFIGURACION INICIAL
2. AREAS INTERNAS DE GIT
3. PRIMER REPOSITORIO
4. COMANDOS DE GIT




1. INSTALACIÓN Y CONFIGURACIÓN INICIAL
======================================
Descargamos e instalamos git en nuestro ordenador

	http://git-scm.com/downloads 

Una vez instalado git realizamos la configuración inicial:

	$ git config --global user.name "Your Name Here"
	$ git config --global user.email "your_email@example.com"




2. AREAS INTERNAS DE GIT
========================

Las áreas de git se dividen en 2 grupos:

* Local (dentro de nuestro disco duro)
* Remoto (servidor remoto bien sea en una lan, como en internet)

Dentro de local hay cuatro subáreas:

1. Stash.
2. Workspace / Working area.
3. Index / Staging area.
4. Local Repository.


* **Stash**: Zona temporal donde podemos guardar archivos sin que se añadan al index al hacer comit. (Hablaremos con mas detalle mas adelante).

* **Working area**: Zona de trabajo habitual. En esta zona es donde creamos, modificamos o borramos los archivos de nuestro directorio.

* **Index / Staging area**: Zona donde se guardan las modificaciones realizadas en el Working area, para posteriormente guardarlas en el repositorio.

* **Local Repository**: Zona donde se guarda nuestro proyecto, con un control de las modificaciones que se han realizado.

Dentro de remoto solo hay una subárea: **Upstream repository**.

+----------------------------------------------+---------------------+
|					LOCAL					   | 	REMOTE		     |
+-------+-----------+-------+------------------+---------------------+
| STASH | WORKSPACE | INDEX | LOCAL REPOSITORY | UPSTREAM REPOSITORY |
+-------+-----------+-------+------------------+---------------------+


Aclaración importante:
----------------------
Para poder trabajar con Git hay que tener un concepto claro. Cada vez que hacemos $ git commit... (paso de Index a Local Repository)no estamos guardando los archivos, sino que en cada commit se guardan las MODIFICACIONES realizadas en cada uno de los archivos.




3. PRIMER REPOSITORIO
=====================
Abrimos el $bash y nos dirigimos al directorio donde queremos crear nuestro primer repositorio.

Creamos un directorio nuevo:

	$ mkdir primerRepositorio

Nos posicionamos dentro del directorio nuevo:

	$ cd primerRepositorio

Inicializamos el repositorio:

	$ git init

(Si nos equivocamos más adelante y volvemos a realizar un git init, no pasa nada ni se borra nada)

Para asegurarnos que se ha inicializado correctamente, lanzamos el comando de listado:

	$ ls -la

(si se ha inicializado correctamente nos aparecerá un fichero con el nombre .git)

WORKING AREA
------------

Creamos el archivo readme.md

	$ echo "Descripción del repositorio" > readme.md

WORKING AREA --> INDEX AREA
---------------------------

	$ git add . (el '.' es equivalente a '*' y sirve para seleccionar TODOS los archivos modificados.)

INDEX AREA --> LOCAL REPOSITORY
-------------------------------

	$ git commit -m "Comentario referente a las modificaciones realizadas"




4. COMANDOS DE GIT
==================

Comandos de información
-----------------------

$ git status : Muestra en que rama estamos y que ficheros han sido modificados.

$ git log: Muestra la lista de commits realizados, quien es el autor de este, la fecha del commit y el comentario.

$ git log --oneline: Muestra un log mas compacto. Muestra en una sola línea el identificador del commit y el comentario.

$ git log --oneline --decorate --graph: Muestra un gráfico con las ramas del repositorio ( veremos las ramas mas adelante)


De working area a Staging area
------------------------------

	$ git add <filename>
	$ git add . 		
	$ git add *.c
	$ git add index.html

	$ git add <directory>

el . es equivalente a * y sirve para seleccionar TODOS los archivos modificados.

De Staging area a Working area
------------------------------

Antes del primer commit
	$ git rm --cached <filename>

Después del primer commit
	$ gir rm HEAD <filename>

De Staging area a Local repository
----------------------------------
	$ git commit -m "comentario de las modificaciones" 

	si no ponemos el comentario se abrirá el editor VIM para obligarnos a poner uno


De Working area a Local repository (sin pasar por staging area)
---------------------------------------------------------------

El archivo debe haver sido procesado ya por el repositorio.

	$ git commit -am "coment"

