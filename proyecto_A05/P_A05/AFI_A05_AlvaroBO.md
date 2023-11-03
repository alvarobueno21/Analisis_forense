# Análisis forense A05

## **FTK Imager**

Para empezar con este programa nos iremos a una máquina de Windows 10, nos descargaremos el programa AccessData FTK Imager y lo ejecutaremos, si no nos deja ejecutarlo, nos iremos a la cmd y lo ejecutaremos desde ahí, nos vamos a su ruta y lo ejecutamos, una vez dentro seleccionaremos el pendrive de origen del que queremos hacer la imagen y le daremos el formato E01, luego nos saldrá la siguiente pestaña donde pondremos algunos detalles como el número de caso, la evidencia y una descripción opcional y quien será el examinador, en este caso sería yo.

![img/08](https://github.com/alvarobueno21/Analisis_forense/blob/f143ca50cd73ec34bafe405267e6dbb32ea3acf3/proyecto_A05/P_A05/img/img08.png)


Luego le daremos click en Siguiente y elegiremos la imagen de destino en este caso el pendrive donde queramos meter la imagen del pendrive de origen, podremos seleccionar también si queremos que nos haga varias imagenes en partes, podemos seleccionar en cuantos Kb, Mb o Gb queremos las imágenes y le daremos click en Finish.

A continuación podremos ver el proceso de creación de la imagen y el tiempo estimado en que tardará en hacerse, luego nos saldrá una pestaña de verificación donde el programa hará varias comprobaciones y si todo esta bien nos saldrá una ultima pestaña con los resultados.

![img/img01](https://github.com/alvarobueno21/Analisis_forense/blob/6a04fde90b3127e41d063419e16f9a9aff675457/proyecto_A05/P_A05/img/img01.png)


En la siguiente pestaña podremos ver los hashes que nos ha creado el programa de MD5 y SHA1 y si hay algun sector que esté mal, en este caso no ha fallado nada y todo esta correcto.

![img/img02](https://github.com/alvarobueno21/Analisis_forense/blob/6a04fde90b3127e41d063419e16f9a9aff675457/proyecto_A05/P_A05/img/img02.png)


## **Programa guymager:**

Lo primero que haremos será ejecutar sudo guymager en la consola de comandos, luego se nos abrirá una pestaña donde seleccionaremos la unidad a la que queramos hacer la imagen y haremos click derecho en el usb que queramos hacer la imagen y le daremos a acquire imagen (Adquirir imagen)

Una vez hecho esto se nos abrirá la siguiente pestaña donde tendremos varios apartados y donde lo podremos rellenar con el número del caso, de la evidencia, examinador …

En la parte de abajo en Destination pondremos la ruta donde queremos que el programa nos cree la imagen, luego le pondremos un nombre al fichero y le daremos a Start para que empiece.

![img/img03](https://github.com/alvarobueno21/Analisis_forense/blob/f143ca50cd73ec34bafe405267e6dbb32ea3acf3/proyecto_A05/P_A05/img/img03.png)

Aquí tendremos que esperar un rato hasta que termine el proceso, como podemos ver ahora mismo esta Running (corriendo) es decir se está creando la imagen, esperaremos a que salga el punto en verde para que termine la creación de la imagen y listo.

![img/img04](https://github.com/alvarobueno21/Analisis_forense/blob/f143ca50cd73ec34bafe405267e6dbb32ea3acf3/proyecto_A05/P_A05/img/img04.png)

A continuación verificaremos el fichero que se acaba de crear y que contiene un fichero de información de la imagen creada, si abrimos el fichero nos podremos encontrar los hashes que ha calculado tanto el MD5 como el SHA1: 

![img/img05](https://github.com/alvarobueno21/Analisis_forense/blob/6a04fde90b3127e41d063419e16f9a9aff675457/proyecto_A05/P_A05/img/img05.png)

## Programa DD:

Para hacer este programa lo haremos con la consola de comandos, el sistema operativo que hemos seleccionado el sistema kali y para hacer la imagen tendremos que tener introducidos los dos pendrives a nuestra máquina virtual y ejecutaremos el comando sudo df -h para ver el sistema de ficheros y donde está montado así como otras opciones de tamaño, porcentaje en uso, etc. 

Es importante que metamos **sudo** delante del comando para que lo ejecute con **privilegios administrativos** si no, no nos ejecutará el comando.

Una vez sabemos la información obtenida con el anterior comando, tendremos que ejecutar el siguiente comando, la sintaxis para el comando es la siguiente **dd if= el archivo de origen** con la ruta con el sistema de ficheros y su letra y número de nuestro pendrive de origen y **of= el archivo de destino** con la ruta donde esta montado nuestro pendrive de destino y img03.dd que sería el nombre que le hemos dado al fichero que creará el comando dd

![img/img06](https://github.com/alvarobueno21/Analisis_forense/blob/6a04fde90b3127e41d063419e16f9a9aff675457/proyecto_A05/P_A05/img/img06.png)

El siguiente paso sería calcular los algoritmos de hash, sería tan sencillo como poner los siguientes comandos, la sintaxis sería la misma para calcular tanto SHA1 como MD5, tendríamos que poner sudo para ejecutar como administrador luego sha1sum o md5sum depende del que queramos calcular y luego la ruta de nuestro pendrive de destino que contiene el fichero img03.dd que creamos anteriormente y nos calcularía los hashes: 

![img/img07](https://github.com/alvarobueno21/Analisis_forense/blob/6a04fde90b3127e41d063419e16f9a9aff675457/proyecto_A05/P_A05/img/img07.png)
