# TIHI07-2019
### **Introducción**
Esta es una guía en la cual se explicarán los pasos a seguir para la puesta en marcha de una "WorkStation". Para esto, nos guiaremos por la siguiente lista, la cual mostrará los cada uno de los puntos a seguir, luego se detallarà una guìa paso a paso, lac ual cubrirá todos los puntos en la lista:
1. [**Instalar en Visrtual Box el Sistema Operativo CentOS o Ubuntu (en este caso se utilizó CentOS 7,3 minimal)**](#paso1)
2. [**Conectarse a la máquina virtual mediante el servicio SSH**](#paso2)
3. [**Desinstalar la versión de Java que viene por defecto en el Sistema e instalar Java de Oracle**](#paso3)
4. [**Instalar un ambiente gráfico (en este caso se utilizó Gnome)**](#paso4)
5. [**Instalar un IDE (en este caso se instaló NetBeans)**](#paso5)
6. [**Instalar Postgre SQL versión 9.6 o superioir**](#paso6)
7. [**Crear un test Java para comprobar la conexión de la Base de Datos**](#paso7)
--------------------------------------------------------------------------------------------------------------------------------

1. **Instalacion de CentOS en Máquina Virtual.**<a name ="paso1"></a>

   1.1	Para comenzar descargaremos el software para la virtualización del S.O CentOS en nuestro ordenador, utilizando el siguiente link: (https://www.virtualbox.org/wiki/Downloads) y seleccionaremos el que corresponda a nuestro sistema.

   1.2 Una vez descargado el programa, lo instalaremos.
   ![VB Installer](https://raw.githubusercontent.com/FcoGzlz/TIHI07-2019/master/Mauina%20Virutal%20y%20PUTTY/VB1.PNG)

   1.3 Ya instalado el software, procederemos a descargar CentOS 7 minimal, para lo cual nos dirigiremos a: (https://www.centos.org/download/). Seleccionaremos la versión minimal.
   
   <img src="https://user-images.githubusercontent.com/48935510/56478835-f543db80-647f-11e9-927f-6b3dfda776de.jpg" width="900px" height="200px"/>


   1.4 Una vez descargados ambos programas, abriremos el VirtualBox y crearemos una máquina nueva.
   
   ![1 4](https://user-images.githubusercontent.com/48935510/56480397-e6f9bd80-6487-11e9-80c9-cfb8980e648c.jpg)
   
   1.5 En las opciones para la creación, en el apartado **Tipo** seleccionaremos "Linux", en **Versión** seleccionaremos "otros", para **Nombre** es libre elección, en cuanto a **Carpeta de maquina** se recomienda dejar el destino por defecto, aunque se puede cambiar si asi se deasea.

   1.6 Una vez configurada la máquina, presionaremos el botón “iniciar”, y seleccionaremos nuestro CentOS antes descargado.



2. **Habilitar servicio SSH**<a name ="paso2"></a>

   2.1 Cuando hayamos seleccionado nuestro "ISO", CentOS iniciará y mostrará la terminal del Sistema, por lo que utilizaremos comandos para seguir con el resto de las instalaciones. Primero revisaremos el nombre y estado de nuestra interfaz de red, utilizando el comando `ip a`:
    
          # ip a
   2.2 Esto nos permitirá saber el nombre de nuestra interfaz el cual es estandarizado, por lo que nos fijaremos en el número 2 que en nuestro caso resultó llamarse *"enp0s3"*, luego utilizaremos el comando `ifup`para levantar la interfaz: 
   
          # ifup enp0s3
          
   2.3 Una vez levantada la interfaz, instalaremos el serivicio **SSH**, este nos permitirá conectarnos de manera remota a nuestra máquina, para ello utlizaremos este comando:
   
          # yum -y install openssh-server openssh-clients
          
   2.4 Para que el servicio inicie con el sistema, utilizaremos el comando:
   
          # chkconfig sshd on
          
   2.5 Para continuar, reiniciaremos el servicio:
   
          # service sshd restart
   
   2.6 Ahora descargaremos el software **PUTTY**, que nos permite conectarnos a nuestra maquina virtual desde nuestro Windows, mediante este link: (https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html)
   
   2.7 Una vez descargado, lo instalaremos; esta instalación es bastante sencilla, por lo que dejaremos los valores por defecto al instalar y solo presionaremos "siguiente.
   
   <img src="https://github.com/FcoGzlz/TIHI07-2019/blob/master/Mauina%20Virutal%20y%20PUTTY/PuttyInstall.PNG" width="250px" height="200px"/> <img src="https://github.com/FcoGzlz/TIHI07-2019/blob/master/Mauina%20Virutal%20y%20PUTTY/PuttyInstall2.PNG" width="250px" height="200px"/>
   
   <img src="https://github.com/FcoGzlz/TIHI07-2019/blob/master/Mauina%20Virutal%20y%20PUTTY/PuttyInstall3.PNG" width="250px" height="200px"/> <img src="https://github.com/FcoGzlz/TIHI07-2019/blob/master/Mauina%20Virutal%20y%20PUTTY/PuttyInstall4.PNG" width="250px" height="200px"/>
   
   
   
   
   2.8 Para usar el software, necesitaremos realizar una configuración de puertos en nuestra máquina, conocida como "Port Forward", para ello, suspenderemos nuestra máquina virtual, y daremos click derecho en nuestra máquina y seleccionaremos "configuración"
   
   2.9 Una vez en la pestaña "configuración", presionaremos en el apartado **Red**, una vez allí, buscaremos la opción que dice **Conectado a** y lo cambiaremos por la opción **Nat** si esque no lo está, para continuar, pincharemos donde dice **Avanzadas**
   
   
   <img src="https://raw.githubusercontent.com/FcoGzlz/TIHI07-2019/master/PORTFORWARD/Configuracion%20red.PNG" width="600" height="400"/>
      
    2.9 Al presionar la opción **Avanzadas** se deslpliegarán más opciones de configuración, pincharemos en la opción **Reenvío de puertos**, luego de acceder a esta opción, aparecerá un recuadro en blanco; daremos click derecho en el cuadro y presionaremos donde dice **Agregar nueva regla**. Una vez realizado esto, procederemos a rellenar los datos: en el parámetro **IP anfitrión**: debe ir la ip de nuestro ordenador, pondremos la dirección **127.0.0.1** ya que esta sirve a modo de loop y siempre apuntará a la nuestra. En el parámetro **Puerto anfitrión** pondremos el puerto **8001** ya que no está siendo ocupado. En **IP Invitado** colocaremos la **IP de nuestra máaquina virtual** (la cual pudimos saber al utilizar el comando `ip a` en el primer paso del punto 2). Finalmente en **Puerto invitado** colocaremos el puerto **22**. Una vez hehco esto, daremos en aceptar en ambas ventanas e iniciaremos nuevamente nuestra máquina virtual.
    
    <img src="https://raw.githubusercontent.com/FcoGzlz/TIHI07-2019/master/PORTFORWARD/Rennvio%20de%20puertos.PNG" width="600" height="400"/>
    
    2.10 Una vez iniciada nuestra máquina virtual, abriremos el software **Putty** descargado anteriormente. Al abrirlo, colocaremos los siguientes datos (estos datos se serán llenados basándonos el los que pusimos en el "Port Forward" realizado en el paso anterior: En **Host name** colocaremos la ip de anfitrión, es decir, **127.0.0.1**. En **Puerto** colocaremos el puerto de anfitrión, el cual es **8001*. Debemos asegurarnos que en el apartado **Connection type** que se encuantra bajos los anteriores parámetros, esté seleccionada la opción **SSH*.
    
    <img src="https://raw.githubusercontent.com/FcoGzlz/TIHI07-2019/master/PORTFORWARD/Puttyconfiguracion.PNG" width="600" height="400"/>

3. **Instalación de Java Oracle en CentOS7**<a name = "paso3"></a>
   
   
  
