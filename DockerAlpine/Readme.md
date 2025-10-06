
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

![2(1).png](Media/2%281%29.png)

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

-----------------------------

[![Miniatura del video](https://img.youtube.com/vi/UyrqI_LYF7M/0.jpg)](https://youtu.be/UyrqI_LYF7M)

> 💡 Haz clic en la imagen para abrir el tutorial en YouTube.

---

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

-----------------------------

[![Miniatura del video](https://img.youtube.com/vi/UyrqI_LYF7M/0.jpg)](https://youtu.be/UyrqI_LYF7M)

> 💡 Haz clic en la imagen para abrir el tutorial en YouTube.

[![Miniatura del video](https://img.youtube.com/vi/CLnaZkrQTWM/0.jpg)](https://youtu.be/CLnaZkrQTWM)

> 💡 Haz clic en la imagen para abrir el tutorial en YouTube.

---

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

-----------------------------

[![Miniatura del video](https://img.youtube.com/vi/_VaOfJrHE9I/0.jpg)](https://youtu.be/_VaOfJrHE9I)

> 💡 Haz clic en la imagen para abrir el tutorial en YouTube.

---


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

-----------------------------

[![Miniatura del video](https://img.youtube.com/vi/8EOCM_wa2lA/0.jpg)](https://youtu.be/8EOCM_wa2lA)

> 💡 Haz clic en la imagen para abrir el tutorial en YouTube.

[![Miniatura del video](https://img.youtube.com/vi/ySYqXAYOTA0/0.jpg)](https://youtu.be/ySYqXAYOTA0)

> 💡 Haz clic en la imagen para abrir el tutorial en YouTube.
---


### Comandos:
```bash

docker create -it --name dam_alp2 alpine
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

-----------------------------

[![Miniatura del video](https://img.youtube.com/vi/PXJOUUilMAo/0.jpg)](https://youtu.be/PXJOUUilMAo)

> 💡 Haz clic en la imagen para abrir el tutorial en YouTube.

---

### Observación:

Cuando sales del terminal del contenedor con `exit`, y el contenedor no se detiene


-----------------------------
## Paso 7: ¿Cuánta memoria en el disco duro ocupaste?
-----------------------------

-----------------------------

[![Miniatura del video](https://img.youtube.com/vi/SdQIEwqcrZk/0.jpg)](https://youtu.be/SdQIEwqcrZk)

> 💡 Haz clic en la imagen para abrir el tutorial en YouTube.

---

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

-----------------------------

[![Miniatura del video](https://img.youtube.com/vi/SdQIEwqcrZk/0.jpg)](https://youtu.be/SdQIEwqcrZk)

> 💡 Haz clic en la imagen para abrir el tutorial en YouTube.

---

### Comandos:
```bash
docker stats --no-stream
```

### Descripción:
`docker stats` muestra en tiempo real el uso de CPU, RAM, red y E/S de todos los contenedores en ejecución.  
Alpine, al ser muy ligero, suele consumir **menos de 2 MB de RAM** cuando está inactivo.

-----------------------------


