# HiperBlog
Proyecto personal con metodologías de aprendizaje en Git y Github

### Features

Comandos básicos en la terminal:

pwd: Nos muestra la ruta de carpetas en la que te encuentras ahora mismo.
mkdir: Nos permite crear carpetas (por ejemplo, mkdir Carpeta-Importante).
touch: Nos permite crear archivos (por ejemplo, touch archivo.txt).
rm: Nos permite borrar un archivo o carpeta (por ejemplo, rm archivo.txt). Mucho cuidado con este comando, puedes borrar todo tu disco duro.
cat: Ver el contenido de un archivo (por ejemplo, cat nombre-archivo.txt).
ls: Nos permite cambiar ver los archivos de la carpeta donde estamos ahora mismo. Podemos usar uno o más argumentos para ver más información sobre estos archivos (los argumentos pueden ser -- + el nombre del argumento o - + una sola letra o shortcut por cada argumento).
- ls -a: Mostrar todos los archivos, incluso los ocultos.
- ls -l: Ver todos los archivos como una lista.
cd: Nos permite navegar entre carpetas.
- cd /: Ir a la ruta principal:
- cd o cd ~: Ir a la ruta de tu usuario
- cd carpeta/subcarpeta: Navegar a una ruta dentro de la carpeta donde estamos ahora mismo.
- cd .. (cd + dos puntos): Regresar una carpeta hacia atrás.
- Si quieres referirte al directorio en el que te encuentras ahora mismo puedes usar cd . (cd + un punto).
history: Ver los últimos comandos que ejecutamos y un número especial con el que podemos repetir su ejecución.
! + número: Ejecutar algún comando con el número que nos muestra el comando history (por ejemplo, !72).
clear: Para limpiar la terminal. También podemos usar los atajos de teclado Ctrl + L o Command + L.


Git reset y git rm son comandos con utilidades muy diferentes, pero aún así se confunden muy fácilmente.
git rm
Este comando nos ayuda a eliminar archivos de Git sin eliminar su historial del sistema de versiones. Esto quiere decir que si necesitamos recuperar el archivo solo debemos “viajar en el tiempo” y recuperar el último commit antes de borrar el archivo en cuestión.
Recuerda que git rm no puede usarse así nomás. Debemos usar uno de los flags para indicarle a Git cómo eliminar los archivos que ya no necesitamos en la última versión del proyecto:
•	git rm --cached: Elimina los archivos del área de Staging y del próximo commit pero los mantiene en nuestro disco duro.
•	git rm --force: Elimina los archivos de Git y del disco duro. Git siempre guarda todo, por lo que podemos acceder al registro de la existencia de los archivos, de modo que podremos recuperarlos si es necesario (pero debemos usar comandos más avanzados).
git reset
Este comando nos ayuda a volver en el tiempo. Pero no como git checkout que nos deja ir, mirar, pasear y volver. Con git reset volvemos al pasado sin la posibilidad de volver al futuro. Borramos la historia y la debemos sobreescribir. No hay vuelta atrás.
Este comando es muy peligroso y debemos usarlo solo en caso de emergencia. Recuerda que debemos usar alguna de estas dos opciones:
Hay dos formas de usar git reset: con el argumento --hard, borrando toda la información que tengamos en el área de staging (y perdiendo todo para siempre). O, un poco más seguro, con el argumento --soft, que mantiene allí los archivos del área de staging para que podamos aplicar nuestros últimos cambios pero desde un commit anterior.
•	git reset --soft: Borramos todo el historial y los registros de Git pero guardamos los cambios que tengamos en Staging, así podemos aplicar las últimas actualizaciones a un nuevo commit.
•	git reset --hard: Borra todo. Todo todito, absolutamente todo. Toda la información de los commits y del área de staging se borra del historial.
¡Pero todavía falta algo!
•	git reset HEAD: Este es el comando para sacar archivos del área de Staging. No para borrarlos ni nada de eso, solo para que los últimos cambios de estos archivos no se envíen al último commit, a menos que cambiemos de opinión y los incluyamos de nuevo en staging con git add, por supuesto

