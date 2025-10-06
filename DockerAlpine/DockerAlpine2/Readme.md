

# Ejercicios prácticos con Docker

-------------------
Este documento contiene una serie de ejercicios para practicar el uso de Docker con imágenes como **Alpine** y **Ubuntu**. Cada ejercicio incluye los comandos necesarios y una breve explicación del proceso.  
Se recomienda realizar un commit por ejercicio si se integra en un repositorio Git.

Requisitos previos
-------------------

- Docker instalado y funcionando.
- Acceso a la terminal.
- Conocimientos básicos de comandos de Linux.
- Conexión a internet para descargar imágenes.

-----------------------------
## Ejercicio 1: Imprimir "Hello World"
-----------------------------

### Objetivo:
Crear un contenedor con la imagen `alpine` y ejecutar un comando que imprima `"Hello World"` usando `echo`.

### Video:



### Comandos:
```bash
docker run alpine echo "Hello World"
```

### Descripción:
Este comando inicia un contenedor efímero, ejecuta `echo "Hello World"` y termina inmediatamente. No requiere interacción.

-----------------------------
## Ejercicio 2: Crear y Eliminar un Contenedor
-----------------------------

### Objetivo:

Crear un contenedor llamado `probando-uno-dos`, verificar que está detenido y eliminarlo.

### Video:



### Comandos:
```bash
docker run --name probando-uno-dos alpine
docker ps -a
docker rm probando-uno-dos
```

### Descripción:
Al no especificar un comando interactivo, el contenedor se ejecuta y se detiene al instante.  
`docker ps -a` muestra contenedores detenidos.  
`docker rm` elimina el contenedor por su nombre.

-----------------------------
## Ejercicio 3: Establecer un Directorio de Trabajo
-----------------------------

### Video:



### Objetivo:
Iniciar un contenedor con directorio de trabajo `/var/lib` y verificarlo con `pwd`.

### Comandos:
```bash
docker run -w /var/lib alpine pwd
```

### Descripción:
La bandera `-w` establece el *working directory*.  
El comando `pwd` muestra `/var/lib`, confirmando que el directorio se aplicó correctamente.

-----------------------------
## Ejercicio 4: Interacción con el Contenedor
-----------------------------
### Objetivo:

Crear un contenedor interactivo que permita usar una shell como si fuera una máquina remota.

### Video:



### Comandos:
```bash
docker run -it alpine
# (dentro del contenedor) puedes ejecutar comandos como ls, apk, etc.
# Para salir: exit
```

### Descripción:
Las banderas `-i` (interactivo) y `-t` (asignar pseudo-TTY) permiten mantener una sesión activa con `/bin/sh`.

-----------------------------
## Ejercicio 5: Mensaje secreto
-----------------------------

### Objetivo:

Iniciar un contenedor con la imagen `devopsdockeruh/simple-web-service:ubuntu` y seguir los logs para ver un "mensaje secreto" cada 10 segundos.

### Video:



### Comandos:
```bash
docker run -d --name secret-service devopsdockeruh/simple-web-service:ubuntu
docker exec -it secret-service tail -f ./text.log
```

> 💡 El contenedor se ejecuta en segundo plano (`-d`).  
> Usa `Ctrl + C` para salir del `tail -f` sin detener el contenedor.

### Descripción:
La aplicación escribe logs periódicos en `./text.log`. El mensaje secreto aparece cada 10 segundos.

-----------------------------
## Ejercicio 6: Ejecutar un Contenedor de Ubuntu con entrada de usuario
-----------------------------

### Objetivo:

Ejecutar un contenedor de Ubuntu que pida un sitio web y use `curl` para acceder a él.

### Video:



### Comandos:
```bash
docker run -it ubuntu sh -c 'echo "Ingresa un sitio web:"; read website; apt-get update && apt-get install -y curl && curl http://$website;'
```

> 💡 Prueba con: `parrot.live`

### Descripción:
- `-it` permite entrada interactiva.
- `curl` no viene instalado en Ubuntu por defecto, así que se instala dentro del mismo comando.
- El proceso se ejecuta en una sola línea para mantener el contexto de la variable `$website`.

-----------------------------
## Ejercicio 7: Crea una imagen a partir del contenedor anterior
-----------------------------

### Objetivo:

Convertir el contenedor del Ejercicio 6 (con `curl` instalado) en una nueva imagen reutilizable.

### Video:



### Comandos:
```bash
# Primero, ejecuta el contenedor sin el comando final (solo para instalar curl):
docker run -it --name ubuntu-curl ubuntu
# Dentro del contenedor:
#   apt-get update && apt-get install -y curl
#   exit

# Luego, crea la imagen:
docker commit ubuntu-curl mi-ubuntu-con-curl

# Prueba la nueva imagen:
docker run -it mi-ubuntu-con-curl sh -c 'echo "Ingresa un sitio web:"; read website; curl http://$website;'
```

### Descripción:
`docker commit` guarda el estado del contenedor como una nueva imagen. Útil para prototipado rápido (aunque no recomendado para producción).

-----------------------------
## Ejercicio 8: Crea un Dockerfile
-----------------------------

### Objetivo:

Crear un `Dockerfile` que genere una imagen de **Ubuntu 20.04** con `curl`, `nano`, `vim`, `git`, y que al ejecutarse haga `ls /usr`. El tamaño debe ser ≤ 221 MB.

### Video:



### Archivo: `Dockerfile`
```Dockerfile
FROM ubuntu:20.04

# Evitar prompts interactivos
ENV DEBIAN_FRONTEND=noninteractive

# Actualizar e instalar paquetes en una sola capa (optimización)
RUN apt-get update && \
    apt-get install -y --no-install-recommends curl nano vim git && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

# Comando por defecto
CMD ["ls", "/usr"]
```

### Construcción:
```bash
docker build -t ubuntu-herramientas .
docker images ubuntu-herramientas  # Verifica el tamaño
```

### Descripción:
- `--no-install-recommends` reduce el tamaño.
- `apt-get clean` y eliminar listas de paquetes minimiza la capa.
- Este enfoque suele mantener la imagen por debajo de **220 MB**.

-----------------------------
## Ejercicio 9: Bind Mount
-----------------------------

### Objetivo:

Iniciar el contenedor `devopsdockeruh/simple-web-service` y montar su archivo de logs (`/usr/src/app/text.log`) en tu sistema de archivos local.

### Video:



### Comandos:
```bash
mkdir -p ~/docker-logs
docker run -d --name logger -v ~/docker-logs:/usr/src/app devopsdockeruh/simple-web-service
```

### Verificación:
```bash
tail -f ~/docker-logs/text.log
```

### Descripción:
El bind mount (`-v`) sincroniza la carpeta `/usr/src/app` del contenedor con `~/docker-logs` en tu máquina.  
Los timestamps se escriben directamente en tu disco, incluso si el contenedor se elimina.


