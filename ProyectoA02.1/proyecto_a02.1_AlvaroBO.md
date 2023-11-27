**Parte 1. Análisis forense del sistema informático**

Responde las siguientes preguntas, teniendo en cuenta que para contestar adecuadamente las preguntas deben mencionarse las herramientas empleadas y **adjuntar una captura de pantalla** **con los resultados obtenidos** para cada pregunta.

**PASOS PREVIOS**

Para empezar, tendremos que usar el programa FTK imager y cogeremos la evidencia del disco que nos han facilitado, la introducimos en el programa y sacamos los ficheros de configuración que nos interesan, para acceder a ellos nos iremos a la evidencia del disco y a la ruta root à Windows à system32 à config à Y extraer los archivos SAM, Security, software y system.

Y ya lo podremos abrir dentro del programa WRR para poder acceder a los registros. 

1. **Describe el entorno de trabajo que has escogido para realizar la actividad.**

El entorno a utilizar es en mi portátil Acer Nitro AN16-51 y estas son sus especificaciones:

- **Procesador:** 13th Gen Intel(R) Core (TM) i7-13700H   2.40 GHz
- **RAM:** 16,0 GB a 4800 Mhz
- **Tarjeta gráfica:** GeForce RTX 4050 Laptop 
- **Disco duro:** Micron 3400 MTFDKBA1TOTFH - SSD 1 TB

Luego usaré una máquina Virtual de Windows 10 con el programa VMWare Workstation Pro y estas son las especificaciones de la máquina:

- **Procesador:** 13th Gen Intel(R) Core (TM) i7-13700H   2.40 GHz (2 procesadores, 1 núcleo)
- **RAM:** 4GB
- **Discos duros virtuales:** 1 disco de 100 Gb y otro disco de 80 Gb 
1. **Describe, como mínimo, la información siguiente, relacionada con el sistema operativo instalado en el sistema informático que estás analizando:**
   1. **¿Qué tamaño tiene la partición a analizar?**

Para ver el tamaño de la partición nos iremos al autopsy y cargaremos la imagen del disco y en la parte derecha podremos ver el nombre del disco y el tamaño en bytes del disco que son 2623832064 bytes que es igual a **2.446 Gb.![](Aspose.Words.d083e4b3-ee46-45cd-95ce-a912a3c49135.001.png)**

**Herramientas utilizadas:** Autopsy: Versión 4.21.0

1. Sistema y versión del sistema operativo instalado.

![](Aspose.Words.d083e4b3-ee46-45cd-95ce-a912a3c49135.002.png)

**Herramientas utilizadas:** Autopsy: Versión 4.21.0

1. Nombre del usuario y organización registrados.

La herramienta que hemos usado ha sido FTK Imager para sacar los archivos SAM, Config, System y Software y con el programa WRR podemos ver las carpetas y registros que queramos.

Si nos vamos a la carpeta Software à Windows à Windows NT à curent version à veremos estos dos registros con la información del usuario y la organización registrados

**Herramientas utilizadas:** Autopsy: Versión 4.21.0 y WRR: Versión 4.21.0

![](Aspose.Words.d083e4b3-ee46-45cd-95ce-a912a3c49135.003.png)

1. “Product ID” asociado al sistema.

Si nos vamos a Software, a la carpeta Microsoft, WindowsNT y dentro de la carpeta Current Version buscamos ProductId

![](Aspose.Words.d083e4b3-ee46-45cd-95ce-a912a3c49135.004.png)

Y este sería el Product ID: 76487-341-1072684-22504

**Herramientas utilizadas:** Autopsy: Versión 4.21.0 y WRR: Versión 4.21.0

1. “Service Pack” instalado.

Para encontrar el Service Pack nos iremos a la carpeta Microsoft, WindowsNT y dentro de la carpeta Current Version y buscamos CSDVersion

![](Aspose.Words.d083e4b3-ee46-45cd-95ce-a912a3c49135.005.png)

**Herramientas utilizadas:** Autopsy: Versión 4.21.0 y WRR: Versión 4.21.0

1. Fecha y hora de instalación del sistema operativo.

Para ver la fecha y hora de la instalación del sistema operativo nos iremos a la misma ruta que antes, es decir Software/Microsoft/WindowsNT/Current Version/Install Date

![](Aspose.Words.d083e4b3-ee46-45cd-95ce-a912a3c49135.006.png)

Este dato nos lo da en hexadecimal y ahora con el programa dcode u otro programa web como puede ser EpochConverter pasaremos el hexadecimal a la fecha original, y nos da la fecha que sería 18 de abril de 2013 a las 15:17:02

![](Aspose.Words.d083e4b3-ee46-45cd-95ce-a912a3c49135.007.png)

