# Servidor remoto

Para poder subir nuestros trabajos a internet, es necesario tener una máquina virtual que haga como servidor remoto de nuestro trabajo.

Para eso, hemos hecho una cuenta en [AWS](https://aws.amazon.com/es/education/awseducate/) (Amazon web services), ya que esta página nos da la posibilidad de crear todas las máquinas virtuales que querammos gratuitamente. Lo malo de esta forma gratuita, es que los servidores no pueden estar encendidos más de 750 horas (el equivalente a 31 días) por eso hay que apagar el servidor cada vez que dejemos de utilizarlo.

Trás este breve resumen, vamos a ver qué hay que hacer para poder ponerlo en funcionamiento:

### Paso 1: Conectarnos mediante nuestro terminal

Primero de todo, es crucial tener descargado el programa [Git](https://git-scm.com/downloads) para poder conectarnos al servidor remoto mediante su terminal, existen otros programas con los que podemos conectar pero no aseguramos que funcionen estos comandos en esos programas.

Vamos a necesitar localizar dónde está nuestra key. Es un archivo que tuvimos que haber descargado cuando creamos el servidor.

Una vez localizada la key, la haremos solo visible para nosotros.

![chmod](../capturas/chmod.PNG)

Hecho esto, es hora de conectarnos con el comando ssh.

(Tanto el nombre de la llave como el link de conexión del server los encontrarás en el botón "conect" en el apartado de "instances", para que el botón sea clickable tienes que encender el servidor)
![serverApagado](../capturas/serverApagado.PNG)


![serverEncendido](../capturas/serverEncendido.PNG)


![Connect](../capturas/connect.PNG)

Meteremos ese comando que sale en el ejemplo y ya estariamos dentro del servidor remoto

![ssh](../capturas/ssh.PNG)

### Paso 2: instalar apache2 en nuestro servidor

Antes de instalar apache tenemos que actualizar el servidor.

![update](../capturas/update.PNG)

Una vez actualizado lo instalaremos mediante el siguiente comando
![apache](../capturas/apache2.PNG)

Ya con el apache instalado tendremos que ir a AWS y en "description->security groups->launch-wizard-2." meteremos el HTTP y HTTPS para que podamos entrar mediante nuestros navegadores

![security](../capturas/security.PNG)

![inbound](../capturas/inbound.PNG)

Finalmente le damos a "add rule" y arriba nos saldrá un nuevo tipo que tendremos que hacerlo HTTP (como sale arriba) y otro para el HTTPS (aunque salgan dos solamente haz)

![AddRule](../capturas/AddRule.PNG)

Si lo hemos hecho perfectamente, al poner en "instances" deberíamos tener el "public DNS". Lo copiamos y pegamos en la barra de URL y nos saldrá esta página:

![pagina](../capturas/Página.PNG)

### Paso 3: Instalar MySQL

Ahora que nuestro servidor funciona perfectamente, vamos a instalaronos el siguiente programa "MySQL". Este programa nos ayudara a manejar las Bases de datos.

Empezaremos instalándolo con la función apt:

![mySql](../capturas/mysql-server.PNG)

Te saldrán paquetes para descargar, si le damos a "Y" se nos descargarán. Después de instalarlo empezaremos con la configuración del mySQL.

![mysql_secure_installation](../capturas/mysql_secure_installation.PNG)

Nos preguntará si queremos poner una contraseña para  Debes tener en cuenta que si digitas 2 representando el nivel más fuerte, recibirás errores al intentar utilizar una contraseña que no contenga números, letras mayúsculas y minúsculas, así como caracteres especiales; además la contraseña no podrá estar basada en palabras comunes en un diccionario.

### Paso 4: instalar PHP

Una vez instalada la base de datos, necesitaremos archivos para conectar con esas bases de datos que creamos, para eso instalaremos PHP de este modo:

![php](../capturas/php.PNG)

Todo lo demás, nos ayudará a configurarlo para que se ejecute sobre el servidor apache y que se comunique con la base de datos de mySQL.

Podemos hacer que priorice los archivos PHP sobre los de html ya que cuando un usuario solicite un archivo, apache buscará primero los archivos html, pero no es algo obligatorio. Solo tendríamos que abrir el archivo dir.conf mediante nano y cambiar esta parte:
![dirconf](../capturas/dirConf.PNG)

Mueve el archivo de índice de PHP (subrayado arriba) a la primera posición después de la especificación DirectoryIndex.

Trás esto, reiniciaremos el apache para que se apliquen los cambios
![restart](../capturas/restartApache.PNG)

Para terminar la instalación de PHP, puedes descargar diferentes módulos que te podrán servir, Si quieres ver los módulos que puedes instalar utiliza el comando "apt search php - | less"

Usa las flechas para moverte hacia arriba y abajo, y pulsa Q para salir.

Y si quisieras una descripción más detallada del paquete, solamente tendrías que poner "apt show package_name"