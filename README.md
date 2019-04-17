# TIHI07-2019
### **Introducción**
Esta es una guía en la cual se explicarán los pasos a seguir para la puesta en marcha de una "WorkStation". Para esto, nos guiaremos por la siguiente lista, la cual mostrará los cada uno de los puntos a seguir, luego se detallarà una guìa paso a paso, lac ual cubrirá todos los puntos en la lista:
1. **Instalar en Visrtual Box el Sistema Operativo CentOS o Ubuntu (en este caso se utilizó CentOS 7,3 minimal).**
2. **Conectarse a la máquina virtual mediante el servidor ssh**.
3. **Desinstalar la versión de Java que viene por defecto en el Sistema e instalar Java de Oracle.**
4. **Instalar un ambiente gráfico (en este caso se utilizó Gnome).**
5. **Instalar un IDE (en este caso se instaló NetBeans).**
6. **Instalar Postgre SQL versión 9.6 o superioir.**
7. **Crear un test Java para comprobar la conexión de la Base de Datos.**
--------------------------------------------------------------------------------------------------------------------------------

1. Hola como estas

2. **Habilitar servidor SSH para conectarse a la máquina virtual**
   * Primero levantaremos la interfaz ip de nuestro centOS, para ello en la terminal, insertaremos el comando `ip a`:
    
          # ip a
   * Esto nos permitirá saber el nombre de nuestra interfaz el cual es estandarizado, por lo que nos fijaremos en el número 2 que en nuestro caso resultó llamarse *"enp0s3"*, luego utilizaremos el comando `ifup`: 
   
          # ifup enp0s3
          
   * Una vez levantada la interfaz, habilitaremos el serivicio **SSH**.
   
          # yum -y install openssh-server openssh-clients
          
   * Lo habilitamos para que inicie con el sistema cada vez que apaguemos y encendamos.
   
          # chkconfig sshd on
          
   * Riniciamos SSHD
   
          # service sshd restart
   
   * Ahora descargaremos el programa **PUTTY**, para poder conectarnos a nuestra maquina virtual desde nuestro Windows, mediante este link: (https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html)
   
   
   Tratamos de colocar una foto: 