git clone url :  se trae los archivos del master a tu repo local.
git add . : para poder agregar todos los cambios a staging.
git commit -m: Para pasarlo al resopositorio
git push: para subirlo al repositorio remoto.
git pull: para bajar los cambios de los ew
git commit -am : ya nos agrega los cambios sin necesidad de hacer un git add .
git branch (Nombre de la rama): Para crear una nueva rama.
git checkout (Nombre de la rama): Para moverme a una rama.
git show: me muestra toda la informacion de donde estoy ubicado y de los cambios que he realizado.
git merge (Nombre de la rama a fucionar); Lo hacemos desde la rama Master para no perder los avances. y despues nos cambiamos a la rama de trabajo y hacemos lo mismo para fusionar lo del master a nuestra rama.
///////////
Pasos para agregar nuestro proyecto a un servidor remoto GITHUB
1)Nos posicionamos en la rama Master
git remote add origin (URL del repositorio en GITHUB Ejem: https://github.com/KAP2592/HiperBlog.git): Nos enlaza nuestro repositorio al servidor de github.
git remote -v: para ver toda la descripcion de nuestro origen.
git push origin master: para enviar nuestro proyecto a nuestro repositorio remoto github.
( si nos aparece un error de fusion) git pull origin master: para traer todo lo que esta en el repositorio remoto.
---------------------------------
CONECCION SSH 
Para configurar nuestro entorno y poder agregar una llava publica y privada a nuestro repositorio para hacerlo mas seguro tenemos que
saber que solamente es una por pc y no por repositorio, ademas de que se tiene que crear en local.
Primeramente tenemos que saber como esta configurado github

1)--> git config -l
2)Segundo tenemos que ingresar el comando para poder desplegar el algoritmo que nos genera git.
ssh-keygen -t rsa -b 4096 -C "kris.portillo25@gmail.com"  (damos enter)
3)nos pedira crear una clave: 
4)Despues de crearla nos vamos a la carpeta donde guardamos nuestra claves, vamos a copiar toda la llave publica 
para poderla agregar.
                                            //
                                            para hacerlo en MAC hacemos lo siguiente:
                                            revisar que el servidor de mack este encendido:
                                            eval $(ssh-agent -s)
                                            despues nos saldra esto:
                                            agen pid 4724
                                            --> despues agregar nuestra llave
                                            ///

<!-- EL SIGNO ~ ES UN CHORKUT QUE NOS AYUDA ACCEDER RAPIDAMENTE A CALQUIER CARPERA DENTRO DE NUESTRA PC CON BACH -->
Seguimos agregando la llave privada con el siguiente comando:
5)ssh-add ~/.ssh/id_rsa

una vez configurado tenemos que copiar la llave publica en github y despues cambiar el origen
para ver el origen: git remote -v
git remote set-url origin (pegamos la url de github ssh) y LISTO!!.

RECORDAR QUE ANTES DE HACER UN NUEVO COMMIT , NOS TENEMOS QUE TRAER LA ULTIMA VERSION DEL Master
////////////OTROS COMANDOS IMPORTANTES/////////////
git show-branch --all: Comando para poder visualizar todos los cambios que han realizado las ramas.
gitk: para poder visualizar un sw de historias.

---------------------------------------------------------------------------------------------------------------
PARA TRABAJAR CON OTRO REPOSITORIO 
git clone (pegamos la URL del repositorio de github): con eso nos descarga todo el proyecto del repositorio remoto.
Y realizamos todos los git que hemos visto hasta el momento.
Ahora bien tenemos que darle permiso para que pueda hacer un push a master.
--------------------------
PASOS PARA DARLE PERMISOS Y TRABAJAR EN COLABORATIVO:
1) Vamos a configuraciones de github
2)Nos vamos a colaboradores
3) agregamos por medio de correo o nombre de usuario de github
4) finalmente al colaborador le llegara un mensaje que tendra que aprobar.

////////////////RECORDAR/////////////////////////////////////////////////
git pull origin master: para descargar las ultimos cambios o modificaciones de nuestro repositorio principal
git push origin (Rama): para enviar nuestros cambios al repositorio principal.

git diff: para visualizar donde se realizaron los ultimos cambios dentro de nuestra rama.
-------------------------------------------------------------------------------------------

USO DEL FORK

Esta funcionalidad la encontramos en github y es cuando no somos colaboradoresde un proyecto pero queremos
hacer cambios en el y que estos los puedan aprobar.

Pasos:
1) nos vamos al repositorio en git, recordamos que tiene que ser publico si no no se puede.
2) damos en FORK
3)git clone (URL DEL REPOSITORIO github): clonamos el repositorio en nuestro pc.
4) hacemos los cambios.
5) guardamos y hacemos un git commit -m.
6)git push
7) despues no vamos a github y damos en new pull request
-------------------------------------------------------------------------------------------------------------
git ignore: lista de archivos que no queremos que se muestren en nuestro repositorio!.

###Images

Image:

![](https://pandao.github.io/editor.md/examples/images/4.jpg)