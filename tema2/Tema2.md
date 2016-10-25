#Ejercicios Tema 2

## Ejercicio 1.
### Instalar alguno de los entornos virtuales de node.js (o de cualquier otro lenguaje con el que se esté familiarizado) y, con ellos, instalar la última versión existente, la versión minor más actual de la 4.x y lo mismo para la 0.11 o alguna impar (de desarrollo).

Al estar realizando mi proyecto con Django, que emplea Python, voy a instarlar virtualenv, un entorno virtual para Python.

Para la instalación de virtualenv podemos usar el comando:
```
pip install virtualenv
```
![img](https://github.com/josejapch/ejerciciosIV/blob/master/tema2/imagenes/tema%202%20ej1%20a.png)

Si no se tiene instalado pip, podemos instalarlo con el comando (Ubuntu):
```
apt-get install python-pip
```
Una vez instalado creamos el directorio de trabajo. Desde este directorio de trabajo usamos el comando:
```
virtualenv directorioEntorno
```
"directorioEntorno" será el directorio donde tendremos los archivos ejecutables de Python y una copia de la biblioteca pip para poder instalar otros paquetes. Esto nos creará el entorno virtual con la versión por defecto de Python pero podemos crear un entorno virtual con una versión en concreto con el comando:
```
virtualenv -p direcciónInterprete directorioEntorno
```
![img](https://github.com/josejapch/ejerciciosIV/blob/master/tema2/imagenes/tema2%20ej1%20b.png)

## Ejercicio 2.
### Como ejercicio, algo ligeramente diferente: una web para calificar las empresas en las que hacen prácticas los alumnos. Si se quiere hacer con cualquier otra aplicación, también es válido. Se trata de hacer una aplicación simple que se pueda hacer rápidamente con un generador de aplicaciones como los que incluyen diferentes marcos MVC.
Como creo que el objetivo de los ejercicios es el realizar tareas que se vean reflejadas en la práctica, voy a usar como aplicación la desarrollada en el proyecto. [Proyecto](https://github.com/josejapch/proyectoIV1617)

## Ejercicio 3.
### Ejecutar el programa en diferentes versiones del lenguaje. ¿Funciona en todas ellas?
Al intentar ejecutar la aplicación en Python 3 (se emplea Python 2.7) obtenemos varios errores ya que hay diferencias en la sintaxis y algunas funciones, por lo que habría que alterar el código.

## Ejercicio 4.
### Crear una descripción del módulo usando package.json. En caso de que se trate de otro lenguaje, usar el método correspondiente.
Para la instalación de dependencias de una aplicación, en Django, se emplea un archivo de texto, normalmente llamado requirements.txt, en el que se incluye la herramienta necesaria y la versión.

![img](https://github.com/josejapch/ejerciciosIV/blob/master/tema2/imagenes/Tema2%20ej4%20A.png)

Si no sabemos la versión que estamos utilizando de cada herramienta podremos verla a través del terminal con el comando ```pip freeze```. Si estamos usando un entorno virtual exclusivamente para el desarrollo de la aplicación podríamos ejecutar el comando ```pip freeze > requirements.txt```, creándonos el archivo requirements.txt con las herramientas y su versión pero corremos el riesgo de incluir herramientas que se instalaron pero finalmente no se hayan usado haciendo que se instalen herramientas inútiles, por lo que el mejor procedimiento es escribirlo a mano asegurándonos de que lo que incluimos es imprescindible.

Además, tenemos la posibilidad de crear el archivo setup.py, que es un archivo de configuración para la instalación de paquetes en Python. A continuación podemos ver un ejemplo de cómo podría ser un setup.py para nuestra aplicación:

![img](https://github.com/josejapch/ejerciciosIV/blob/master/tema2/imagenes/Tema2%20ej4%20B.png)

## Ejercicio 5.
### Automatizar con grunt y docco (o algún otro sistema) la generación de documentación de la librería que se cree. Previamente, por supuesto, habrá que documentar tal librería.
Para documentar el código en Python podemos usar [Docstring](https://www.python.org/dev/peps/pep-0257/).

![img](https://github.com/josejapch/ejerciciosIV/blob/master/tema2/imagenes/Tema2%20ej5%20A.png)

Una vez tenemos el código documentado podemos automatizar la generación de la documentación con pydoc o con pycco. En este caso usaremos pycco.

Podemos instalar pycco con el comando:
```
pip install pycco
```
*Nota: Hacemos un inciso para comentar el problema de ```pip freeze > requirements.txt``` que comentábamos en el ejercicio anterior. Si tras instalar pycco ejecutamos ```pip freeze```, veremos que se ha añadido: Markdown, Pycco, Pygments, pystache, smartypants. Dichas herramientas son necesarias para que funcione pycco y elaborar la documentacion pero en ningún momento son necesarias para el funcionamiento de nuestra aplicación, por lo que en ningún momento hay que añadirlas a nuestro archivo requirements.txt*

Con el comando ```pycco queue/*.py -p``` generaremos la documentación de los archivos .py que se encuentren en el directorio queue.

![img](https://github.com/josejapch/ejerciciosIV/blob/master/tema2/imagenes/Tema2%20ej5%20B.png)

## Ejercicio 6.
### Para la aplicación que se está haciendo, escribir una serie de aserciones y probar que efectivamente no fallan. Añadir tests para una nueva funcionalidad, probar que falla y escribir el código para que no lo haga (vamos, lo que viene siendo TDD).
Para realizar los test en Python utilizamos [unitest](https://docs.python.org/2/library/unittest.html), un módulo para construir, ejecutar y automatizar test. A continuación podemos ver un par de ejemplos en los que se comprueba que se insertan correctamente elementos en los modelos "Cola" y "Encolado".

![img](https://github.com/josejapch/ejerciciosIV/blob/master/tema2/imagenes/Tema2%20ej6%20A.png)

![img](https://github.com/josejapch/ejerciciosIV/blob/master/tema2/imagenes/Tema2%20ej6%20B.png)

Podemos comprobar que los test se ejecutan con éxito.

## Ejercicio 7.
### Convertir los tests unitarios anteriores con assert a programas de test y ejecutarlos desde mocha, usando descripciones del test y del grupo de test de forma correcta. Si hasta ahora no has subido el código que has venido realizando a GitHub, es el momento de hacerlo, porque lo vas a necesitar un poco más adelante.
En nuestro caso no tenemos que utilizar Mocha. Los programas de test pueden encontrarse en [queue/tests.py](https://github.com/josejapch/proyectoIV1617/blob/master/queue/tests.py) y para ejecutar todos los test podemos emplear el comando: 
```
python manage.py test
```
![img](https://github.com/josejapch/ejerciciosIV/blob/master/tema2/imagenes/Tema2%20ej7%20A.png)

## Ejercicio 8.
### Haced los dos primeros pasos antes de pasar al tercero.
Se puede consultar los pasos para la configuración de Travis CI en la [documentación extra](https://github.com/josejapch/documentacion-Proyecto-IV/blob/master/hito2.md) del hito2.