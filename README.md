![logo](https://user-images.githubusercontent.com/15006935/126084461-ae0c626d-66b4-4d08-b699-e6dd1c2ccd51.png)


# Como usar BAF.FI?

BAF.FI es un sistema de deteccion de copias en archivos de codigo fuente, que realiza comparaciones entre grupos de archivos y muestra informacion sobre las mismas.

Dentro del sistema hay 3 entidades principales:

- Tareas
- Entregas
- Comparaciones

## Tareas

Una tarea es una forma de agrupar archivos para crear comparaciones entre ellos de manera mas sencilla. Para crearla, se deben agrupar todos los archivos en un directorio y cargar el directorio al crear la tarea. La estructura de carpetas del directorio se utiliza de la siguiente manera:

- Todos los archivos que esten en cada subdirectorio directo del directorio principal no se compararan entre ellos. - Se compararan todos los archivos de cada subdirectorio con los de los demas subdirectorios, sin importar la estructura de carpetas dentro de los mismos.

- Se compararan todos los archivos de cada subdirectorio con los de los demas subdirectorios, sin importar la estructura de carpetas dentro de los mismos.

Por ejemplo, para la siguiente estructura:

```
📦Tarea
 ┣ 📂Entrega1
 ┃ ┗ 📜archivo1.py
 ┃ ┗ 📂Carpeta
 ┃   ┗ 📜archivo2.py
 ┣ 📂Entrega2
 ┃ ┗ 📂Carpeta
 ┃   ┗ 📜archivo3.py
 ┃   ┗ 📜archivo4.py
 ┣ 📂Entrega3
 ┃ ┗ 📜archivo5.py
 ┣ 📜 archivo6.py
```

Los grupos a comparar seran {archivo1.py, archivo.py} vs {archivo3,archivo4} vs {archivo5} vs {archivo6}. No se compararan los archivos `archivo1.py` y `archivo.py` ni `archivo3.py` y `archivo4.py`, y no se tomaran en cuenta las carpetas `Carpeta`.

## Entregas

Una entrega es una forma de agrupar archivos que son parte de una tarea cuando no se desea que se comparen entre ellos. Dentro de una tarea, todas las entregas seran comparadas entre si, pero los archivos pertenecientes a una misma entrega no seran comparados entre ellos.

## Comparaciones 

Hay 3 tipos de comparaciones posibles:

- A partir de una tarea
- Entre grupos de archivos que no pertenecen a una tarea
- A partir de un snippet de codigo

### A partir de una tarea

Se comparan todos los archivos incluidos dentro de las entregas que forman parte de la tarea como se explico anteriormente. 

### Entre grupos de archivos que no pertenecen a una tarea

Se comparan dos grupos de archivos (cada grupo puede tener entre cualquier cantidad de archivos). Los archivos pertenecientes a un mismo grupo no se comparan entre si.

### A partir de un snippet de codigo

Se puede comparar un snippet de codigo contra una tarea o contra un grupo de archivos. En cualquier caso, se comparara el snippet con todos los archivos pertenecientes a la tarea o al grupo. 

En todos los casos, al realizar una comparacion se puede ver una lista de las similaridades encontradas entre cada uno de los archivos comparados. No se mostraran resultados con un 0% de similaridad. Ademas, se puede ver un grafo donde cada nodo representa un archivo de la comparacion y la distancia entre ellos es inversamente proporcional a la similaridad encontrada. Seleccionando una arista del grafo se puede ver la comparacion que le dio origen.
