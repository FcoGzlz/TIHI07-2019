# TIHI07-2019
### **Introducción**
Esta es una guía en la cual se explicarán los pasos a seguir para la puesta en marcha de una "WorkStation". Para esto, nos guiaremos por la siguiente lista, la cual mostrará los cada uno de los puntos a seguir, luego se detallarà una guìa paso a paso, la cual cubrirá todos los puntos en la lista:
1. [**Instalar en Visrtual Box el Sistema Operativo CentOS o Ubuntu (en este caso se utilizó CentOS 7,3 minimal)**](#paso1)
2. [**Conectarse a la máquina virtual mediante el servicio SSH**](#paso2)
3. [**Desinstalar la versión de Java que viene por defecto en el Sistema e instalar Java de Oracle**](#paso3)
4. [**Instalar un ambiente gráfico (en este caso se utilizó Gnome)**](#paso4)
5. [**Instalar un IDE (en este caso se instaló NetBeans)**](#paso5)
6. [**Instalar Postgre SQL versión 9.6 o superioir**](#paso6)
7. [**Crear un test Java para comprobar la conexión de la Base de Datos**](#paso7)

Antes de comenzar, cave aclarar algunos puntos sobre esta guía:

* Todos los comandos utilizados, se usan estando en el **Super Usuario** o **usuario Root**.
* A partir de la instalación del software **Putty**, podrás copiar y pegar los comandos, para facilitar el seguimiento de los pasos.
* Es importante tener la **Virtualización activada** para poder virtualizar CentOS, si no estás seguro si tu ordenador tiene activada esta opción, puedes seguir los siguietes pasos, de lo contrario, puedes pasar directamente al primer paso de la guía.

**Activar virtualización**

Para esto, debes acceder a la **BIOS** del sistema, una vez allí, seleccionar el apartado **Configuration**, dentro de este apartado, se encuentra la opción **Virtual Technology** la cual debe estar configurada como **Enable**:

<p align="center">
        <img src="https://raw.githubusercontent.com/FcoGzlz/TIHI07-2019/master/BIOS/IMG_20190427_220556000.jpgG" width="900px" height="200px"/>
 </p>
    
--------------------------------------------------------------------------------------------------------------------------------


1. **Instalacion de CentOS en Máquina Virtual.**<a name ="paso1"></a>

    1.1	Para comenzar descargaremos el software para la virtualización del S.O CentOS en nuestro ordenador, utilizando el             siguiente link: (https://www.virtualbox.org/wiki/Downloads) y seleccionaremos el que corresponda a nuestro sistema.

    1.2 Una vez descargado el programa, lo instalaremos.
   
   <p align="center">
        <img src="https://raw.githubusercontent.com/FcoGzlz/TIHI07-2019/master/Mauina%20Virutal%20y%20PUTTY/VB1.PNG"/>
    </p>

    1.3 Ya instalado el software, procederemos a descargar CentOS 7 minimal, para lo cual nos dirigiremos a: (https://www.centos.org/download/). Seleccionaremos la versión minimal.
   
   <img src="https://user-images.githubusercontent.com/48935510/56478835-f543db80-647f-11e9-927f-6b3dfda776de.jpg" width="900px" height="200px"/>


    1.4 Una vez descargados **VirtualBox** y **CentOS 7**, abriremos **VirtualBox** y seleccionaremos la opción **Nueva** para crear una nueva máquina:
   
   <p align="center">
        <img src="https://raw.githubusercontent.com/FcoGzlz/TIHI07-2019/master/Mauina%20Virutal%20y%20PUTTY/VBNUEVA2.PNG"/>
    </p>
   
    1.5 En las opciones para la creación, se encontrarán los siguientes campos:
   
    * **Nombre:** Aquí se define el nombre que tendrá la carpeta la la máquina virtual.
    * **Carpeta de máquina:** Esta es la ruta donde se guardará la máquina (en caso de querer respaldar la máquina, se debe copiar la carpeta de esta ruta), se recomienda dejar la ruta por defecto, pero se puede cambiar si asi se desea.
    * **Tipo:** Aquí se selecciona el tipo de S.O, en nuestro caso es **Linux** 
    * **Versión:** Esta es la versión de S.O, por lo que seleccionaremos **Other Linux (64-bit)**, es importante seleccionar la versión de 64 bits.
    
    Una vez completados los campos, presionaremos **Next**.
   
    <p align="center">
        <img src="https://raw.githubusercontent.com/FcoGzlz/TIHI07-2019/master/Mauina%20Virutal%20y%20PUTTY/NuevoVB.PNG"/>
    </p>
    
   1.6 En la siguiente ventana, se configurará la cantidad de **Memoria RAM** que se asignará a la máquina, se recomienda dejar **2 GB** de memoria, lo que equibale a **2048 MB**, esto será suficiente para ejecutar algunos programas que se instalarán en la máquina, luego presionaremos **Next**:
    
    <p align="center">
    <img src="https://raw.githubusercontent.com/FcoGzlz/TIHI07-2019/master/Mauina%20Virutal%20y%20PUTTY/BVMemoria.PNG"  width="600px" height="420px"/>
    </p>

  
   1.7 Lo siguiente es la asignación de **Disco Duro**:
   
   
   1.7.1 Seleccionaremos la opción **Crear un disco duro virtual ahora** y presionaremos **Crear**.
   
   <p align="center">
        <img src="https://raw.githubusercontent.com/FcoGzlz/TIHI07-2019/master/Mauina%20Virutal%20y%20PUTTY/VBDisco.PNG"/>
    </p>
   
   
   1.7.2 Seleccionaremos la opción **VDI (VirtualBox Disk Image)**, seleccionamos **Next**.
   
   <p align="center">
        <img src="https://raw.githubusercontent.com/FcoGzlz/TIHI07-2019/master/Mauina%20Virutal%20y%20PUTTY/VBDisco2.PNG"/>
   </p>
    
   1.7.3 En la siguiente ventana, seleccionaremos la opción **Reservado dinámicamente**, esto permite que el tamaño del disco aumente según instalemos programas, presionaremos **Next**.
   
   <p align="center">
        <img src="https://raw.githubusercontent.com/FcoGzlz/TIHI07-2019/master/Mauina%20Virutal%20y%20PUTTY/VBTama%C3%B1oDisco.PNG"/>
    </p>
    
   1.7.4 Para continuar, configuraremos el tamaño del disco, pondremos un mínimo de **100 GB** y presionaremos **Crear**.
    
  <p align="center">
        <img src="https://raw.githubusercontent.com/FcoGzlz/TIHI07-2019/master/Mauina%20Virutal%20y%20PUTTY/VBTama%C3%B1oDisco2.PNG"/>
    </p>


   1.8 Una vez configurada la máquina, presionaremos el botón **Iniciar**, y seleccionaremos nuestro **ISO** de **CentOS** antes descargado:
   
   <p align="center">
        <img src="https://raw.githubusercontent.com/FcoGzlz/TIHI07-2019/master/Mauina%20Virutal%20y%20PUTTY/VBIso.PNG"/>
    </p>



2. **Habilitar servicio SSH**<a name ="paso2"></a>


   2.1 Cuando hayamos seleccionado nuestro "ISO", CentOS iniciará y mostrará la terminal del Sistema, por lo que utilizaremos comandos para seguir con el resto de las instalaciones. Primero revisaremos el nombre y estado de nuestra interfaz de red, utilizando el comando `ip a`:
    
          # ip a
     
<p align="center">
<img src="https://github.com/FcoGzlz/TIHI07-2019/blob/master/SSH/Buscar%20Interfaz.PNG"/>
</p>

   2.2 Esto nos permitirá saber el nombre de nuestra interfaz el cual es estandarizado, por lo que nos fijaremos en el número "2", luego utilizaremos el comando `ifup "nombre de la interfaz"`para levantar la interfaz, como el nombre de nuestra interfaz resultó ser **enp0s3**, el comando queda: 
   
          # ifup enp0s3
          
  <p align="center">
        <img src="https://github.com/FcoGzlz/TIHI07-2019/blob/master/SSH/Levanar%20interfaz.PNG"/>
    </p>
          
   2.3 Una vez levantada la interfaz, instalaremos el servicio **SSH**, este nos permitirá conectarnos de manera remota a nuestra máquina, para ello utlizaremos el comando:
   
          # yum -y install openssh-server openssh-clients
          
   2.4 Para que el servicio inicie con el sistema, utilizaremos el comando:
   
          # chkconfig sshd on
          
   2.5 Para continuar, reiniciaremos el servicio:
   
          # service sshd restart
   
   2.6 Ahora descargaremos el software **Putty**, que nos permite conectarnos a nuestra maquina virtual desde nuestro Windows, mediante este link: (https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html)
   
   <p align="center">
<img src="https://github.com/FcoGzlz/TIHI07-2019/blob/master/SSH/Putty%20Installer.PNG"/>
</p>
   
   2.7 Una vez descargado, lo instalaremos; esta instalación es bastante sencilla, por lo que dejaremos los valores por defecto al instalar y solo presionaremos **Siguiente**.
   
<p align="center">
   <img src="https://github.com/FcoGzlz/TIHI07-2019/blob/master/Mauina%20Virutal%20y%20PUTTY/PuttyInstall.PNG" width="250px" height="200px"/> <img src="https://github.com/FcoGzlz/TIHI07-2019/blob/master/Mauina%20Virutal%20y%20PUTTY/PuttyInstall2.PNG" width="250px" height="200px"/>
</p>
   
<p align="center">
   <img src="https://github.com/FcoGzlz/TIHI07-2019/blob/master/Mauina%20Virutal%20y%20PUTTY/PuttyInstall3.PNG" width="250px" height="200px"/> <img src="https://github.com/FcoGzlz/TIHI07-2019/blob/master/Mauina%20Virutal%20y%20PUTTY/PuttyInstall4.PNG" width="250px" height="200px"/>
</p>
   
   2.8 Para usar el software, necesitaremos realizar una configuración de puertos en nuestra máquina, conocida como **Port Forward**, para ello,
   
   * Suspenderemos nuestra máquina virtual.
   * Una vez detenida la máquina, presionaremos **configuración**.
   * Dentro del apartado de **Configuración** seleccionaremos donde dice **Red**. 
   * Una vez allí, buscaremos la opción que dice **Conectado a** y lo cambiaremos por la opción **NAT**. 
   * Para continuar, pincharemos donde dice **Avanzadas**.
   
   <p align="center">
   <img src="https://raw.githubusercontent.com/FcoGzlz/TIHI07-2019/master/PORTFORWARD/Configuracion%20red.PNG"/>
    </p>  
    
   2.9 Al presionar la opción **Avanzadas** se deslpliegarán más opciones de configuración, pincharemos en la opción **Reenvío de puertos**, luego de acceder a esta opción, aparecerá un recuadro en blanco; daremos click derecho en el cuadro y presionaremos donde dice **Agregar nueva regla**. Una vez realizado esto, procederemos a completar los datos:
   
   * **Nombre:** Este será el nombre de nuestro reenvío de puertos, puede ser cualquiera.
   * **Protocolo:** Este es el protocolo de transferencia, por lo que pondremos **TCP**
   * **IP anfitrión:** Debe ir la ip de nuestro ordenador, pondremos la dirección **127.0.0.1** ya que esta sirve a modo de loop y siempre apuntará a la nuestra.
   * **Puerto anfitrión** Pondremos el puerto **8001** ya que no está siendo ocupado. 
   * **IP Invitado:** Colocaremos la **IP de nuestra máquina virtual** (la cual pudimos saber al utilizar el comando `ip a` en el primer paso del punto 2).
   * **Puerto invitado:** Colocaremos el puerto **22**.

       Una vez configurados los campos, presionaremos la opción **Aceptar** tanto en la ventana de reenvío de puertos, como en la  de configuración.
    
<p align ="center">
<img src="https://raw.githubusercontent.com/FcoGzlz/TIHI07-2019/master/PORTFORWARD/Rennvio%20de%20puertos.PNG"/>
</p>

   2.10 Una vez iniciada nuestra máquina virtual, abriremos el software **Putty** descargado anteriormente (es importante recordar que este paso se realiza en el ambiente de escritorio de nuestro ordenador, no en la máquina virtual). Al abrirlo, colocaremos los siguientes datos (estos datos serán llenados basándonos el los que pusimos en el "Port Forward" realizado en el paso anterior):
   
* **Host name:** colocaremos la ip de anfitrión, es decir, **127.0.0.1**.
* **Puerto:** colocaremos el puerto de anfitrión, el cual es **8001**. 
* **Connection type:** Este parámetro es importante ya que dictará el método de conexión, por lo que seleccionaremos la opción **SSH**.

Una vez completados los datos, presionaremos donde dice **Open**.

   <p align="center">
   <img src="https://raw.githubusercontent.com/FcoGzlz/TIHI07-2019/master/PORTFORWARD/Puttyconfiguracion.PNG"/>
   </p>
   
   2.11 Al momento de presionar **Open**, se conectará a nuestra máquina virtual, por lo que nos pidirán nuestro usuario y contraseña. Una vez ingresados, podemos operar nuestra máquina virtual a través del software **Putty**, por lo que no habrá necesidad de ir directamente a la máquina virtual, sino que basta conque esta esté operando.
   
   <p align="center">
        <img src="https://github.com/FcoGzlz/TIHI07-2019/blob/master/SSH/Putty.PNG"/>
    </p>
   
   
3. **Instalación de Java Oracle en CentOS7**<a name = "paso3"></a>

   3.1 Para instalar Joava Oracle en CentOS, primero instalaremos *OpenJDK 8*, ara ello, utilizaremos el siguiente comando (durante la instalación, aparecerán opciones de confirmación, por lo que presionaremos la tecla `y` y luego `Enter` para confirmar):
   
        # yum install java-1.8.0-openjdk-devel
   
   3.2 Una vez completado el paso anterior, procederemos a instalar **Java Oracle 8 JDK**, para lo cual iremos a la página de Oracle, utilizando el siguiente link: (https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html), de igual manera, copiaremos el anterior link para utilizarlo en el comando `wget --no-cookies --no-check-certificate --header "Cookie: gpw_e24=http%3A%2F%2Fwww.oracle.com%2F; oraclelicense=accept-securebackup-cookie" "EN ESTA SECCIÓN DEBE IR EL LINK"`, hecho esto introduciremos los siguientes comandos (recuerda poner el link de la página en el segundo comando):
        
        # cd ~
        # wget --no-cookies --no-check-certificate --header "Cookie: gpw_e24=http%3A%2F%2Fwww.oracle.com%2F; oraclelicense=accept-securebackup-cookie" "https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html"
   
   3.3 Una vez completado el paso anterior, iremos nuevamente a la página de Oracle mediante el link utilizado en el paso anterior: (https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html). Una vez ahí, ubicaremos donde diga **Java SE Development Kit 8u211**:
   
   <p align="center">
        <img src="https://raw.githubusercontent.com/FcoGzlz/TIHI07-2019/master/Oracle/Oracle.PNG"/>
    </p>
   
   3.4 Debemos asegurarnos de que está marcada la opción **Accept License Agreement**, luego buscaremos el archivo **Linux x64**, debemos tener precaución de **elegir el que tenga la extención ".rpm"**.
   
   <p align="center">
        <img src="https://raw.githubusercontent.com/FcoGzlz/TIHI07-2019/master/Oracle/OracleN.PNG"/>
    </p>
    
   3.5 Una vez encontrado el archivo, daremos lcick derecho en donde dice **jdk-8u211-linux-x64.rpm** y seleccionaremos **Copiar ubicación del enlace**.
   
    <p align="center">
        <img src="https://github.com/FcoGzlz/TIHI07-2019/blob/master/Oracle/OracleCopiarLink2.png"/>
    </p>
    
   3.6 Por último, utilizaremos el siguiente comando para instalar **JDK 8** `yum localinstall "AQUÍ VA EL LINK COPIADO EN EL PASO ANTERIOR"` (recuerda utilizar el link copiado en el aso anterior), en nuestro caso el comando queda así:
   
        # yum localinstall https://download.oracle.com/otn/java/jdk/8u211-b12/478a62b7d4e34b78b671c754eaaf38ab/jdk-8u211-linux-x64.rpm
    
    
4. **Instalar de ambiente grádico Gnome**<a name = "paso4"></a>

   4.1 Para su instalación, ejecutaremos el siguiente comando en nuestra terminal:
   
        # yum -y groups install "GNOME Desktop"
    
   4.2 Una vez terminada la descarga e instalación, introduciremos el comando `startx` (este comando se deberá intrducir cada vez que se inicie la máquina):
   
        # startx
        
   4.3 GNOME Desktop Environment iniciara. En el primer encendido, se ejecutara la configuracion inicial en la que deberás:
  
   * Selecciona el idioma del sistema.
   * Selecciona la entrada de tu teclado.
   * Si quieres puedes colocar una cuenta (Funciona sin cuenta)
   * Finalmente le damos click a "Start using CentOS Linux"
   
   4.4 El ambiente gráfico se verá como en la siguiente imágen:
   
    <p align="center">
        <img src="https://github.com/FcoGzlz/TIHI07-2019/blob/master/Gnome/Gnome.PNG"/>
    </p>
 
   4.5 Si se quiere cambiar la resoución del escritorio de Gnome:
   
   * Haga click en el apartado **Aplicaciones** que se encuentra en la parte superior izquierda.
   * Luego dirijase al apartado **Herramientas del sistema**.
   * Dentro de este apartado, haga cick en la opción **Configuración**.
   * Una vez dentro de las configuraciones, acceda al apartado **Dispositivos**, el cual es el penúltimo de la lista.
   * Finalmente, haga click donde dice **Resolución** y seleccionae la que más le acomode.
   
   <p align="center">
        <img src="https://github.com/FcoGzlz/TIHI07-2019/blob/master/Gnome/GnomeConfig.PNG"/>
        <img src="https://github.com/FcoGzlz/TIHI07-2019/blob/master/Gnome/GnomeDispsitivos.PNG"/>
        <img src="https://github.com/FcoGzlz/TIHI07-2019/blob/master/Gnome/GnomeResolucion.PNG"/>
    </p>
 
 5. **Instalación de IDE (en este caso se instaló NetBeans)** <a name = "paso5"></a>
    5.1 Por recomendación, ejecutaremos el ambiente gráfico que instalamos en el cuarto paso. Esto debido a que NetBeans se instalará mediante una **ventana de instalación**, para esto, utilizaremos el siguiente comando:
    
        # startx 
        
    5.2 Una vez estemos en el ambiente gráfico, arbiremos una terminal (click derecho en el escritrio y **abrir terminal**), luego verificaremos la versión de Java, la cual se instaló en el tercer paso de esta guía:
    
        # java -version
        
    5.3 Una vez verifiada la versión de java, la cual debería ser la 8, procederemos a descargar NetBeans:
    
        # wget http://download.netbeans.org/netbeans/8.0.1/final/bundles/netbeans-8.0.1-linux.sh
        
    5.4 Ahora crearemos un **package** para poder ejecutarlo:
    
        # chmod 700 netbeans-8.0.1-linux.sh
        
    5.5 Una vez creado el **package**, lo ejecutaremos:
    
        # ./netbeans-8.0.1-linux.sh
        
    5.6 Una vez introducido el comando anterior, se desplegará el instalador de **NetBeans**, presionaremos **Next**:
    
    <p align="center">
        <img src="https://raw.githubusercontent.com/FcoGzlz/TIHI07-2019/master/NetBeans/NetBeans.jpg"/>
    </p>
     
    5.7 Las siguientes dos ventanas, son las confirmaciones de licencia, por lo que seleccionaremos **I accept the terms in the license agreement** y presionaremos **Next** (repetiremos este proceso en las dos vetnanas de licencia):
    
    <p align="center">
        <img src="https://raw.githubusercontent.com/FcoGzlz/TIHI07-2019/master/NetBeans/NetBeansLicencia1.jpg"/>
        <img src="https://raw.githubusercontent.com/FcoGzlz/TIHI07-2019/master/NetBeans/NetBeansLicencia2.jpg"/>
    </p>
    
    5.8 Lo siguiente es seleccionar la versión de **JDK** a utilizar, por lo que seleccionremos la que aparece en la imágen, en caso de que no salga esta versión, podemos seleccionar la que en su nombre incluya la palabra **default**, luego de seleccionar, presionaremos **Next**:
    
    <p align="center">
        <img src="https://raw.githubusercontent.com/FcoGzlz/TIHI07-2019/master/NetBeans/NetBeansJava.jpg"/>
    </p>
    
    5.8 A continuación, se instala el servidor **GlassFish**, por lo que no cambiaremos nada, solamente presionaremos **Next**:
    
    <p align="center">
        <img src="https://raw.githubusercontent.com/FcoGzlz/TIHI07-2019/master/NetBeans/NetBeansGlassfish.jpg"/>
    </p>
    
    5.9 Luego se mostrará la ventana de **buscar actualizaciones**, esto es a libre elección, ya que no influirá en la instalación de **NetBeans**, para continuar, presionaremos **Install**:
    
    <p align="center">
        <img src="https://raw.githubusercontent.com/FcoGzlz/TIHI07-2019/master/NetBeans/NetBeansUpdates.jpg"/>
    </p>
    
    5.9 Una vez se haya completado la instalacióm, nos aparecerá una última ventana, la cual nos pedirá si deseamos contribuir con información, esto es irrelevante, por lo que queda a libre elección, para terminar, presionaremos **Finish**:
    
    <p align="center">
        <img src="https://raw.githubusercontent.com/FcoGzlz/TIHI07-2019/master/NetBeans/NetBeansContribute.jpg"/>
    </p>
    
 6. **Instalar Postgre SQL versión 9.6 o superior** <a name = "paso6"></a>
 
    6.1 Para comenzar, añadiremos el repositorio de **Postgre SQL 9.6** ya que en los repositorios oficiales, va en una versión anterior, para ello, ejecutaremos el comando:
    
        # yum install  https://download.postgresql.org/pub/repos/yum/9.6/redhat/rhel-7-x86_64/pgdg-redhat96-9.6-3.noarch.rpm -y
        
    6.2 Una vez agregado el repositorio, instalremos **Postgre SQL 9.6**, para lo cual utilizaremos el siguiente comando:
    
        # yum install postgresql96 postgresql96-server postgresql96-contrib postgresql96-libs -y
        
    6.3 Una vez instalado, lo inicializaremos, para ello utilizamos:
       
        # /usr/pgsql-9.6/bin/postgresql96-setup initdb
        
    6.4 Activaremos **Postgree** para que inicie con el sistema, para ello utilizaremos los siguientes comandos:
    
        # systemctl enable postgresql-9.6.service
        # systemctl start postgresql-9.6.service
        
    6.5 Ahora configuraremos **Postgre** para permitir las conexiones remotas, para ello, ejecutaremos el siguiente comando, con el cual buscaremos el archivo a configurar:
    
        # cd /var/lib/pgsql/9.6/data
       
    6.6 Una vez en este directorio, utilizaremos el comando `ls`, que nos permite leer los archivos, y a continuación utilizaremos un editor de texto (en este caso se utilizó el editor nano) para modificar el archivo **postgresql.conf**:
    
        # ls
        # nano postgresql.conf
 
    <p align="center">
        <img src="https://raw.githubusercontent.com/FcoGzlz/TIHI07-2019/master/PostgreConf/PostgreConf.PNG"/>
    </p>
    
    
    6.7 Una vez abierto el archivo, buscaremos la línea que diga **#listen_address** y cambiaremos su valor por `*`, nos quedaría así:
    
     <p align="center">
        <img src="https://raw.githubusercontent.com/FcoGzlz/TIHI07-2019/master/PostgreConf/PostgreConf2.PNG"/>
    </p>
    
    6.8 Una vez completado, guardaremos el los cambios presionando **Ctrl + O**, una vez guardados los cambios, saldremos del editor, presionando **Ctrl + X**, y reiniciaremos el servicio con el comando:
    
        # systemctl restart postgresql-9.6
        
    6.9 Ahora crearemos un **usuario Postgre**, para ello utlizaremos el comando:
    
        # su postgres
        
    6.10 Una vez ingresado el comando, introduciremos lo siguiente:
    
        # psql
        
    6.11 Cuando hayamos entrado al ambiente Postgre, crearemos un usuario con la syntaxis `create user "nombre de usuario" with password "contraseña del usuario";`:
    
        # create user inacap with password "123456";
        
    6.12 Para agregarle permisos de superusuario al usuario que hemos creado, intoduciremos la syntaxis `alter user "nombre de usuario" superuser";`:
    
        # alter user inacap superuser;
        
    6.13 Ahora crearemos una Base de Datos, para ello utilizaremos la syntaxis `create database "nombre de la base de datos";`:
    
        # create database inacap;
        
    6.14 Por último, le daremos acceso a nuestro usuario a la Base de Datos que hemos creado con la syntaxis `grant all on database "nombre de la Base de Datos" to "nombre del usuario";`:
    
        # grant all on database inacap to inacap;
        
    6.15 Ya tenemos un usuario y Base de Datos creados, para salir del ambiente postgre, presione **Ctrl + D**
    
    
7. **Ejecutar pruebas de conexión** <a name = "paso7"></a>

   
   
  
