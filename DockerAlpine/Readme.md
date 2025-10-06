
# Práctica con contenedores Docker usando Alpine

-------------------
Este documento proporciona una guía paso a paso para realizar una serie de tareas prácticas utilizando contenedores Docker con la imagen ligera **Alpine Linux**. 
Cada apartado incluye los comandos necesarios y una breve descripción del proceso.  
Se espera que se cree un archivo `README.md` en formato Markdown, con un commit por cada apartado completado, y que se entregue el repositorio al finalizar.

Requisitos previos
-------------------

- Tener Docker Desktop instalado y funcionando en tu sistema.
- Acceso a la terminal.
- Conocimientos básicos de comandos de Docker.

-----------------------------
## Paso 1: Descargar la imagen "alpine" SIN ARRANCARLA y comprobar que está en tu equipo
-----------------------------

### Imagen:

![2(1).png](Fotos/2%281%29.png)

### Comandos:
```bash
docker pull alpine
```

### Descripción:

El comando `docker pull alpine` descarga la imagen oficial de Alpine desde Docker Hub sin ejecutarla.  

-----------------------------
## Paso 2: Crear un contenedor sin ponerle nombre. ¿Está arrancado? Obtén el nombre
-----------------------------

### Video:

[3.webm](Fotos/3.webm)


### Comandos:
```bash
docker create -it alpine

```

### Descripción:
Al ejecutar `docker create -it  alpine`, se crea un contenedor con imagen alpine sin nombre.  

-----------------------------
## Paso 3: Crear un contenedor con el nombre 'dam_alp1'. ¿Cómo puedes acceder a él?
-----------------------------

### Video:

[3.webm](Fotos/3.webm)
[3-4.webm](Fotos/3-4.webm)

### Comandos:
```bash
docker create -it --name dam_alp1 alpine
```

### Descripción:
Al ejecutar `docker create -it --name dam_alp1 alpine`, se crea un contenedor con imagen alpine y nombre dam_alp1.

-----------------------------
## Paso 4: Comprobar qué IP tiene y si puedes hacer un ping a google.com
-----------------------------

### Video:

[3-4.webm](Fotos/3-4.webm)

### Comandos:
```bash
docker start dam_alp1
docker exec -it dam_alp1 sh
ping -c 4 google.com / ping -c 4 8.8.8.8 / ping 8.8.8.8
```


### Descripción:
Usamos `docker exec` para entrar al contenedor ya existente.  
El ping a `google.com` comprueba conectividad a internet.

-----------------------------
## Paso 5: Crear un contenedor con el nombre 'dam_alp2'. ¿Puedes hacer ping entre los contenedores?
-----------------------------

### Video:

[crear dam2.webm](Fotos/crear%20dam2.webm)

[ping contenedor al otro.webm](Fotos/ping%20contenedor%20al%20otro.webm)

### Comandos:
```bash

docker create -it --name dam_alp2 alpine
docker start dam_alp2
docker exec -it dam_alp2 sh

(En la consola que ya tenias abierta de dam_alp1, escribe ip a, de ahi cogeras la ip de dam_alp1)

ping -c 4 <ip de dam_alp1>
```

### Descripción:
Por defecto, los contenedores en la misma red `bridge` pueden comunicarse por IP.  
Al hacer ping desde `dam_alp2` a la IP de `dam_alp1`, verificamos esta conectividad interna.

-----------------------------
## Paso 6: Sal del terminal, ¿qué ocurrió con el contenedor?
-----------------------------

### Video:

[exit.webm](Fotos/exit.webm)

### Observación:

Cuando sales del terminal del contenedor con `exit`, y el contenedor no se detiene


-----------------------------
## Paso 7: ¿Cuánta memoria en el disco duro ocupaste?
-----------------------------

### Video:

[memoria ram y memoria total.webm](Fotos/memoria%20ram%20y%20memoria%20total.webm)

### Comandos:
```bash
docker system df
```

### Descripción:
El comando `docker system df` muestra el espacio en disco usado por:
- Imágenes
- Contenedores
- Volúmenes
- Cache

La imagen de Alpine ocupa **menos de 10 MB**, y los contenedores apenas añaden sobrecarga si no almacenan datos.

-----------------------------
## Paso 8: ¿Cuánta RAM ocupan los contenedores? ¿Hay algún comando Docker para saber esto?
-----------------------------

### Video:

[memoria ram y memoria total.webm](Fotos/memoria%20ram%20y%20memoria%20total.webm)

### Comandos:
```bash
docker stats --no-stream
```

### Descripción:
`docker stats` muestra en tiempo real el uso de CPU, RAM, red y E/S de todos los contenedores en ejecución.  
Alpine, al ser muy ligero, suele consumir **menos de 2 MB de RAM** cuando está inactivo.

-----------------------------


