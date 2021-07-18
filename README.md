# Como usar BAF.FI?

BAF.FI es un sistema de deteccion de copias en archivos de codigo fuente, que realiza comparaciones entre grupos de archivos y muestra informacion sobre las mismas.

## Tareas

Una tarea es simplemente una forma de agrupar archivos para crear comparaciones entre ellos de manera mas sencilla. Para crearla, se deben agrupar todos los archivos en un directorio y cargar el directorio al crear la tarea. La estructura de carpetas del directorio se utiliza de la siguiente manera:

- Todos los archivos que esten en cada subdirectorio directo del directorio principal no se compararan entre ellos.

- Se compararan todos los archivos de cada subdirectorio con los de los demas subdirectorios, sin importar la estructura de carpetas dentro de los mismos.
