### Virtual Hosts

Crearemos dos subdominios de nuevo, como lo hicimos en la [Tarea 3](https://github.com/ekaitz888/evidencias/blob/master/tarea%203/evidencias/DNS.md)

![cliente-ekaitz](../capturas/servidor-ekaitz.PNG)

Uno de cliente y otro para servidor

![servidor-ekaitz](../capturas/servidor-ekaitz.PNG)

En el servidor, crearemos en el directorio *var/www* las carpetas *servidor* y *cliente*

![mkdir](../capturas/www.PNG)

Vamos a crear dos archivos html en las carpetas llamadas *index.html*

![index](../capturas/ServidorIndex.PNG)

Uno para servidor y otro para cliente

![IndexCliente](../capturas/ClienteIndex.PNG)

Usaremos el comando a2ensite para habilitarlos

![a2ensite](../capturas/a2ensite.PNG)

Copiaremos el archivos *000-default.conf* que tenemos en sites-avaliable a los archivos *.conf* de cada archivo index que hemos hecho anteriormente

![cp](../capturas/cp.PNG)

Los archivos conf vamos a editarlos para crear un directorio al *var/www* para que se nos abra el archivo en el navegador

![clienteConf](../capturas/clienteConf.PNG) 

![servidorConf](../capturas/ServevrConf.PNG)

Finalmente vamos a reiniciar el systemctl para que se apliquen los cambios al apache

![systemctl](../capturas/systemctl.PNG)

Si entramos a la página desde nuestro navegador nos saldrá el archivo subido al servidor

![pagina](../capturas/pagina.PNG)