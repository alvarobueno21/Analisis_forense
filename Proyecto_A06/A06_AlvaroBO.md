# Trabajo Forense P6

# Indice
1. [Introducción](#introducción)
2. [Programas utilizados](#programas-utilizados)
   - [Magnet RAM Capture](#magnet-ram-capture)
   - [Win Triage](#win-triage)
   - [FTK Imager](#ftk-imager)

# Introducción

Para hacer el siguiente trabajo nos fijaremos en la norma APINAG4 que hicimos en la anterior practica y veremos el orden de volatilidad a la hora de recolectar evidencias, a partir de ahí sabemos que el orden será empezar con RAM Capture para que nos saque de manera segura el contenido completo de la memoria volátil, luego usaremos el programa WinTriage que nos sacará el DFIR que es una especie de respuesta anti-incidenttes de seguridad informática y nos ayudará a analizar la actividad del usuario en esa máquina y si ha sido maliciosa, por último usaremos el programa FTK Imager para realizar una imagen completa del disco de la máquina virtual.

## Programas utilizados

### Magnet RAM Capture:

Para utilizar el siguiente programa lo primero que haremos será abrirlo y en browse pondremos la ruta donde queremos crear la captura de la RAM, le damos a start y se tomará un poco de tiempo.

![img/img01](https://github.com/alvarobueno21/Analisis_forense/blob/82587b9484a33cf1db28635a69feaf226f82d2d1/Proyecto_A06/img/img01.png)

Y una vez terminado nos dirá que todo está correcto y que ha creado el archivo Ram_registros.raw

![img/img02](https://github.com/alvarobueno21/Analisis_forense/blob/82587b9484a33cf1db28635a69feaf226f82d2d1/Proyecto_A06/img/img02.png)

### Win Triage

A continuación, usaremos WinTriage que es un programa el cual le puedes pasar varios programas y herramientas como ejecutables, y te las ejecutará y hará un informe de todo lo que ha conseguido capturar en vivo, para que funcione simplemente metemos las herramientas o ejecutables que queramos en su carpeta de Tools, en el zip de la instalación hay un bloc de notas con varios enlaces a descargas de programas, nos descargamos algunos y se quedaría así la carpeta de herramientas:

![img/img03](https://github.com/alvarobueno21/Analisis_forense/blob/82587b9484a33cf1db28635a69feaf226f82d2d1/Proyecto_A06/img/img03.png)

Y ahora ejecutamos el programa y ya nos dará el informe correctamente:

![img/img04](https://github.com/alvarobueno21/Analisis_forense/blob/82587b9484a33cf1db28635a69feaf226f82d2d1/Proyecto_A06/img/img04.png)

Y ahora nos vamos a la carpeta donde le hemos dicho que nos cree el informe y veremos que nos saca varias carpetas con varias evidencias e informes y ya estaría terminado.

![img/img05](https://github.com/alvarobueno21/Analisis_forense/blob/82587b9484a33cf1db28635a69feaf226f82d2d1/Proyecto_A06/img/img05.png)

### FTK Imager

Aquí seleccionamos en dispositivo de origen seleccionaremos disco físico que será el de nuestra máquina virtual:

![img/img06](https://github.com/alvarobueno21/Analisis_forense/blob/82587b9484a33cf1db28635a69feaf226f82d2d1/Proyecto_A06/img/img06.png)

Y ahora aquí seleccionamos donde guardaremos la imagen del disco que nos sacará el FTK Imager, en este caso seleccionamos E:\ que es el pendrive que hemos introducido a la máquina virtual. En la parte de abajo donde pone 1500 podemos fragmentar las partes de la imagen que nos sacará el programa, podemos poner el tamaño que queramos y también un rango del 1 al 9 para establecer si queremos una compresión más rápida o más pequeña.

![img/img07](https://github.com/alvarobueno21/Analisis_forense/blob/82587b9484a33cf1db28635a69feaf226f82d2d1/Proyecto_A06/img/img07.png)

Y aquí esperamos a que termine el proceso de creación de la imagen del disco duro y ya habremos finalizado la imagen del disco duro

![img/img08](https://github.com/alvarobueno21/Analisis_forense/blob/82587b9484a33cf1db28635a69feaf226f82d2d1/Proyecto_A06/img/img08.png)

Y para finalizar nos daría un resumen de los hashes en este caso MD5 y SHA1 y también los sectores del disco que han fallado o estaban mal a la hora de sacar la información:

![img/img09](https://github.com/alvarobueno21/Analisis_forense/blob/82587b9484a33cf1db28635a69feaf226f82d2d1/Proyecto_A06/img/img09.png)
