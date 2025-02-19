[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/KjkUBfOZ)
[![Open in Visual Studio Code](https://classroom.github.com/assets/open-in-vscode-c66648af7eb3fe8bc4f294546bfd86ef473780cde1dea487d3c4ff354943c9ae.svg)](https://classroom.github.com/online_ide?assignment_repo_id=9883733&assignment_repo_type=AssignmentRepo)
# Fundamentos de Github

Archivo de práctica, en este proyecto de GIT se practicarán conceptos relacionados con: 

* Manipular los archivos de un repositorio local mediante los comandos básicos: add, commit, status, log
* Entender qué es un repositorio remoto.
* Clonar un repositorio remoto.
* Manipular los archivos de un repositorio local y sincronizar los cambios en el repositorio remoto mediante los comandos básicos: push y pull.
* Comprender cuándo se genera un conflicto y cómo solucionarlo.


## Familiarizacion con repositorios remotos  y locales
*	Clone el repositorio. Llamaremos en adelante a este repositorio repositorio(1)
* Observe la carpeta oculta .git creada dentro del disco duro
*	Cree un archivo de texto en markdown(.md) dentro del repositorio. Este archivo debe tener su nombre en formato nombre_apellido. Ejm PEDRO_PEREZ.md
*	Agregue el archivo al repositorio local
*	Agregue el archivo un nuevo texto que diga "Oh Gloria inmarcesible, oh júbilo inmortal"
*	Agregue el archivo al stagging area  ``git add ruta del archivo``
*	Haga commit al archivo. Recuerde poner un comentario en el archivo.   ``git commit -m "su mensaje" ``
*	Haga push al repositorio remoto para subir los cambios hechos al repositorio ``git push origin main``

## Conflictos
### En el mismo archivo
#### Modificar el archivo
* Clone el repositorio remoto en un **directorio diferente** al que usó en la parte de familiarización (Repositorio 1)
* En el segundo repositorio modifique la primera línea del primer archivo.md que creo con el formato *nombre_apellido.md*. Quite lo que estaba y en su lugar escriba "En un lugar de la mancha de cuyo nombre no quiero acordarme"
* Guarde el archivo
* Agregue el archivo al stagging area:  ``git add ruta del archivo``
* Haga commit del archivo en el repositorio local: ``git commit -m "su mensaje" ``
* Haga push al repositorio remoto: ``git push origin main``
 
#### Crear conflicto en el mismo archivo
* Vuelva a la carpeta del primer repositorio que clonó. (Repositorio 1)
* Abra el archivo que creó con el formato *nombre_apellido.md*.
* Agregue al texto que ya tiene lo siguiente: "En surcos de dolores el bien germina ya".( Note que en esta copia del repositorio todavía no se ve reflejado los cambios que hizo en el repositorio(1) en el paso anterior, por lo que todavía tiene una parte del himno nacional)
* Guarde el archivo
* Agregue el archivo al stagging area:  ``git add ruta del archivo``
* Haga commit del archivo en el repositorio local: ``git commit -m "su mensaje" ``
* Intente hacer push al repositorio remoto: ``git push origin main``. Debe aparecerle un error similar a este ``! [rejected] master -> master (fetch first)``. Esto significa que Git rechazó el push al repositorio remoto porque el mismo archivo fue modificado desde repositorios diferentes. La última versión del repositorio remoto no coincide con la versión del repositorio local que esta intentado hacer el push

#### Resolver conflicto cuando un mismo archivo tiene diferente información
Este es un conflicto que NO puede ser resuelto automáticamente por GIT. Este tipo de conficto ocurre cuando se ha modificado las mismas líneas de un archivo en dos repositorios diferentes y por lo tanto la copia remota y la copia local no coinciden.  Para solucionar este caso es necesario: 
* Hacer pull al repositorio
* Abrir con el editor preferido los archivos que tienen conflicto y editarlos *manualmente*. Las líneas de código que están después de la etiqueta HEAD corresponden a lo que está en el repositorio local y lo que está después de ===== corresponde a lo que está en el repositorio remoto. Quien corrije el error decide cuál de las dos versiones permanece en el archivo. En todo caso recuerde eliminar las etiquetas <<<<<<< HEAD, ======= y >>>>>>>.
* Haga que en la primera línea quede el siguiente texto: *"Oh Gloria inmarcesible, oh júbilo inmortal. En surcos de dolores el bien germina ya. En un lugar de la mancha de cuyo nombre no quiero acordarme"*
* Una vez terminado el ajuste:
    * Agregué el archivo al repositorio remoto  ``git add ruta``
    * Haga commit del archivo ``git commit -m "su mensaje" ``
    * Haga push al repositorio remoto ``git push origin main``
    * Sus cambios debieron de subir correctamente al repositorio remoto. Verifique en la página de Github que el archivo subido tenga la versión ajustada. 

 ### Conflictos en archivos diferentes
Esos son conflictos que **no** modifican las mismas partes de un archivo o que modifican archivos diferentes.  En ese caso solo deberá escribir ``git pull origin``. El comando descargará los nuevos archivos y hará un merge automáticamente con sus archivos locales. }

Este tipo de error es **muy común** cuando se trabaja en equipo, por esa razón antes de subir cambios use siempre el comando  ``git pull origin`` para bajar la última versión del repositorio. 

* Vaya al repositorio 2
*	Cree un segundo archivo. Este archivo debe tener su nombre en formato apellido_nombre_2. Ejm PEREZ_PEDRO_2.md
*	Agregue el archivo al stagging área 
*	Haga commit al archivo
*	Intente hacer push al repositorio remoto: ``git push origin main``. Debe aparecer un error que indica que hay conflictos entre tu versión local y la versión remota del repositorio.  Este conflicto se puede resolver automáticamente. Para hacerlo haga pull del repositorio para actualizar la última versión ``git pull origin``. Agregué nuevamente el archivo al stagging area, haga nuevamente commit del archivo e intente hacer nuevamente push. Esta vez su push debe ser exitoso. 
