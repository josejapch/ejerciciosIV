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

A la izquierda podemos ver la configuración de "una-caja" cuando fué creada y a la derecha la configuración modificada con un límite de memoria de 1024 MB y una CPU.

## Ejercicio 6.
### Instalar docker.

