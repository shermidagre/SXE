
# Instalacion de WordPress en Ubuntu Desktop 22.04 LTS

-------------------
Este documento proporciona una guía paso a paso para

instalar WordPress en un servidor Ubuntu 22.04 LTS. WordPress es un sistema de gestión de contenido (CMS) popular que permite crear y administrar sitios web fácilmente.
Requisitos previos
-------------------

- Un servidor con Ubuntu 22.04 LTS.
- Acceso a una cuenta con privilegios sudo.
- Un servidor web (Apache o Nginx).
- PHP 7.4 o superior.
- MySQL o MariaDB.
- Acceso a la terminal o SSH.

----------------------------
# En caso de que no tengas nada instalado(apache, php o mysql), sigue estos pasos, para asi poder tener lo minimo:
-----------------------------
## Paso 1: Instalar Apache como servidor web
-----------------------------

[Ver video](https://youtu.be/OJctgGheJWM)

### Si quieres hacerlo sin video, aqui tienes los comandos:

```bash
sudo apt update && sudo apt upgrade 
sudo apt install apache2
Escribe en el navegador para asi comprobar si funciona: http://localhost
```

-----------------------------
## Paso 2: Instalar mysql como servidor de base de datos
-----------------------------

![Instalar mysql - Hecho con Clipchamp_1759056236552(1).mp4](Videos/Instalar%20mysql%20-%20Hecho%20con%20Clipchamp_1759056236552%281%29.mp4)

### Si quieres hacerlo sin video, aqui tienes los comandos:

```bash
sudo apt update && sudo apt upgrade 
sudo apt install mysql-server
sudo systemctl status mysql
sudo systemctl restart mysql
```
-----------------------------
## Paso 3: Instalar php para interpretar lenguajes de script
-----------------------------

![Instalar php - Hecho con Clipchamp_1759055070293(1).mp4](Videos/Instalar%20php%20-%20Hecho%20con%20Clipchamp_1759055070293%281%29.mp4)

### Si quieres hacerlo sin video, aqui tienes los comandos:

```bash
sudo apt update && sudo apt upgrade 
sudo apt install php libapache2-mod-php php-mysql
sudo systemctl restart apache2
sudo systemctl status apache2
sudo nano /var/www/html/info.php para asi poder abrir el archivo y escribir 
Aqui dentro del archivo escribimos: Prueba<?php phpinfo();?> 
Guardamos y salimos con ctrl + x y luego Y
Escribimos en el navegador para asi comprobar si funciona: http://localhost/info.php
```

-----------------------------
## Paso 4: Instalar phpMyAdmin como interfaz grafica para gestionar MySQL
-----------------------------

![instalar phpmyadmin - Hecho con Clipchamp_1759056482327(1).mp4](Videos/instalar%20phpmyadmin%20-%20Hecho%20con%20Clipchamp_1759056482327%281%29.mp4)

```bash
sudo mysql_secure_installation
Aqui seguimos los pasos que nos indica, en el primero ponemos un 1 para establecer una contraseña de root
Despues de esto, nos va a pedir que pongamos una contraseña, la ponemos y la confirmamos
Despues nos va a hacer una serie de preguntas, a todas respondemos con algo random para skippearlas
sudo mysql -u root -p
Aqui nos va a pedir la contraseña que hemos puesto antes, la ponemos y entramos
Creamos la base de datos para wordpress:
CREATE DATABASE wordpress;
Creamos un usuario y le damos permisos a la base de datos que acabamos de crear:
CREATE USER 'usuario_wp'@'localhost' IDENTIFIED BY 'tu_contraseña_segura';
GRANT ALL PRIVILEGES ON wordpress.* TO 'usuario_wp'@'localhost';
FLUSH PRIVILEGES;
\q para salir de mysql
sudo apt install phpmyadmin
ls /usr/share/phpmyadmin para comprobar que se ha instalado correctamente
sudo ln -s /usr/share/phpmyadmin /var/www/html/phpmyadmin # Creamos un enlace simbolico para asi poder acceder desde el navegador
sudo systemctl restart apache2 # Reiniciamos apache2 para que tome los cambios
ls -l /var/www/html/phpmyadmin para comprobar que se ha creado el enlace simbolico
Aqui nos va a pedir que seleccionemos el servidor web, seleccionamos apache2 
Despues nos va a pedir que configuremos la base de datos para phpmyadmin, seleccionamos que no para asi editar luego
Escribimos en el navegador para asi comprobar si funciona: http://localhost/phpmyadmin
```
-----------------------------
# Ya tienes lo minimo para instalar WordPress
-----------------------------


-----------------------------
## Paso 5: Descargar e instalar WordPress
-----------------------------

![configuracion wordpress1 - Hecho con Clipchamp_1759056027531(1).mp4](Videos/configuracion%20wordpress1%20-%20Hecho%20con%20Clipchamp_1759056027531%281%29.mp4)

```bash
cd /tmp
wget https://wordpress.org/latest.tar.gz
tar -xvzf latest.tar.gz
sudo cp -a wordpress /var/www/html/
sudo chown -R www-data:www-data /var/www/html/wordpress
sudo chmod -R 755 /var/www/html/wordpress
```

### Separamos su configuracion en dos partes para que sea mas facil de entender

![configuracion wordpress2 - Hecho con Clipchamp_1759055294187(1).mp4](Videos/configuracion%20wordpress2%20-%20Hecho%20con%20Clipchamp_1759055294187%281%29.mp4)

### Si quieres hacerlo sin video, aqui tienes los comandos:

```bash
sudo cp /var/www/html/wp-config-sample.php /var/www/html/wp-config.php
sudo nano /var/www/html/wordpress/wp-config.php # Editamos el archivo de configuracion
define('DB_NAME', 'wordpress');
define('DB_USER', 'usuario_wp');
define('DB_PASSWORD', 'tu_contraseña_segura');
define('DB_HOST', 'localhost');
Guardamos y salimos con ctrl + x y luego Y
Escribimos los datos de la base de datos que hemos creado antes
sudo snap install curl # Instalamos curl si no lo tenemos
curl -s https://api.wordpress.org/secret-key/1.1/salt/ # Copiamos las lineas que nos da y las pegamos en el archivo de configuracion, reemplazando las que ya hay
agregamos las lineas que nos ha dado curl en el archivo de configuracion
systemctl restart apache2 # Reiniciamos apache2 para que tome los cambios
Y con los siguientes pasos terminamos la instalacion desde el navegador
Abrimos el navegador y escribimos: http://localhost/wordpress
Seleccionamos el idioma y le damos a continuar
Rellenamos los campos del formulario y le damos a instalar wordpress
Una vez instalado, nos va a pedir que iniciemos sesion, ponemos el usuario y la contraseña que hemos puesto antes
```