#Ejercicios Tema 4

## Ejercicio 1.
### Instala LXC en tu versión de Linux favorita. Normalmente la versión en desarrollo, disponible tanto en GitHub como en el sitio web está bastante más avanzada; para evitar problemas sobre todo con las herramientas que vamos a ver más adelante, conviene que te instales la última versión y si es posible una igual o mayor a la 1.0.

Para la instalación en Ubuntu podemos usar el comando: ```apt-get install lxc```

Con el comando ```lxc-ls --version``` podemos ver la versión instalada y con el comando ```lxc-checkconfig``` comprobamos que el núcleo del SO está preparado para usar lxc.

![imagen](https://github.com/josejapch/ejerciciosIV/blob/master/tema4/imagenes/tema4%20ej1.png)

## Ejercicio 2.
### Comprobar qué interfaces puente se han creado y explicarlos.

Si ejecutamos el comando ```ifconfig``` podemos ver "lcbr0" y "veth38L23G".

![imagen](https://github.com/josejapch/ejerciciosIV/blob/master/tema4/imagenes/Tema4%20ej2.1.png)

Según he podido entender por la [wiki](https://wiki.debian.org/LXC/SimpleBridge) de debian y la páguina de [ayuda](https://help.ubuntu.com/lts/serverguide/lxc.html) de ubuntu, "lcbr0" se trata del puente (NAT) que suministra la conexión a internet al contenedor a través de la máquina anfitriona y "veth38L23G" sería una interfaz virtual ethernet.

## Ejercicio 3.
### 1. Crear y ejecutar un contenedor basado en Debian.

- Para crear un contenedor usamos el comando ```sudo lxc-create -t ubuntu -n una-caja``` siendo "una-caja" el nombre del contenedor y "ubuntu" el SO que queremos que tenga el contenedor.

- Ponemos en marcha el contenedor con el comando ```lxc-start -n una-caja```.

![imagen](https://github.com/josejapch/ejerciciosIV/blob/master/tema4/imagenes/Tema4%20ej3.1.png)

### 2. Crear y ejecutar un contenedor basado en otra distribución, tal como Fedora. Nota En general, crear un contenedor basado en tu distribución y otro basado en otra que no sea la tuya. Fedora, al parecer, tiene problemas si estás en Ubuntu 13.04 o superior, así que en tal caso usa cualquier otra distro.

Podemos ver los templates disponibles usando el comando ```sudo ls /usr/share/lxc/templates/```

![imagen](https://github.com/josejapch/ejerciciosIV/blob/master/tema4/imagenes/Tema4%20ej3.2.png)

En este caso instalaremos CentOS.

- Primero instalaremos "yum" con el comando: ```apt-get install yum```.
- Una vez instalado, crearemos el contenedor con el comando: ```sudo lxc-create -t centos -n una-caja-centos```
- Al terminar la instalación se nos comunicará que la contraseña de root es temporal y debemos cambiarla.

    ![imagen](https://github.com/josejapch/ejerciciosIV/blob/master/tema4/imagenes/Tema4%20ej3.3.png)
    
- Ponemos en marcha el contenedor con el comando ```lxc-start -n una-caja-centos```.

    ![imagen](https://github.com/josejapch/ejerciciosIV/blob/master/tema4/imagenes/Tema4%20ej3.4.png)
    
## Ejercicio 4.
### 1. Instalar lxc-webpanel y usarlo para arrancar, parar y visualizar las máquinas virtuales que se tengan instaladas.

- Para instalarlo seguimos las [instrucciones](http://lxc-webpanel.github.io/install.html) de la [página oficial](http://lxc-webpanel.github.io/) y ejecutamos el comando ```wget https://lxc-webpanel.github.io/tools/install.sh -O - | bash``` como usuario root.

- Una vez instalado se nos indicará cómo podemos acceder a lxc-webpanel.

    ![imagen](https://github.com/josejapch/ejerciciosIV/blob/master/tema4/imagenes/Tema4%20ej4.1.png)
    
    ![imagen](https://github.com/josejapch/ejerciciosIV/blob/master/tema4/imagenes/Tema4%20ej4.2.png)
    
- Si seleccionamos uno de los contenedores se nos mostrará un menú con la opción de iniciar, pausar y parar el contendor.

    ![imagen](https://github.com/josejapch/ejerciciosIV/blob/master/tema4/imagenes/Tema4%20ej4.4.png)
    
    ![imagen](https://github.com/josejapch/ejerciciosIV/blob/master/tema4/imagenes/Tema4%20ej4.5.png)
    
    ![imagen](https://github.com/josejapch/ejerciciosIV/blob/master/tema4/imagenes/Tema4%20ej4.3.png)
    
### 2. Desde el panel restringir los recursos que pueden usar: CPU shares, CPUs que se pueden usar (en sistemas multinúcleo) o cantidad de memoria.

![imagen](https://github.com/josejapch/ejerciciosIV/blob/master/tema4/imagenes/Tema4%20ej4.6.png) ![imagen](https://github.com/josejapch/ejerciciosIV/blob/master/tema4/imagenes/Tema4%20ej4.7.png)

En la primera imagen podemos ver la configuración de "una-caja" cuando fué creada y en la segunda la configuración modificada con un límite de memoria de 1024 MB y una CPU.

## Ejercicio 6.
### Instalar docker.

Explicado en la documentación extra del hito 4: [Creación de un entorno de pruebas para la aplicación usando contenedores: 1. Instalación de Docker.](https://github.com/josejapch/documentacion-Proyecto-IV/blob/master/hito4.md)

## Ejercicio 7.
### 1. Instalar a partir de docker una imagen alternativa de Ubuntu y alguna adicional, por ejemplo de CentOS.

Para crear la imagen de Ubuntu podemos usar el comando: ```docker pull ubuntu```

Para crear la imagen de CentOS podemos usar el comando: ```docker pull centos```

### 2. Buscar e instalar una imagen que incluya MongoDB.

Podemos usar el comando: ```docker pull mongo```

Podemos ver las imágenes instaladas a partir de docker con el comando: ```docker images```

![imagen](https://github.com/josejapch/ejerciciosIV/blob/master/tema4/imagenes/Tema4%20ej7.1.png)

Información sobre cómo instalar las imágenes se puede obtener del repositorio de dockerHub: [CentOS](https://hub.docker.com/_/centos/), [Ubuntu](https://hub.docker.com/_/ubuntu/), [Mongo](https://hub.docker.com/_/mongo/).

## Ejercicio 8.
### Crear un usuario propio e instalar nginx en el contenedor creado de esta forma.

- Para crear el usuario vamos a arrancar la máquina Ubuntu (podría realicarse sin conectarnos son el comando ```docker run <id de la máquina> <comando>```). Para esto usaremos el comando: ```docker run -i -t ubuntu /bin/bash```. Para crear el usuario emplearemos el comando ```adduser```.

![imagen](https://github.com/josejapch/ejerciciosIV/blob/master/tema4/imagenes/Tema4%20ej8.1.png)

- Actualizamos el repositorio con ```apt-get update``` e instalamos nginx con el comando: ```apt-get install nginx```

- Iniciamos el servicio con el comando: ```service nginx start```.

Si queremos comprobar si realmente está funcionando, podemos instalar curl con el comando: ```apt-get install curl```.

![imagen](https://github.com/josejapch/ejerciciosIV/blob/master/tema4/imagenes/Tema4%20ej8.2.png)

## Ejercicio 9.
### Crear a partir del contenedor anterior una imagen persistente con commit.

Para hacer la imagen del contenedor anterior podemos ver, con el comando ´´´ docker ps -a ```  las ejecuciones de las máquinas.

![imagen](https://github.com/josejapch/ejerciciosIV/blob/master/tema4/imagenes/Tema4%20imagen%209.1.png)

En este caso queremos hacer el commit sobre el contenedor de ID: 51bd498824ea (el correspondiente con el ejercicio anterior).

Hacemos un commit, en este caso: ```docker commit 51bd498824ea ubuntu4-e8```

![imagen](https://github.com/josejapch/ejerciciosIV/blob/master/tema4/imagenes/Tema4%20ej9.2.png)

Podemos ver cómo se ha creado una imagen con el nuevo nombre. Si ahora ponemos en marcha el nuevo contenedor, podemos iniciar el servicio de nginx ya que se encuentra instalado.

![imagen](https://github.com/josejapch/ejerciciosIV/blob/master/tema4/imagenes/tema4%20ej9.3.png)

## Ejercicio 10.
### Crear una imagen con las herramientas necesarias para el proyecto de la asignatura sobre un sistema operativo de tu elección.

Todo el proceso se encuentra documentado en la [documentación extra del hito4](https://github.com/josejapch/documentacion-Proyecto-IV/blob/master/hito4.md).