**Herramientas utilizadas:** Autopsy: Versión 4.21.0 y WRR: Versión 4.21.0

1. Fecha y hora del último “shutdown”.

Esta en el fichero system à ControlSet001 à Control à Windows à Shutdown time, y aquí nos daría la fecha en binario pero si nos fijamos bien en el apartado de datetime en WIN 64 nos da la fecha correctamente y es la siguiente: 19/06/2013 

![](Aspose.Words.d083e4b3-ee46-45cd-95ce-a912a3c49135.008.png)

**Herramientas utilizadas:** Autopsy: Versión 4.21.0 y WRR: Versión 4.21.0



1. Determina qué usuarios hay definidos en el sistema (sin contar con los usuarios definidos por defecto). Para cada uno de ellos encuentra, como mínimo, la información siguiente:
   1. Fecha y hora del último “logon” del usuario.

Para ver esta información nos vamos a SAM à SAM à John à Last logon

![](Aspose.Words.d083e4b3-ee46-45cd-95ce-a912a3c49135.009.png)

Para ver esta información nos vamos a SAM à SAM à Ian à Last logon

![](Aspose.Words.d083e4b3-ee46-45cd-95ce-a912a3c49135.010.png)

Para ver esta información nos vamos a SAM à Jessy à Jessy à Last logon

![](Aspose.Words.d083e4b3-ee46-45cd-95ce-a912a3c49135.011.png)



1. Fecha y hora del último cambio de contraseña.

Para ver esta información nos vamos a SAM à SAM à John à Last password set y 

nos saldrá la última vez que se modificó la contraseña

![](Aspose.Words.d083e4b3-ee46-45cd-95ce-a912a3c49135.012.png)

Para ver esta información nos vamos a SAM à SAM à Ian à Last password set y 

nos saldrá la última vez que se modificó la contraseña

![](Aspose.Words.d083e4b3-ee46-45cd-95ce-a912a3c49135.013.png)

Para ver esta información nos vamos a SAM à SAM à Jessy à Last password set y 

nos saldrá la ultima vez que se modificó la contraseña

![](Aspose.Words.d083e4b3-ee46-45cd-95ce-a912a3c49135.014.png)



1. ¿Existe alguna contradicción entre las fechas halladas en éste apartado y el anterior? En caso afirmativo, ¿a qué crees que puede ser debido?

Si nos fijamos bien en la fecha de instalación del sistema operativo vemos que es el 18 de abril de 2013 a las 15:17:02 y si nos vamos al usuario john y vemos el último inicio de sesión es el 18 de marzo a las 3:10:49, es decir el usuario inicio sesión un mes antes de que el sistema operativo estuviera instalado lo cual es imposible, por lo tanto, deducimos que el delincuente ha podido falsificar dicho registro. 

1. Localiza, extrae y relaciona los siguientes hallazgos, asociándose, si es posible, al usuario al cual pertenecen:
   1. Localización y extracción de archivos eliminados.
   1. Documentos y archivos fotográficos relacionados con presuntas conductas delictivas.
   1. ¿Los ficheros fotográficos contienen algún tipo de metadatos? En caso afirmativo, ¿qué información te permiten obtener?
   1. Hojas de cálculo.
   1. Ficheros comprimidos.
   1. ¿Has localizado algún fichero con contraseña? ¿Has podido acceder a su contenido?
   1. Estudio de la navegación a través de internet: históricos de internet, URLs favoritas, búsquedas, etc.

4\.2 Localiza, extrae y relaciona los siguientes hallazgos, asociándose, si es posible, al usuario al cual pertenecen: (De la segunda evidencia que encontremos)

1. Localización y extracción de archivos eliminados.
1. Documentos y archivos fotográficos relacionados con presuntas conductas delictivas.
1. ¿Los ficheros fotográficos contienen algún tipo de metadatos? En caso afirmativo, ¿qué información te permiten obtener?
1. Hojas de cálculo.
1. Ficheros comprimidos.
1. ¿Has localizado algún fichero con contraseña? ¿Has podido acceder a su contenido?
1. Estudio de la navegación a través de internet: históricos de internet, URLs favoritas, búsquedas, etc.
1. ¿Has podido localizar alguna otra evidencia relacionada con algún otro tipo delictivo? En caso afirmativo, describe y extrae los hallazgos localizados, y determina y lleva a cabo aquellas acciones que realizarías en calidad de perito (puedes utilizar, como guión, los apartados de la pregunta 4).

Anexo a parte: Hacer en un documento a parte la estructuración de las tablas

Ruta de localización completa 

Contenido del fichero: es decir, en caso que el contenido del fichero se pueda mostrar (una fotografía, una hoja de cálculo, etc.), debe incluirse en este apartado.

MAC time.

Tamaño lógico del fichero.

Valor hash del fichero.





