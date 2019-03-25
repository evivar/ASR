# Monitorizacion de directorios y modificaciones en los archivos del directorio
## Grupo: Cable USB 2.0

### Explicación del problema:
	Como administradores de sistemas podemos tener directorios y ficheros sensibles a modificaciones por parte de otros usuarios. Por tanto queremos poder tener un registro de cúando se han realizado las modificaciones 


### Explicación teórica de la solución:
	Para resolver el problema enunciado anteriormente. primero, el administrador del sistema debeŕá instalar la herramienta de software libre iNotify-tools, con el siguiente comando:
		- dnf install inotify-tools
	Seguidamente el administrador del sistema ejecutará el archivo:
		- scriptfichero.sh
	Con este script se empezará a ejecutar en segundo plano la monitorización de los directorios y archivos especificados.


### Explicación del código:
	El código estaá dividido en dos ficheros distintos:
		- scriptfichero.sh: Este fichero ejecuta el archivo script.sh en segundo plano sin que se bloquee la consola del usuario por 					 el comando inotifywait. Para hacer que el script.sh se ejecute en segundo plano hemos optado por utilizar 						el comando nohup.

		- script.sh: Este fichero contiene toda el código de monitorización y el formateo de la salida, así como la ruta de los 				 directorios a monitorizar. Si queremos cambiar el directorio a monitorizar habria que modificar la segunda linea 			   de este fichero intercambiando la ruta de '/media' por la ruta deseada.
					 La salida generada por este script tiene el siguiente formato, y se guardará en la ruta /var/log/log-media.log
					 	- Tres guiones, ---
					 	- Cambios en el directorio monitorizado
					 	- En el fichero modificado
					 	- En el dia en que se produjo la modificación

### Referencias:
	- [Wiki del proyecto iNotify-tools](https://github.com/rvoicilas/inotify-tools/wiki)
	- [Manual del comando inotifywait](https://linux.die.net/man/1/inotifywait)
	- [Manual del comando nohup](https://linux.die.net/man/1/nohup)