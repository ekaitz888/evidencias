### Virtual host

Para empezar esta evidencia, iremos a *inbound* em *launch-wizard-3* y le vamos a meter otro puerto, en este caso el puerto 21.

![inbound](../capturas/inbound.PNG)

Le daremos al botón de *edit* y posteriormente al de *add rules*.

![servicio](../capturas/servicio.PNG)

Una vez hecho esto, abriremos nuestro cmd y ahí instalaremos en nuestra máquina virtual el programa vsftpd

![vsftpd](../capturas/vsftpd.PNG)

Tras instalarlo, crearemos un usuario con su respectiva contraseña para cada subdominio utilizando el comando useradd y passwd

![useradd](../capturas/useradd.PNG)

![passwd](../capturas/passwd.PNG)

Ya creado los usuarios, iremos al archivo *vsftpd.conf* para borrar y editar unas cuantas líneas

![vsftpdConf](../capturas/vsftpd.conf.PNG)

Hasta que te quede así

![archivo](../capturas/archivo.PNG)

Y después de todo esto, reiniciamos el ftpd

![ftpd](../capturas/ftpdRestart.PNG)

Por último dejamos el terminal para volver a nuestro ordenador para abrir la aplicación WINSCP para poder conectarlo con la máquina virtual.

![winscp](../capturas/winscp.PNG)

Una vez iniciada la sesión, iremos al apartado de *avanzado* y le daremos en *conexión para desactivar el modo pasivo.

![pasivo](../capturas/pasivo.PNG)

Finalmente, si le damos a conectar debería de salirnos nuestras carpetas 

![conexion](../capturas/aws-conexion.PNG)