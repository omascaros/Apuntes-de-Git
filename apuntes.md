/*********************************\
	APUNTES DE GIT
\*********************************/

1. INSTALACIÓN Y CONFIGURACION INICIAL
2. AREAS INTERNAS DE GIT
3. PRIMER REPOSITORIO
4. COMANDOS DE GIT



1. INSTALACIÓN Y CONFIGURACION INICIAL
======================================
Descargamos e instalamos git en nuestro ordenador

[link](http://git-scm.com/downloads)

Una vez instalado git realizamos la configuración inicial:

	$ git config --global user.name "Your Name Here"
	$ git config --global user.email "your_email@example.com"


2. AREAS INTERNAS DE GIT
========================

Las areas de git se dividen en 2 grupos:

* Local (dentro de nuestro disco duro)
* Remoto (servidor remoto bien sea en una lan como en internet)

Dentro de local hay cuatro subareas:
1. Stash.
2. Working area.
3. Index / Staging area.
4. Local Repository.

**Stash**: Zona temporal donde podemos guardar archivos sin que se añadan al index al hacer comit. (Hablaremos con mas detalle mas adelante).
**Working area**: Zona de trabajo habitual. En esta zona es donde creamos, modificamos o borramos los archivos de nuestro directorio.
**Index / Staging area**: Zona donde se guardan las modificaciones realizadas en el Working area, para posteriormente guardarlas en el repositorio
**Local Repository**: Zona donde se guarda nuestro proyecto, con un control de las modificaciones que se han realizado.

Dentro de remoto solo hay una subarea: **Upstream repository**.

Para poder trabajar en Git hay que tener un concepto claro. Cada vez que hacemos $ git commit... (paso de index a local repository)no estamos guardando en el local repository los archivos, sino que en cada commit se guardan las MODIFICACIONES realizadas en cada uno de los archivos.

					/---------------------------------\
			|---	|		 WORKING DIRECTORY		  |
					\---------------------------------/
		$ git add
					/---------------------------------\
			|-->	|			STAGING AREA          |        --|
					\---------------------------------/
															$ git commit
					/---------------------------------\			 
					|			REPOSITORY            |		  <--|
					\---------------------------------/


3. PRIMER REPOSITORIO
=====================
Abrimos el $bash y nos dirigimos al directorio donde queremos crear nuestro primer repositorio.

Creamos un directorio nuevo:
	$ mkdir primerRepositorio

nos posicionamos dentro del directorio nuevo
	$ cd primerRepositorio

inicializamos el repositorio
	$ git init

WORKING AREA
------------

creamos el archivo readme.md

	$ echo "descripcion del repositorio" > readme.md

INDEX AREA
----------
	$ git add . (el . es equivalente a * y sirve para seleccionar TODOS los archivos modificados.)

	   ó

	$ git add readme.md (tambien podemos elegir el fichero que queremos enviar al repositorio)

LOCAL REPOSITORY
----------------

	$ git -m "Comentario referente a las modificaciones realizadas"


4. COMANDOS DE GIT
==================

comandos de información
-----------------------

$ git status : muestra en que rama estamos y que ficheros han sido modificados.

$ git log: muestra la lista de commits realizados, quien es el autor de este, la fecha del commit y el comentario.

$ git log --oneline: log mas compactor. Muestra en una sola linea el identificador del commit y el comentario.

$ git log --oneline --decorate: muestra un grafico con las ramas del repositorio ( veremos las ramas mas adelante)


working area -> staging area
----------------------------

	$ git add <filename>
	$ git add .
	$ git add *.c
	$ git add index.html

	$ git add <directory>
	

staging area -> working area
----------------------------

# antes del primer commit
	$ git rm --cached <filename>

# después del primer commit
	$ gir rm HEAD <filename>


working area -> local repository
--------------------------------

El archivo debe haver sido procesado ya por el repositorio.

	$ git commit -am "coment"

