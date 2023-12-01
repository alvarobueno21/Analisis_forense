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
2. **Describe, como mínimo, la información siguiente, relacionada con el sistema operativo instalado en el sistema informático que estás analizando:**
   a. **¿Qué tamaño tiene la partición a analizar?**

Para ver el tamaño de la partición nos iremos al autopsy y cargaremos la imagen del disco y en la parte derecha podremos ver el nombre del disco y el tamaño en bytes del disco que son 2623832064 bytes que es igual a **2.446 Gb.**
![img/1.png](https://github.com/alvarobueno21/Analisis_forense/blob/138d56dbc0fb0aa1e5736aebff000700d00454a6/ProyectoA02.1/img/1.png)

**Herramienta utilizada:** Autopsy: Versión 4.21.0

   b. Sistema y versión del sistema operativo instalado.

![img/2.png](https://github.com/alvarobueno21/Analisis_forense/blob/138d56dbc0fb0aa1e5736aebff000700d00454a6/ProyectoA02.1/img/2.png)

**Herramienta utilizada:** Autopsy: Versión 4.21.0

   c. Nombre del usuario y organización registrados.

La herramienta que hemos usado ha sido FTK Imager para sacar los archivos SAM, Config, System y Software y con el programa WRR podemos ver las carpetas y registros que queramos.

Si nos vamos a la carpeta Software à Windows à Windows NT à curent version à veremos estos dos registros con la información del usuario y la organización registrados

**Herramientas utilizadas:** FTK Imager: Versión 4.2.0.13 y WRR: Versión 4.21.0

![img/3.png](https://github.com/alvarobueno21/Analisis_forense/blob/138d56dbc0fb0aa1e5736aebff000700d00454a6/ProyectoA02.1/img/3.png)

   d. “Product ID” asociado al sistema.

Si nos vamos a Software, a la carpeta Microsoft, WindowsNT y dentro de la carpeta Current Version buscamos ProductId

![img/4.png](https://github.com/alvarobueno21/Analisis_forense/blob/138d56dbc0fb0aa1e5736aebff000700d00454a6/ProyectoA02.1/img/4.png)

Y este sería el Product ID: 76487-341-1072684-22504

**Herramienta utilizada:** WRR: Versión 4.21.0

   e. “Service Pack” instalado.

Para encontrar el Service Pack nos iremos a la carpeta Microsoft, WindowsNT y dentro de la carpeta Current Version y buscamos CSDVersion

![img/5.png](https://github.com/alvarobueno21/Analisis_forense/blob/138d56dbc0fb0aa1e5736aebff000700d00454a6/ProyectoA02.1/img/5.png)

**Herramienta utilizada:** WRR: Versión 4.21.0

   f. Fecha y hora de instalación del sistema operativo.

Para ver la fecha y hora de la instalación del sistema operativo nos iremos a la misma ruta que antes, es decir Software/Microsoft/WindowsNT/Current Version/Install Date

![img/6.png](https://github.com/alvarobueno21/Analisis_forense/blob/138d56dbc0fb0aa1e5736aebff000700d00454a6/ProyectoA02.1/img/6.png)

Este dato nos lo da en hexadecimal y ahora con el programa dcode u otro programa web como puede ser EpochConverter pasaremos el hexadecimal a la fecha original, y nos da la fecha que sería 18 de abril de 2013 a las 15:17:02

![img/7.png](https://github.com/alvarobueno21/Analisis_forense/blob/138d56dbc0fb0aa1e5736aebff000700d00454a6/ProyectoA02.1/img/7.png)

**Herramienta utilizada:** WRR: Versión 4.21.0 y Epoch Converter (web)

g. Fecha y hora del último “shutdown”.

Esta en el fichero system à ControlSet001 à Control à Windows à Shutdown time, y aquí nos daría la fecha en binario pero si nos fijamos bien en el apartado de datetime en WIN 64 nos da la fecha correctamente y es la siguiente: 19/06/2013 

![img/8.png](https://github.com/alvarobueno21/Analisis_forense/blob/138d56dbc0fb0aa1e5736aebff000700d00454a6/ProyectoA02.1/img/8.png)

**Herramienta utilizada:** WRR: Versión 4.21.0


3. Determina qué usuarios hay definidos en el sistema (sin contar con los usuarios definidos por defecto). Para cada uno de ellos encuentra, como mínimo, la información siguiente:
   a. Fecha y hora del último “logon” del usuario.

Para ver esta información nos vamos al registro SAM luego al apartado SAM -> John -> Last logon

![img/9.png](https://github.com/alvarobueno21/Analisis_forense/blob/138d56dbc0fb0aa1e5736aebff000700d00454a6/ProyectoA02.1/img/9.png)

**Herramienta utilizada:** WRR: Versión 4.21.0

Para ver esta información nos vamos al registro SAM luego al apartado SAM -> Ian -> Last logon

![img/10.png](https://github.com/alvarobueno21/Analisis_forense/blob/138d56dbc0fb0aa1e5736aebff000700d00454a6/ProyectoA02.1/img/10.png)

**Herramienta utilizada:** WRR: Versión 4.21.0

Para ver esta información nos vamos al registro SAM luego al apartado SAM -> Jessy -> Last logon

![img/11.png](https://github.com/alvarobueno21/Analisis_forense/blob/138d56dbc0fb0aa1e5736aebff000700d00454a6/ProyectoA02.1/img/11.png)

**Herramienta utilizada:** WRR: Versión 4.21.0

b. Fecha y hora del último cambio de contraseña.

Para ver esta información nos vamos al registro SAM luego al apartado SAM después nos vamos al usuario John y a Last password set y nos saldrá la última vez que se modificó la contraseña.

![img/12.png](https://github.com/alvarobueno21/Analisis_forense/blob/138d56dbc0fb0aa1e5736aebff000700d00454a6/ProyectoA02.1/img/12.png)

**Herramienta utilizada:** WRR: Versión 4.21.0

Para ver esta información nos vamos al registro SAM luego al apartado SAM después nos vamos al usuario Ian después Last password set y nos saldrá la última vez que se modificó la contraseña.

![img/13.png](https://github.com/alvarobueno21/Analisis_forense/blob/138d56dbc0fb0aa1e5736aebff000700d00454a6/ProyectoA02.1/img/13.png)

**Herramienta utilizada:** WRR: Versión 4.21.0

Para ver esta información nos vamos al registro SAM luego al apartado SAM y nos vamos al usuario Jessy luego en Last password set y nos saldrá la ultima vez que se modificó la contraseña.

![img/14.png](https://github.com/alvarobueno21/Analisis_forense/blob/138d56dbc0fb0aa1e5736aebff000700d00454a6/ProyectoA02.1/img/14.png)

**Herramienta utilizada:** WRR: Versión 4.21.0


   c. ¿Existe alguna contradicción entre las fechas halladas en éste apartado y el anterior? En caso afirmativo, ¿a qué crees que puede ser debido?

Si nos fijamos bien en la fecha de instalación del sistema operativo vemos que es el 18 de abril de 2013 a las 15:17:02 y si nos vamos al usuario John y vemos el último inicio de sesión es el 18 de marzo a las 3:10:49, es decir el usuario inicio sesión un mes antes de que el sistema operativo estuviera instalado lo cual es imposible, por lo tanto, deducimos que el delincuente ha podido falsificar dicho registro. 

4. Localiza, extrae y relaciona los siguientes hallazgos, asociándose, si es posible, al usuario al cual pertenecen:
   a. Localización y extracción de archivos eliminados.
Si queremos ver a que usuario pertenece cada uno de los ficheros podemos parsear el fichero SAM con regripper y así veremos que estos son sus identificadores:
Administrador {500}
Invitado {501}
John {1003}
Ian {1004}
Jessy {1005}

Si nos vamos al apartado de Deleted Files en autopsy podemos ver que en total tenemos 582 archivos, de los cuales tenemos 85 archivos que son imágenes que podemos visualizar y si vemos las imágenes podemos observar que hay 38 imágenes que están relacionadas con el caso que estamos investigando, de esas 38 solo hay 19 imágenes únicas donde aparecen fotografías como mercancía de droga, pastillas, fabricando coca, rayas de coca, almacenes y alijos de droga.
Anotación: También podemos observar que en la carpeta CarvedFiles y OrphanFiles están las mismas imágenes que encontramos en el apartado Deleted Files pero tienen otros nombres de archivo.

b. Documentos y archivos fotográficos relacionados con presuntas conductas delictivas.
En el apartado de Recycler, podemos ver una imagen que nos da alguna pista de un local o almacen donde podría encontrarse algun alijo de droga, el usuario de esta imagen corresponde al identificador 1003, es decir es del usuario John.
Si nos vamos a la carpeta de Desktop podemos ver varios documentos entre ellos un documento llamado manufacturing amfetas.link en el que encontramos una guía para fabricar metanfetamina en casa, también nos encontramos otro documento manufacturing.link que contiene los usos de varias pastillas, explicación y sintesis del éxtasis... , seguimos investigando y nos encontramos otro documento llamado provider.ico donde hay varios números de telefono de contactos y los horarios a los que se les puede contactar, con la dirección del punto de encuentro, etc. Por ultimo nos encontramos un documento pdf llamado coca.pdf que tiene información sobre las plantas de coca en colombia e información importante sobre tipos de plantas, etc.

En el usuario John si nos metemos en la carpeta de Mataro store podemos encontrar varias imágenes y planos que quizas sea uno de los almacenes de Mataro. También nos iremos a la carpeta de My Pictures y podemos ver varias imagenes que se duplicaban con las que teniamos anteriormente pero hay una que es importante y no esta duplicada y se llama proceso final donde explica el proceso a seguir para hacer ciertas drogas.

   c. ¿Los ficheros fotográficos contienen algún tipo de metadatos? En caso afirmativo, ¿qué información te permiten obtener?

   Si, para ello nos iremos a las carpetas de las imágenes tanto de Recycler como en My Documents/Mataro Store podemos observar varias imágenes en la que podemos extraer algunos metadatos como la localización y el dispositvo con el que se tomó la foto.
   
   En la foto 20130404_102715.jpg podemos ver en los metadatos su latitud y longitud, si lo buscamos en google podemos ver que la ubicación es 139 Carrer LLauder en Mataró, Cataluña, también podemos ver la información del dispositivo con la que se hizó la foto en este caso es el Samsung GT-18190 (Samsung S3 mini) y aquí tendríamos una foto de la calle:

   ![img/evidencia_calle](https://github.com/alvarobueno21/Analisis_forense/blob/3da4eb33f1155624f1dbe4f8acd4ffd4aafbe710/ProyectoA02.1/img/evidencia_calle.png)

Podemos ver otras fotos como "emcdda_building[1].jpg" que nos da información en los metadatos y nos dice que el dispositivo con el que se tomó la foto es la cámara Nikon D300.
También nos encontramos con la foto "20130329_140033.jpg" que nos da información en sus metadatos sobre el dispositivo con el que se tomó la foto y que es el Samsung GT-18190 (Samsung S3 mini).

   d. Hojas de cálculo.
   En la ruta del escritorio podemos ver un documento xls que se llama Contactes y que traducido del catalán al español significa Contactos y tiene alguna información que nos puede ser de utilidad, el fichero esta cifrado con contraseña y luego explicaremos el proceso de como lo pudimos descifrar.
   En la ruta de Documents and Settings/Default User/Templates encontramos varios excel como son "excel.xls" y "excel4.xls" pero que no tienen información valiosa para el caso y no tienen apenas datos en su interior.
   
   e. Ficheros comprimidos.
   He podido encontrar un fichero en el usuario John, en su carpeta SendTo llamado Compressed (zipped) Folder.ZFSendToTarget.
   
   f. ¿Has localizado algún fichero con contraseña? ¿Has podido acceder a su contenido?
   He podido localizar un documento llamado contrasenyas.xls que estaba ubicado dentro del usuario John en la carpeta de Mis documentos, para poder ver descifrar la contraseña usaremos el programa Excel Password Recovery Lastic y una vez dentro podemos ver el contenido del fichero donde tenemos información de un cliente llamado María, su numero de telefono y la fecha en que hizo varias ventas de 1 gr de coca que se cobró a 60 euros.

   g. Estudio de la navegación a través de internet: históricos de internet, URLs favoritas, búsquedas, etc.
   Si nos vamos al usuario John y nos metemos en la carpeta de Cookies podemos ver algunas de las cookies en algunos sitios web como pueden ser ebay, fotomotor, terrasa.cat (si recordamos algunas de las imágenes 
   encontradas en Deleted Files tenian de nombre Almacen Terrasa por lo que tiene relación con este caso)

   En el usuario John en la carpeta de History.IE5 podemos ver un fichero index.dat donde se encuentran los enlaces a los que el usuario John ha tenido acceso, por ejemplo vemos que en youtube ha buscado como hacer    
   cocaina, también ha buscado en bing pena delito trafico de drogas.


5.  ¿Has podido localizar alguna otra evidencia relacionada con algún otro tipo delictivo? En caso afirmativo, describe y extrae los hallazgos localizados, y determina y lleva a cabo aquellas acciones que realizarías en calidad de perito (puedes utilizar, como guión, los apartados de la pregunta 4).

Si he podido encontrar alguna evidencia relacionado con otro caso de pornografía y aquí realizo otra vez el apartado 4 para determinar los hallazgos encontrados de este nuevo caso.




4\.2 Localiza, extrae y relaciona los siguientes hallazgos, asociándose, si es posible, al usuario al cual pertenecen: (De la segunda evidencia que encontremos)

a. Localización y extracción de archivos eliminados.

b. Documentos y archivos fotográficos relacionados con presuntas conductas delictivas.

En el apartado de Recycled podemos ver un documento sospechoso donde en su interior nos encontramos material y palabras relacionadas con contenido pornográfico por lo que deducimos que pertenece a este otro caso, si vemos el identificador de usuario coincide con el usuario Ian.  doc1 - recycler - s-1-5-21- segunda carpeta

c. ¿Los ficheros fotográficos contienen algún tipo de metadatos? En caso afirmativo, ¿qué información te permiten obtener?
d. Hojas de cálculo.
e. Ficheros comprimidos.
f. ¿Has localizado algún fichero con contraseña? ¿Has podido acceder a su contenido?
g. Estudio de la navegación a través de internet: históricos de internet, URLs favoritas, búsquedas, etc.
 





Anexo a parte: Hacer en un documento a parte la estructuración de las tablas

Ruta de localización completa 

Contenido del fichero: es decir, en caso que el contenido del fichero se pueda mostrar (una fotografía, una hoja de cálculo, etc.), debe incluirse en este apartado.

MAC time.

Tamaño lógico del fichero.

Valor hash del fichero.





