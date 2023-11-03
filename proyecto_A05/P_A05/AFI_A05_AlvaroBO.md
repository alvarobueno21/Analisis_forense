# Análisis forense A05

## **FTK Imager**

Para empezar con este programa nos iremos a una máquina de Windows 10, nos descargaremos el programa AccessData FTK Imager y lo ejecutaremos, si no nos deja ejecutarlo, nos iremos a la cmd y lo ejecutaremos desde ahí, nos vamos a su ruta y lo ejecutamos, una vez dentro Seleccionaremos el pendrive de origen del que queremos hacer la imagen y le daremos el formato E01, luego nos saldrá la siguiente pestaña donde pondremos algunos detalles como el numero de caso, la evidencia y una descripción opcional y quien será el examinador, en este caso sería yo.

![Untitled](Ana%CC%81lisis%20forense%20A05%20c7d1f559e06040e29e9891b6e25a0635/Untitled.png)
![[img01]]
Luego le daremos click en Siguiente y eligiremos la imagen de destino en este caso el pendrive donde queramos meter la imagen del pendrive de origen, podremos seleccionar también si queremos que nos haga varias imagenes en partes, podemos seleccionar en cuantos Kb, Mb o Gb queremos las imagenes y le daremos click en Finish.

A continuacion podremos ver el proceso de creación de la imagen y el tiempo estimado en que tardará en hacerse, luego nos saldrá una pestaña de verificación donde el programa hará varias comprobaciones y si todo esta bien nos saldrá una ultima pestaña con los resultados.

![Untitled](Ana%CC%81lisis%20forense%20A05%20c7d1f559e06040e29e9891b6e25a0635/Untitled%201.png)

En la siguiente pestaña podremos ver los hashes que nos ha creado el programa de MD5 y SHA1 y si hay algun sector que esté mal, en este caso no ha fallado nada y todo esta correcto.

![Untitled](Ana%CC%81lisis%20forense%20A05%20c7d1f559e06040e29e9891b6e25a0635/Untitled%202.png)

## **Programa guymager:**

Lo primero que haremos será ejecutar sudo guymager en la consola de comandos, luego se nos abrirá una pestaña donde seleccionaremos la unidad a la que queramos hacer la imagen y haremos click derecho en el usb que queramos hacer la imagen y le daremos a acquire imagen (Adquirir imagen)

Una vez hecho esto se nos abrirá la siguiente pestaña donde tendremos varios apartados y donde lo podremos rellenar con el numero del caso, de la evidencia, examinador …

En la parte de abajo en Destination pondremos la rta donde queremos que el programa nos cree la imagen, luego le pondremos un nombre al fichero y le daremos a Start para que empiece.

![Untitled](Ana%CC%81lisis%20forense%20A05%20c7d1f559e06040e29e9891b6e25a0635/Untitled%203.png)

Aquí tendremos que esperar un rato hasta que termine el proceso, como podemos ver ahora mismo esta Running (corriendo) es decir se está creando la imagen, esperaremos a que salga el punto en verde para que termine la creación de la imagen y listo.

![Untitled](Ana%CC%81lisis%20forense%20A05%20c7d1f559e06040e29e9891b6e25a0635/Untitled%204.png)

A continuación verificaremos el fichero que se acaba de crear y que contiene un fichero de informacion de la imagen creada, si abrimos el fichero nos podremos encontrar los hashes que ha calculado tanto el MD5 como el SHA1: 

![Untitled](Ana%CC%81lisis%20forense%20A05%20c7d1f559e06040e29e9891b6e25a0635/Untitled%205.png)

## Programa DD:

Para hacer esta ultima parte se hace a partir de la consola de comandos, el sistema operativo que hemos seleccionado el sistema kali y para hacer la imagen tendremos que tener introducidos los dos pendrives a nuestra maquina virtual y ejecutaremos el comando sudo df -h para ver el sistema de ficheros y donde está montado así como otras opciones de tamaño, porcentaje en uso, etc. 

Es importante que metamos **sudo** delante del comando para que lo ejecute con **privilegios administrativos** si no, no nos ejecutará el comando.

Una vez sabemos la información obtenida con el anterior comando, tendremos que ejecutar el siguiente comando, la sintaxis para el comando es la siguiente **dd if= el archivo de origen** con la ruta con el sistema de ficheros y su letra y numero de nuestro pendrive de origen y **of= el archivo de destino** con la ruta donde esta montado nuestro pendrive de destino y img03.dd que sería el nombre que le hemos dado al fichero que creará el comando dd

![Untitled](Ana%CC%81lisis%20forense%20A05%20c7d1f559e06040e29e9891b6e25a0635/Untitled%206.png)

El siguiente paso sería calcular los algoritmos de hash, sería tan sencillo como poner los siguientes comandos, la sintaxis sería la misma para calcular tanto SHA1 como MD5, tendríamos que poner sudo para ejecutar como administrador luego sha1sum o md5sum depende del que queramos calcular y luego la ruta de nuestro pendrive de destino que contiene el fichero img03.dd que creamos anteriormente y nos calcularía los hashes: 

![Untitled](Ana%CC%81lisis%20forense%20A05%20c7d1f559e06040e29e9891b6e25a0635/Untitled%207.png)