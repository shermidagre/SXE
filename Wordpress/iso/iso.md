
# Instalar Ubuntu Desktop 22.04 LTS

-------------------

Este documento proporciona una guía paso a paso para instalar Ubuntu Desktop 22.04 LTS en tu computadora. Ubuntu es una distribución popular de Linux que ofrece una experiencia de usuario amigable y una amplia gama de aplicaciones.
Requisitos previos
-------------------
- Una computadora compatible con Ubuntu (verifica los requisitos del sistema en el sitio web oficial de Ubuntu).
- Una unidad USB con al menos 4 GB de espacio (para crear un medio de instalación
- Acceso a otra computadora para descargar la imagen ISO de Ubuntu y crear el medio de instalación.
- Una conexión a Internet (opcional, pero recomendada para descargar actualizaciones durante la instalación
- Acceso a la terminal o BIOS/UEFI de tu computadora para cambiar el orden de arranque si es necesario.
-------------------
# Paso 1: Descargar la imagen ISO de Ubuntu 22.04 LTS
-------------------
1. Abre un navegador web en otra computadora.
2. Ve al sitio web oficial de Ubuntu: [https://ubuntu.com/download/desktop](https://ubuntu.com/download/desktop)
3. Selecciona la versión 22.04 LTS y haz clic en "Download".
4. Guarda el archivo ISO en una ubicación accesible.
-------------------
# Paso 2: Crear un medio de instalación USB
-------------------
1. Descarga e instala una herramienta para crear medios de instalación USB, como Rufus (https://rufus.ie/) para Windows o balenaEtcher (https://www.balena
2. Inserta la unidad USB en la computadora.
3. Abre la herramienta de creación de medios USB.
4. Selecciona la imagen ISO de Ubuntu que descargaste.
5. Selecciona la unidad USB como destino.
6. Haz clic en "Start" o "Flash" para crear el medio de instalación.
-------------------
# Paso 3: Configurar la computadora para arrancar desde USB
-------------------
1. Inserta la unidad USB en la computadora donde deseas instalar Ubuntu.
2. Reinicia la computadora y accede al menú de arranque o BIOS/UEFI (generalmente presionando una tecla como F2, F12, Esc o Del durante el arranque).
3. Cambia el orden de arranque para que la unidad USB sea la primera opción.
4. Guarda los cambios y sal del BIOS/UEFI.
-------------------
# Paso 4: Instalar Ubuntu 22.04 LTS
-------------------
1. La computadora debería arrancar desde la unidad USB y mostrar el menú de instalación de Ubuntu.
2. Selecciona "Install Ubuntu".
3. Sigue las instrucciones en pantalla para seleccionar el idioma, la distribución del teclado y la conexión a Internet (si es necesario).
4. Elige el tipo de instalación (normal o mínima) y si deseas instalar actualizaciones y software de terceros.
5. Selecciona el disco donde deseas instalar Ubuntu. Puedes optar por borrar todo el disco o instalar junto a otro sistema operativo.
6. Configura tu zona horaria.
7. Crea una cuenta de usuario proporcionando tu nombre, nombre de usuario y contraseña.
8. Revisa la configuración y haz clic en "Install Now" para comenzar la instalación.
9. Espera a que se complete la instalación. Esto puede tardar varios minutos.
10. Una vez finalizada la instalación, reinicia la computadora cuando se te indique.
11. Retira la unidad USB cuando se te solicite.
-------------------
# Paso 5: Configuración inicial
-------------------
1. Inicia sesión con la cuenta de usuario que creaste durante la instalación.
2. Actualiza el sistema abriendo la terminal y ejecutando los siguientes comandos:
   ```bash
   sudo apt update
   sudo apt upgrade
   ```
3. Instala cualquier software adicional que necesites desde la tienda de aplicaciones de Ubuntu o usando la terminal.
4. Configura tus preferencias de sistema, como fondos de pantalla, temas y ajustes de privacidad.
¡Felicidades! Has instalado Ubuntu Desktop 22.04 LTS en tu computadora. Disfruta explorando y utilizando tu nuevo sistema operativo.


-------
## Si quieres simplemente instalarlo en una maquian virtual (VM) como VirtualBox o VMware, simplemente crea una nueva maquina virtual y cuando te pida un disco de arranque, selecciona la ISO que descargaste en el paso 1 y sigue los pasos de la instalación.
-------

### Descarga la ISO de Ubuntu 22.04 LTS aquí:
[https://ubuntu.com/download/desktop](https://ubuntu.com/download/desktop)

#### Ahora simplemente configura la vbox sigue el tutorial y disfruta de Ubuntu 22.04 LTS!

## Como configurar VirtualBox para Ubuntu 22.04 LTS?
1. Abre VirtualBox y haz clic en "Nuevo" para crear una nueva máquina virtual.
2. Asigna un nombre a la máquina virtual (por ejemplo, "Ubuntu 22.04 LTS").
3. Selecciona "Linux" como tipo y "Ubuntu (64-bit)" como versión. Haz clic en "Siguiente".
4. Asigna la cantidad de memoria RAM (recomendado al menos 2048 MB). Haz clic en "Siguiente".
5. Selecciona "Crear un disco duro virtual ahora" y haz clic en "Crear".
6. Elige "VDI (VirtualBox Disk Image)" y haz clic en "Siguiente".
7. Selecciona "Reservado dinámicamente" y haz clic en "Siguiente".
8. Asigna el tamaño del disco duro virtual (recomendado al menos 25 GB). Haz clic en "Crear".
9. Selecciona la máquina virtual recién creada y haz clic en "Configuración".
10. Ve a la pestaña "Almacenamiento", selecciona el controlador IDE y haz clic en el icono del disco con un signo más para agregar un nuevo dispositivo óptico.
11. Selecciona "Elegir un archivo de disco" y navega hasta la ubicación donde descargaste la ISO de Ubuntu 22.04 LTS. Selecciónala y haz clic en "Abrir".
12. Haz clic en "Aceptar" para guardar la configuración.
13. Inicia la máquina virtual haciendo clic en "Iniciar".
14. Sigue los pasos de instalación de Ubuntu 22.04 LTS como se describe en la sección anterior.


