#Ejercicios Tema 1

## Ejercicio 1.
### Consultar en el catálogo de alguna tienda de informática el precio de un ordenador tipo servidor y calcular su coste de amortización a cuatro y siete años.

Antes de nada debemos saber qué es y [cómo calcular una amortización](http://www.ennaranja.com/economia-facil/que-es-y-como-calcular-una-amortizacion/). En este caso supondremos que se trata de la sustitución de un bien a los 4 años y los 7 años, por lo que tendremos que dividir el valor del servidor (sin IVA) entre esos 4 y 7 años. Si consultamos la [tabla de amortizaciones simplificada](http://www.agenciatributaria.es/AEAT.internet/Inicio/_Segmentos_/Empresas_y_profesionales/Empresarios_individuales_y_profesionales/Rendimientos_de_actividades_economicas_en_el_IRPF/Regimenes_para_determinar_el_rendimiento_de_las_actividades_economicas/Estimacion_Directa_Simplificada.shtml), podemos ver que el coeficiente lineal máximo aplicable es de un 26% (en "Equipos para tratamiento de la información y sistemas y programas informáticos). En el caso de los 4 años supondrá aplicar un 25% y un 14,29% (aproximadamente) en el caso de los 7 años por lo que nos encontramos dentro del máximo aplicable. Para realizar este ejercicio, calcularemos la amortización a un [servidor](https://www.pccomponentes.com/hp-proliant-ml310e-g8-xe-e3-1220-8gb-2tb) de 796€ (635,54€ sin IVA).

**Amortización a 4 años:**
Cuota de amortización: 158,89€ (redondeado hacia arriba)
| Año  | Amortización acumulada  | Valor  |
|:-:|:-:|:-:|:-:|
|1| | 158,89€ | 476,65€|
|2| |317,78€  |317,76€|
|3| |476,67€  |158,87€|
|4| |635,54€  |0€|

**Amortización a 7 años:**
Cuota de amortización: 90,79€ (redondeado hacia abajo)
| Año  | Amortización acumulada  | Valor  |
|:-:|:-:|:-:|:-:|
|1||90,79€|544,75€|
|2||181,58€|453,96€|
|3||272.37€|363.17€|
|4||363,16€|272,38€|
|5||453,95€|181,59€|
|6||544,74€|90,8€|
|7||635,54€|0€|
*(el valor del penúltimo año difiere un poco de la cuota de amortización por el redondeo)*

## Ejercicio 2.
### Usando las tablas de precios de servicios de alojamiento en Internet y de proveedores de servicios en la nube, Comparar el coste durante un año de un ordenador con un procesador estándar (escogerlo de forma que sea el mismo tipo de procesador en los dos vendedores) y con el resto de las características similares (tamaño de disco duro equivalente a transferencia de disco duro) en el caso de que la infraestructura comprada se usa sólo el 1% o el 10% del tiempo.

## Ejercicio 3.
### 1. ¿Qué tipo de virtualización usarías en cada caso?
[Enlace al issue](https://github.com/JJ/IV16-17/issues/1)

![Imagen Ej3.1](http://i1294.photobucket.com/albums/b605/josejapch/IV/Tema%201/ej3_zps7s1hev7w.jpg)

### 2. Crear un programa simple en cualquier lenguaje interpretado para Linux, empaquetarlo con CDE y probarlo en diferentes distribuciones.

## Ejercicio 4.
### Comprobar si el procesador o procesadores instalados tienen estos flags. ¿Qué modelo de procesador es? ¿Qué aparece como salida de esa orden?

Modelo de procesador: Intel(R) Core(TM) i7-4700MQ CPU @ 2.40GHz

Orden:

```
egrep '^flags.*(vmx|svm)' /proc/cpuinfo
```
Resultado:
![Imagen Ej4](http://i1294.photobucket.com/albums/b605/josejapch/IV/Tema%201/ej4_zps7ugqs0hw.jpg)

*(texto repetido por cada uno de los núcleos del procesador)*

##Ejercicio 5.
### 1. Comprobar si el núcleo instalado en tu ordenador contiene este módulo del kernel usando la orden kvm-ok.
![Imagen Ej5.1](http://i1294.photobucket.com/albums/b605/josejapch/IV/Tema%201/Ej5-1_zpsiip9dt0z.jpg)
### 2. Instalar un hipervisor para gestionar máquinas virtuales, que más adelante se podrá usar en pruebas y ejercicios.
Actualmente dispongo de VMware Player y VirtualBox.

![Imagen Ej5.2](http://i1294.photobucket.com/albums/b605/josejapch/IV/Tema%201/ej5-2_zpsnfbi1doa.jpg)