#Ejercicios Tema 6

## Ejercicio 1.
### Instalar chef en la máquina virtual que vayamos a usar

Instalamos con el comando: 

```curl -L https://www.opscode.com/chef/install.sh | bash```

![](6.1)

## Ejercicio 3.
### Desplegar la aplicación de DAI con todos los módulos necesarios usando un playbook de Ansible.

```
- hosts: azure
  remote_user: usuario
  become: yes
  become_method: sudo
  tasks:
  - name: Repo update
    apt: update_cache=yes

  - name: Instalar dependencias
    apt: name={{ item }}
    with_items:
      - git
      - python-setuptools
      - python-dev
      - build-essential
      - python-psycopg2

  - name: Instalar pip
    easy_install: name=pip

  - name: Descargar aplicacion
    git: repo=https://github.com/josejapch/proyectoIV1617.git dest=~ force=yes

  - name: Instalar requisitos
    pip: requirements=~/proyectoIV1617/requirements.txt

  - name: Ejecutar aplicación
    command: python ~/proyectoIV1617/manage.py runserver 0.0.0.0:80
```

## Ejercicio 4.
### Instalar una máquina virtual Debian usando Vagrant y conectar con ella.

Aprovecho que he roto la máquina virtual de DAI para instalarla y explicar el proceso:

- Creamos el Vagrantfile: ```vagrant init bento/ubuntu-16.04```
- Inicializamos la máquina: ```vagrant up```

![](6.2)

*NOTA: En el momento que realicé vagrant up por primera vez no recordé hacer la captura... por lo que la captura es de un segundo inicio.*

- Conectamos con ella mediante ssh: ```vagrant ssh```

![](6.3)

## Ejercicio 5.
### Crear un script para provisionar `nginx` o cualquier otro servidor web que pueda ser útil para alguna otra práctica.

Si usamos el Vagrantfile del ejercicio anterior:

```
Vagrant.configure("2") do |config|

  config.vm.box = "bento/ubuntu-16.04"
  config.vm.network "forwarded_port", guest: 5000, host: 8080

end
```

Nos quedaría:

```
Vagrant.configure("2") do |config|

  config.vm.box = "bento/ubuntu-16.04"
  config.vm.network "forwarded_port", guest: 5000, host: 8080
  
  config.vm.provision "shell",
        inline: "sudo apt-get install nginx"

end
```
