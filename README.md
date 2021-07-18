![logo](https://user-images.githubusercontent.com/15006935/126084461-ae0c626d-66b4-4d08-b699-e6dd1c2ccd51.png)


# ¿Qué es BAF.FI?

BAF.FI es un sistema de detección de plagio en archivos de código fuente, realiza comparaciones entre grupos de archivos y muestra informacion sobre las mismas.

Dentro de BAFFI encontramos 3 entidades principales:

- Tareas
- Entregas
- Comparaciones

## Tareas

Una tarea es una forma de agrupar archivos para crear comparaciones entre ellos de manera mas sencilla. Para crearla, se deben agrupar todos los archivos en un directorio y cargar el directorio al crear la tarea. La estructura de carpetas del directorio se utiliza de la siguiente manera:

- Todos los archivos que esten en cada subdirectorio directo del directorio principal no se compararan entre ellos
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

Los grupos a comparar serán {archivo1.py, archivo2.py} vs {archivo3.py, archivo4.py} vs {archivo5.py} vs {archivo6.py}. No se compararán entre sí los archivos `archivo1.py` y `archivo.py` ni `archivo3.py` y `archivo4.py`, y no se tomaran en cuenta las carpetas `Carpeta`.

## Entregas

Una entrega es una forma de agrupar archivos que son parte de una tarea cuando no se desea que se comparen entre ellos. Dentro de una tarea, todas las entregas seran comparadas entre sí, pero los archivos pertenecientes a una misma entrega no seran comparados entre ellos.

## Comparaciones 

Se pueden generar comparaciones de diferentes formas:

- A partir de una tarea
- A partir de grupos de archivos que no pertenecen a una tarea
- A partir de un snippet de codigo

### A partir de una tarea

Se comparan todos los archivos incluidos dentro de las entregas que forman parte de la tarea como se explicó anteriormente.

### A partir de grupos de archivos que no pertenecen a una tarea

Se comparan dos grupos de archivos (cada grupo puede tener entre cualquier cantidad de archivos). Los archivos pertenecientes a un mismo grupo no se comparan entre si.

### A partir de un snippet (bloque) de código

Se puede comparar un snippet de codigo contra una tarea o contra un grupo de archivos. En cualquier caso, se comparara el snippet con todos los archivos pertenecientes a la tarea o al grupo.

En todos los casos, al realizar una comparacion se puede ver una lista de las similaridades encontradas entre cada uno de los archivos comparados. No se mostrarán resultados con un 0% de similaridad. Además, se genera un grafo donde cada nodo representa un archivo de la comparacion y la distancia entre ellos es inversamente proporcional a la similaridad encontrada. Seleccionando una arista del grafo se puede ver la comparación que le dió origen.

----------

# FAQ

## 💾 Si cierro BAFFI pierdo todas mis tareas y comparaciones?
Los usuarios de BAFFI pueden usar nuestra herramienta de dos formas:
- Como invitado: Las tareas y comparaciones creadas son efímeras y durarán hasta que se venza la sesión
- Ingresando con Google (sólo cuentas `@fi.uba.ar`): Las tareas y comparaciones quedan guardadas bajo tu nombre y siempre disponibles para que las vuelvas a consultar.

## 🔗 Si necesito compartir una comparación con otra persona como puedo hacer?
En el caso de querer compartir una comparación solamente se necesita pasar la URL de la página de la misma a la persona que queremos mostrarles los resultados de una comparación en particular.

## 💻 En que lenguajes de programación puedo detectar plagios con BAFFI?
En la primer versión de BAFFI solamente se pueden detectar plagios entre archivos Python (.py) o C (.c)

## 🕵️ Si una comparación detecta similaridades entre dos archivos de alumnos, quiere decir que se copiaron?
BAFFI no es prueba de que exista plagio, es una herramienta de apoyo para el docente y siempre se debe confiar en su cirterio para tomar cualquier decisión.

## ⛔ Estoy teniendo problemas al logearme, que puede ser?
En algunos casos Heroku cancela algunos request dado que no estamos en la versión paga, por lo que si se observan algunos problemas por favor intente nuevamente. Próximamente planeamos deployar una instancia de BAFFI en Google Cloud para evitar este tipo de inconvenientes.

## 🔃 Esta es la versión final de BAFFI?
BAFFI se encuentra en sus etapas finales de desarrollo, por lo que algunas features, experiencias o la infraestructura donde se encuentra alojado pueden cambiar.
