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
--------------------------------------------------------------------------------------------------------------------------------

1. **Instalacion de CentOS en Máquina Virtual.**<a name ="paso1"></a>

    1.1	Para comenzar descargaremos el software para la virtualización del S.O CentOS en nuestro ordenador, utilizando el             siguiente link: (https://www.virtualbox.org/wiki/Downloads) y seleccionaremos el que corresponda a nuestro sistema.

    1.2 Una vez descargado el programa, lo instalaremos.
   
   <p align="center">
        <img src="https://raw.githubusercontent.com/FcoGzlz/TIHI07-2019/master/Mauina%20Virutal%20y%20PUTTY/VB1.PNG"/>
    </p>

    1.3 Ya instalado el software, procederemos a descargar CentOS 7 minimal, para lo cual nos dirigiremos a: (https://www.centos.org/download/). Seleccionaremos la versión minimal.
   
   <img src="https://user-images.githubusercontent.com/48935510/56478835-f543db80-647f-11e9-927f-6b3dfda776de.jpg" width="900px" height="200px"/>


    1.4 Una vez descargados ambos programas, abriremos el VirtualBox y crearemos una máquina nueva.
   
   ![1 4](https://user-images.githubusercontent.com/48935510/56480397-e6f9bd80-6487-11e9-80c9-cfb8980e648c.jpg)
   
   1.5 En las opciones para la creación, en el apartado **Tipo** seleccionaremos "Linux", en **Versión** seleccionaremos "otros", para **Nombre** es libre elección, en cuanto a **Carpeta de maquina** se recomienda dejar el destino por defecto, aunque se puede cambiar si asi se deasea.

   1.6 Una vez configurada la máquina, presionaremos el botón “iniciar”, y seleccionaremos nuestro CentOS antes descargado.



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
          
   2.3 Una vez levantada la interfaz, instalaremos el serivicio **SSH**, este nos permitirá conectarnos de manera remota a nuestra máquina, para ello utlizaremos el comando:
   
          # yum -y install openssh-server openssh-clients
          
   2.4 Para que el servicio inicie con el sistema, utilizaremos el comando:
   
          # chkconfig sshd on
          
   2.5 Para continuar, reiniciaremos el servicio:
   
          # service sshd restart
   
   2.6 Ahora descargaremos el software **PUTTY**, que nos permite conectarnos a nuestra maquina virtual desde nuestro Windows, mediante este link: (https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html)
   
   <p align="center">
<img src="https://github.com/FcoGzlz/TIHI07-2019/blob/master/SSH/Putty%20Installer.PNG"/>
</p>
   
   2.7 Una vez descargado, lo instalaremos; esta instalación es bastante sencilla, por lo que dejaremos los valores por defecto al instalar y solo presionaremos "siguiente.
   
<p align="center">
   <img src="https://github.com/FcoGzlz/TIHI07-2019/blob/master/Mauina%20Virutal%20y%20PUTTY/PuttyInstall.PNG" width="250px" height="200px"/> <img src="https://github.com/FcoGzlz/TIHI07-2019/blob/master/Mauina%20Virutal%20y%20PUTTY/PuttyInstall2.PNG" width="250px" height="200px"/>
</p>
   
<p align="center">
   <img src="https://github.com/FcoGzlz/TIHI07-2019/blob/master/Mauina%20Virutal%20y%20PUTTY/PuttyInstall3.PNG" width="250px" height="200px"/> <img src="https://github.com/FcoGzlz/TIHI07-2019/blob/master/Mauina%20Virutal%20y%20PUTTY/PuttyInstall4.PNG" width="250px" height="200px"/>
</p>
   
   
   
   2.8 Para usar el software, necesitaremos realizar una configuración de puertos en nuestra máquina, conocida como "Port Forward", para ello, suspenderemos nuestra máquina virtual, y daremos click derecho en nuestra máquina y seleccionaremos "configuración". Una vez en la pestaña "configuración", presionaremos en el apartado **Red**, una vez allí, buscaremos la opción que dice **Conectado a** y lo cambiaremos por la opción **Nat**, para continuar, pincharemos donde dice **Avanzadas**
   
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

Una vez comfigurados los campos, presionaremos la opción **Aceptar** tanto en la ventana de reenvío de puertos, como en la de configuración.
    
<p align ="center">
<img src="https://raw.githubusercontent.com/FcoGzlz/TIHI07-2019/master/PORTFORWARD/Rennvio%20de%20puertos.PNG"/>
</p>
   2.10 Una vez iniciada nuestra máquina virtual, abriremos el software **Putty** descargado anteriormente (es importante recordar que este paso se realiza en el ambiente de escritorio de nuestro ordenador, no en la máquina virtual). Al abrirlo, colocaremos los siguientes datos (estos datos serán llenados basándonos el los que pusimos en el "Port Forward" realizado en el paso anterior):
* **Host name:** colocaremos la ip de anfitrión, es decir, **127.0.0.1**.
* **Puerto:** colocaremos el puerto de anfitrión, el cual es **8001**. 
* **Connection type:** Este parámetro es importante ya que dictará el método de conexión, por lo que seleccionaremos la opción **SSH**.

Una vez completados los datos, presionaremos donde dice **Open**.
    
   <img src="https://raw.githubusercontent.com/FcoGzlz/TIHI07-2019/master/PORTFORWARD/Puttyconfiguracion.PNG" width="500" height="450"/>
   
   2.11 Al momento de presionar **Open**, se conectará a nuestra máquina virtual, por lo que nos pidirán nuestro usuario y contraseña. Una vez ingresados, podemos operar nuestra máquina virtual a través del software **Putty**, por lo que no habrá necesidad de ir directamente a la máquina virtual, sino que basta conque esta esté operando.
   
3. **Instalación de Java Oracle en CentOS7**<a name = "paso3"></a>

   3.1 EN PROCESO....
   
4. **Instalar de ambiente grádico Gnome**<a name = "paso4"></a>

   4.1 Para su instalación, ejecutremos el siguiente comando en nuestra terminal:
   
        # yum -y groups install "GNOME Desktop"
    
   4.2 Una vez terminada la descarga e instalación, introduciremos el comando `startx` (este comando se deberá intrducir cada vez que se inicie la máquina):
   
        # startx
        
   4.3 GNOME Desktop Environment iniciara. En el primer encendido, se ejecutara la configuracion inicial en laque deberás:
  
   * Selecciona el idioma del sistema.
   * Selecciona la entrada de tu teclado.
   * Si quieres puedes colocar una cuenta (Funciona sin cuenta)
   * Finalmente le damos click a "Start using CentOS Linux"
   
   4.4 El ambiente gráfico se verá como en la siguiente imágen:
 
   4.5 Si la resolucion del escritorio es baja, debes ir a configuracion/dispositivos/ .....
 
 5. **Instalar un IDE (en este caso se instaló NetBeans)** <a name = "paso5"></a>
    5.1 En Proceso, mas que eso, recibe un hueso .-.
    
 6. **Instalar Postgre SQL versión 9.6 o superior** <a name = "paso6"></a>
    6.1 añadimos el repositorio PostgreSQL 9.6
    
        # yum install  https://download.postgresql.org/pub/repos/yum/9.6/redhat/rhel-7-x86_64/pgdg-redhat96-9.6-3.noarch.rpm -y
        
    6.2 instalamos PostgreSQL 9.6
    
        # yum install postgresql96 postgresql96-server postgresql96-contrib postgresql96-libs -y
        
    6.3 ejecutar PostgreSQL 
    
       *inicializamos PostgreSQL
       
        # /usr/pgsql-9.6/bin/postgresql96-setup initdb
        
       *habilitamos PostgreSQL
 
  
    

   
   
  
