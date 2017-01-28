#Ejercicios Tema 5

## Ejercicio 1.
### Instalar los paquetes necesarios para usar KVM. Se pueden seguir estas instrucciones. Ya lo hicimos en el primer tema, pero volver a comprobar si nuestro sistema está preparado para ejecutarlo o hay que conformarse con la paravirtualización.

Consultamos los flags del procesador con el comando: ```egrep '^flags.*(vmx|svm)' /proc/cpuinfo```

Podemos ver que en cada núcleo del procesador tenemos el flag vmx.

![](INSERTAR IMAGEN 5.1)

Para la instalación de KVM, se han seguido los pasos de la [documentación](https://help.ubuntu.com/community/KVM/Installation) y la [wiki](https://wiki.debian.org/KVM#Installation) de Debian:

- Instalamos con el comando: ```apt-get install qemu-kvm libvirt-bin ubuntu-vm-builder bridge-utils```

- Instalamos ```virtinst``` para trabajar con líneas de comandos o ```virt-manager``` para emplear una interfaz gráfica: ```apt-get install virtinst``` o ```apt-get install virt-manager```

   ![](INSERTAR IMAGEN 5.3)

- Añadimos nuestro usuario a los grupos "kvm" y "libvirtd".

- Verificamos la instalación con el comando: ```virsh list --all```

   ![](INSERTAR IMAGEN 5.2)
    
## Ejercicio 2.
### Crear varias máquinas virtuales con algún sistema operativo libre tal como Linux o BSD. Si se quieren distribuciones que ocupen poco espacio con el objetivo principalmente de hacer pruebas se puede usar CoreOS (que sirve como soporte para Docker) GALPon Minino, hecha en Galicia para el mundo, Damn Small Linux, SliTaz (que cabe en 35 megas) y ttylinux (basado en línea de órdenes solo).

- En este caso instalaremos "Slitaz4" y "Damn Small Linux 4".

- Primero creamos los discos duros para instalar los sistemas operativos:

```qemu-img create -f qcow2 slitaz4.qcow2 1G```

```qemu-img create -f qcow2 dsl4.qcow2 1G```

- Cargamos el módulo KVM con el comando: ```modprobe kvm-intel```

- Instalaremos los SO en los respectivos discos:

```qemu-system-x86_64 -hda slitaz4.qcow2 -cdrom ~/Descargas/slitaz-4.0.iso```

   ![](INSERTAR IMAGEN 5.4)
    
```qemu-system-x86_64 -hda dsl4.qcow2 -cdrom ~/Descargas/dsl-4.4.10.iso```

   ![](INSERTAR IMAGEN 5.5)
   
NOTA: Tendremos que elegir la opción correcta en el menú de inicio (por ejemplo F3 en DSLinux) para que se instale y no se inicie como un "Live CD".

### Hacer un ejercicio equivalente usando otro hipervisor como Xen, VirtualBox o Parallels.

- Entramos en VirtualBox, seleccionamos nuevo y realizamos la configuración básica de la máquina virtual.

![](INSERTAR IMAGEN 5.6)

![](INSERTAR IMAGEN 5.7)

![](INSERTAR IMAGEN 5.8)

![](INSERTAR IMAGEN 5.9)

![](INSERTAR IMAGEN 5.10)

- Iniciamos la máquina y nos pedirá cómo obtener la imagen. Al introducir la imagen se ejecutará como si la estuvieramos cargando desde un USB/CD.

![](INSERTAR IMAGEN 5.11)

![](INSERTAR IMAGEN 5.12)

## Ejercicio 4.
### Crear una máquina virtual Linux con 512 megas de RAM y entorno gráfico LXDE a la que se pueda acceder mediante VNC y ssh.

Para este ejercicio crearemos una máquina virtual con el SO Lubuntu, una versión "lite" de Ubuntu que utiliza LXDE como gestor de escritorio (Lubuntu = LXDE + Ubuntu). Para este ejercicio utilizaremos un hipervidor distinto, VMWare Player, que es gratuito y el sistema de instalación es muy parecido a VirtualBox.

![](INSERTAR IMAGEN 5.13)

![](INSERTAR IMAGEN 5.14)

![](INSERTAR IMAGEN 5.15)

Una vez instalado, instalamos openssh con el comando: ```apt-get install openssh-server```

![](INSERTAR IMAGEN 5.16)

Una vez instalado, podemos acceder mediante usuario-contraseña con el comando: ```ssh usuario@ipservidor```

Se pedirá que escribamos la contraseña, la introducimos y conectaremos con la máquina virtual.

![](INSERTAR IMAGEN 5.17)

Podemos configurarlo para que el acceso sea mediante clave pública o mediante certificado pero el acceso ssh ya está disponible.

Para la conexión VNC, VMware Player nos ofrece una opción para configurar la máquina virtual como un servidor VNC. Si lo activamos y ponemos en marcha la máquina, tan solo tendríamos que ejecutar el comando: ```vinagre ipservidor:puerto``` para conectarnos a ella. 

![](INSERTAR IMAGEN 5.18)


![](INSERTAR IMAGEN 5.19)

Si lo hubieramos querido hacer mediante qemu (como se especifica en los apuntes), podríamos haber convertido la imagen de la máquina a un formato compatible con el comando ```qemu-img```, por ejemplo, con el comando: ```qemu-img convert -f vmdk -O qcow2 ~/vmware/LUbuntu\ 64-bit/LUbuntu\ 64-bit.vmdk LUbuntu64.qcow2```.

## Ejercicio 5.
### Crear una máquina virtual ubuntu e instalar en ella alguno de los servicios que estamos usando en el proyecto de la asignatura.

El [proyecto de la asignatura](https://github.com/josejapch/proyectoIV1617) está desplegado en una máquina virtual con Ubuntu Server. Pueden verse todos los pasos en la [documentacion](https://github.com/josejapch/documentacion-Proyecto-IV/blob/master/hito5.md)

## Ejercicio 6.
### Instalar una máquina virtual con Linux Mint para el hipervisor que tengas instalado.

Siguiendo los pasos de los ejercicios anteriores.

![](INSERTAR IMAGEN 5.20)







