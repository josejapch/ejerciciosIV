﻿#Ejercicios Tema 3

## Ejercicio 1.
### Darse de alta en algún servicio PaaS tal como Heroku, Nodejitsu, BlueMix u OpenShift.
En este caso me he dado de alta en Heroku ya que es el que voy a emplear para el despliegue de la aplicación.

![imagen](https://github.com/josejapch/ejerciciosIV/blob/master/tema3/imagenes/ej1%20alta%20heroku.png)

Como no documenté el proceso de alta, incluyo también el alta en OpenShift.

- Al entrar en la página oficial de [OpenShift](https://www.openshift.com/) pulsamos sobre la opción "Sign up for free" y nos dará la posibilidad de registrarnos mediante nuestra cuenta de GitHub.

![imagen](https://github.com/josejapch/ejerciciosIV/blob/master/tema3/imagenes/ej1%20pagina%20registro%20openshift.png)

- Tendremos que autorizar el acceso de OpenShift a nuestra cuenta de GitHub y tomará nuestros datos. Con estos datos nos damos de alta y nos colocará en lista de espera notificándonos, además, de que tenemos una cuenta limitada al ser una "Developer preview".

![imagen](https://github.com/josejapch/ejerciciosIV/blob/master/tema3/imagenes/ej1%20notificacion%20de%20alta%20openshift.png)

## Ejercicio 2.
### Crear una aplicación en OpenShift o en algún otro PaaS en el que se haya dado uno de alta. Realizar un despliegue de prueba usando alguno de los ejemplos.
Creación de una aplicación en Heroku a través de la interfaz web. La creación, instalación de la aplicación y despliegue en Heroku a través de la linea de comandos podremos verlo en el ejercicio 5.

- Una vez nos logueamos en Heroku, nos llevará al "Dashboard".

    ![imagen](https://github.com/josejapch/ejerciciosIV/blob/master/tema3/imagenes/ej2%20dashboard%20heroku.png)

    En este caso nos encontramos la aplicación que ya tenemos desplegada (aplicación de la práctica) pero si nos acabamos de dar de alta, no aparecerá ninguna. Para crear una nueva aplicación pulsaremos sobre el botón "New".
    
- Nos llevará a un formulario en el que tendremos que indicar el nombre de nuestra aplicación y la región a la que pertenece.

    ![imagen](https://github.com/josejapch/ejerciciosIV/blob/master/tema3/imagenes/ej2%20creacion%20de%20aplicacion.png)
    
- Una vez creamos la aplicación podremos verla en nuestro "Dashboard" y verla desplegada en el navegador.

    ![imagen](https://github.com/josejapch/ejerciciosIV/blob/master/tema3/imagenes/ej2%20dashboard%20con%20aplicacion%20creada.png)
    
    ![imagen](https://github.com/josejapch/ejerciciosIV/blob/master/tema3/imagenes/ej2%20aplicacion%20desplegada%20en%20heroku.png)

Creación de una aplicación en OpenShift a través de la interfaz web.

- Una vez nos logueamos en OpenShift pulsamos sobre "New Project".

    ![imagen](https://github.com/josejapch/ejerciciosIV/blob/master/tema3/imagenes/ej2%20openshift%20dashboard.png)
    
- Nos llevará a un formulario en el que tendremos que indicar el nombre de nuestra aplicación y descripción.

    ![imagen](https://github.com/josejapch/ejerciciosIV/blob/master/tema3/imagenes/ej2%20openshift%20formulario%20de%20creacion.png)
    
- A continuación podremos elegir el lenguaje del proyecto o elegir una imagen de despliegue o incluir un JSON/YAML que indique los requisitos.
- Tras elegir el lenguaje, debemos indicar el nombre de la construcción y el repositorio que queremos desplegar.

    ![imagen](https://github.com/josejapch/ejerciciosIV/blob/master/tema3/imagenes/ej2%20openshift%20formulario%20git.png)
    
    ![imagen](https://github.com/josejapch/ejerciciosIV/blob/master/tema3/imagenes/despliegue%20de%20aplicacion%20en%20openshift.png)
    
## Ejercicio 3.
### Realizar una app en express (o el lenguaje y marco elegido) que incluya variables como en el caso anterior.
Para incluir servicio REST a nuestra aplicación emplearemos [Django REST framework](http://www.django-rest-framework.org/) y seguiremos la documentación disponible en su página.
- Instalamos Django REST framework con el comando:

    ```pip install djangorestframework```
- Añadimos la nueva dependencia a [requirements.txt](https://github.com/josejapch/proyectoIV1617/blob/master/requirements.txt)
- Añadimos en nuestro archivo [settings.py](https://github.com/josejapch/proyectoIV1617/blob/master/queueme/settings.py) la nueva aplicación instalada (INSTALLED_APPS).
- Creamos un archivo [serializers.py](https://github.com/josejapch/proyectoIV1617/blob/master/queue/serializers.py) que contendrá las clases serializadas, en este caso serán las colas de la aplicación.
- Probamos la clase de serialización accediendo a la consola de Django con el comando:

    ```python manage.py shell```
    
    ![imagen](https://github.com/josejapch/ejerciciosIV/blob/master/tema3/imagenes/ej3%20prueba1.png)
    
    En la imagen superior hemos creado una cola nueva y la hemos pasado por la serialización. En la siguiente imagen se muestran los datos de la cola en formato JSON.
    
    ![imagen](https://github.com/josejapch/ejerciciosIV/blob/master/tema3/imagenes/ej3%20prueba%20json.png)
    
    Se ha añadido una vista para que, a través de un formulario se busque una cola. Si existe, se devuelve la información en formato JSON; si no, se vuelve a la página con el formulario con un mensaje de error.
    
    ![imagen](https://github.com/josejapch/ejerciciosIV/blob/master/tema3/imagenes/ej3%20consultaJSON%20(exito).png)
    
    ![imagen](https://github.com/josejapch/ejerciciosIV/blob/master/tema3/imagenes/ej3%20consultaJSON%20(fracaso).png)

## Ejercicio 4.
### Crear pruebas para las diferentes rutas de la aplicación.
Para realizar los test, se ha modificado el archivo [test.py](https://github.com/josejapch/proyectoIV1617/blob/master/queue/tests.py) incluyendo una nueva clase "TestJson". En ella incluimos una función que comprueba que se devuelve un JSON al hacer una consulta correcta en el formulario comentado en el ejercicio 3.

![imagen](https://github.com/josejapch/ejerciciosIV/blob/master/tema3/imagenes/ej4%20prueba%20json.png)

Además, en la clase "TestViews", hemos añadido test para asegurarnos de que una consulta GET a "consultar_colaJSON" obtiene una respuesta 200 (correcta) y que obtiene la misma respuesta el formulario ante una petición POST en la que se introduce un código de cola incorrecto.

![imagen](https://github.com/josejapch/ejerciciosIV/blob/master/tema3/imagenes/ej4%20json%20respuesta%20200.png)

Resultado de los test:

![imagen](https://github.com/josejapch/ejerciciosIV/blob/master/tema3/imagenes/ej4%20resultado%20test.png)

## Ejercicio 5.
### Instalar y echar a andar tu primera aplicación en Heroku.
La instalación de la aplicación en Heroku se encuentra en la [documentación de la práctica 3](https://github.com/josejapch/documentacion-Proyecto-IV/blob/master/hito3.md).

Despliegue de la aplicación:
[![Heroku](http://i66.tinypic.com/2d2ja74.jpg)](https://queueme.herokuapp.com/)

## Ejercicio 6.
### Usar como base la aplicación de ejemplo de heroku y combinarla con la aplicación en node que se ha creado anteriormente. Probarla de forma local con foreman. Al final de cada modificación, los tests tendrán que funcionar correctamente; cuando se pasen los tests, se puede volver a desplegar en heroku.


## Ejercicio 7.
### Haz alguna modificación a tu aplicación en node.js para Heroku, sin olvidar añadir los tests para la nueva funcionalidad, y configura el despliegue automático a Heroku usando Snap CI o alguno de los otros servicios, como Codeship, mencionados en StackOverflow.
En el proyecto he automatizado el despliegue con las opciones que ofrece Heroku esperando a que se pasen los test en TravisCI tras realizar un "push" en GitHub. Puede verse cómo se ha hecho en [Informacion extra: Configuración Travis CI](https://github.com/josejapch/documentacion-Proyecto-IV/blob/master/hito2.md) e [Informacion extra: Despliegue y automatización en Heroku](https://github.com/josejapch/documentacion-Proyecto-IV/blob/master/hito3.md), punto 3.

Procedemos a explicar cómo hacer con Snap CI:

- Para integrar Snap CI en nuestro proyecto nos dirigimos a las opciones del proyecto y, en "Integrations & services", añadimos el servicio Snap CI.

    ![imagen](https://github.com/josejapch/ejerciciosIV/blob/master/tema3/imagenes/ej7%20elegir%20snapCI%20github.png)
    
- Nos indica que tenemos que darnos de alta en Snap CI con nuestra cuenta de GitHub y añadir el repositorio. Lo hacemos y podremos editar los pasos que se van a seguir para la integración contínua.

- Podemos indicar los pasos a seguir mediante una especie de "cajas" donde incluimos los comandos que se van a ir ejecutando.

    ![imagen](https://github.com/josejapch/ejerciciosIV/blob/master/tema3/imagenes/ej7%20cajas%20snapci.png)
    
- En la imagen anterior podemos ver como se han añadido 2 "cajas". Una se encarga de instalar los requisitos de la aplicación y la otra ejecutará los test mediante el makefile que se ha incluido en el proyecto (también se podría haber usado el comando ```python manage.py test```).

    ![imagen](https://github.com/josejapch/ejerciciosIV/blob/master/tema3/imagenes/ej7%20caja%20requisistos.png)
    
    ![imagen](https://github.com/josejapch/ejerciciosIV/blob/master/tema3/imagenes/ej7%20caja%20test.png)
    
- Guardamos la configuración y ejecutará las "cajas" indicándonos si ha fallado algo.

    ![imagen](https://github.com/josejapch/ejerciciosIV/blob/master/tema3/imagenes/ej7%20cajas%20superadas.png)
    
- Ya tan solo quedaría indicar, en Heroku, que se realice el despliegue tras realizar la integración contínua tal y como hemos indicado en la documentación extra del hito 3.

*NOTA: En el proyecto se ha conservado la configuración con Travis CI.*


## Ejercicio 8.
### Preparar la aplicación con la que se ha venido trabajando hasta este momento para ejecutarse en un PaaS, el que se haya elegido.
[![Heroku](http://i66.tinypic.com/2d2ja74.jpg)](https://queueme.herokuapp.com/)
