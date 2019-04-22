# TIHI07-2019
### **Introducción**
Esta es una guía en la cual se explicarán los pasos a seguir para la puesta en marcha de una "WorkStation". Para esto, nos guiaremos por la siguiente lista, la cual mostrará los cada uno de los puntos a seguir, luego se detallarà una guìa paso a paso, lac ual cubrirá todos los puntos en la lista:
1. [**Instalar en Visrtual Box el Sistema Operativo CentOS o Ubuntu (en este caso se utilizó CentOS 7,3 minimal)**](#paso1)
2. [**Conectarse a la máquina virtual mediante el servidor ssh**](#paso2)
3. [**Desinstalar la versión de Java que viene por defecto en el Sistema e instalar Java de Oracle**](#paso3)
4. [**Instalar un ambiente gráfico (en este caso se utilizó Gnome)**](#paso4)
5. [**Instalar un IDE (en este caso se instaló NetBeans)**](#paso5)
6. [**Instalar Postgre SQL versión 9.6 o superioir**](#paso6)
7. [**Crear un test Java para comprobar la conexión de la Base de Datos**](#paso7)
--------------------------------------------------------------------------------------------------------------------------------

1. **Instalacion de CentOS en Máquina Virtual.**<a name ="paso1"></a>

   1.1	Para comenzar descargaremos el software para la virtualización del S.O CentOS en nuestro ordenador, utilizando el siguiente link: (https://www.virtualbox.org/wiki/Downloads) y seleccionaremos el que corresponda a nuestro sistema.

   1.2 Una vez descargado el programa, lo instalaremos.

   1.3 Ya instalado el software, procederemos a descargar CentOS 7 minimal, para lo cual utilizaremos nos dirigiremos a: (https://www.centos.org/download/). Seleccionaremos la versión minimal.

   ![1 1](https://user-images.githubusercontent.com/48935510/56478835-f543db80-647f-11e9-927f-6b3dfda776de.jpg)

   1.4 Una vez descargados ambos programas, abriremos el VirtualBox y crearemos una máquina nueva.
   
   ![1 4](https://user-images.githubusercontent.com/48935510/56480397-e6f9bd80-6487-11e9-80c9-cfb8980e648c.jpg)
   
   1.5 En las opciones para la creación, seleccionaremos “otros” en el apartado “tipo de sistema”, seleccionaremos el tamaño de disco y la memoria RAM (es recomendable 1GB para no entorpecer el rendimiento de nuestro PC)

   1.6 Una vez configurada la máquina, presionaremos el botón “iniciar”, y seleccionaremos nuestro CentOS antes descargado.



2. **Habilitar servidor SSH para conectarse a la máquina virtual**<a name ="paso2"></a>

   2.1 Primero levantaremos la interfaz ip de nuestro centOS, para ello en la terminal, insertaremos el comando `ip a`:
    
          # ip a
   2.2 Esto nos permitirá saber el nombre de nuestra interfaz el cual es estandarizado, por lo que nos fijaremos en el número 2 que en nuestro caso resultó llamarse *"enp0s3"*, luego utilizaremos el comando `ifup`: 
   
          # ifup enp0s3
          
   2.3 Una vez levantada la interfaz, habilitaremos el serivicio **SSH**.
   
          # yum -y install openssh-server openssh-clients
          
   2.4 Lo habilitamos para que inicie con el sistema cada vez que apaguemos y encendamos.
   
          # chkconfig sshd on
          
   2.5 Riniciamos SSHD
   
          # service sshd restart
   
   2.6 Ahora descargaremos el programa **PUTTY**, para poder conectarnos a nuestra maquina virtual desde nuestro Windows, mediante este link: (https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html)
   
   
   Tratamos de colocar una foto: 
