
---

# Práctica: Servidores Web con Docker y Apache

Este documento describe los pasos realizados para configurar dos contenedores de Apache usando Docker, con un volumen compartido mediante *bind mount*, de forma que ambos sirvan el mismo contenido web.

---


## Los pasos 1 y 2 en el mismo video

### 1. Descarga la imagen 'httpd' y comprueba que está en tu equipo.

### 2. Crea un contenedor con el nombre 'dam_web1'.

**Comando:**
```bash

docker create --name dam_web httpd:2.4

docker images
docker ps -a 

```
---

**Video**:

[![Miniatura del video](https://img.youtube.com/vi/czanQGPz53k/0.jpg)](https://youtu.be/czanQGPz53k)

> 💡 Haz clic en la imagen para abrir el tutorial en YouTube.
---


### 3. Si quieres poder acceder desde el navegador de tu equipo, ¿qué debes hacer?


**Comando:**
```bash

docker start dam_web1
docker exec -it dam_web1 sh

```

---
**Video**:

[![Miniatura del video](https://img.youtube.com/vi/438rsUtOuTw/0.jpg)](https://youtu.be/438rsUtOuTw)

> 💡 Haz clic en la imagen para abrir el tutorial en YouTube.
---



## Los pasos 4 y 5 estan en el mismo video

### 4. Utiliza bind mount para que el directorio del Apache 'htdocs' esté montado en un directorio que tú elijas.

**Comando:**
```bash
docker create -p 8000:80 -v  C:\Userrs\samue\Documents\Dam2\SXE\Docker-Tarea04\src:/usr/local/apache2/hdocs --name secondone httpd

```

### 5. Realiza un 'hola mundo' en HTML y comprueba que accedes desde el navegador.

---

**Video**:

[![Miniatura del video](https://img.youtube.com/vi/7PeQxfycCaM/0.jpg)](https://youtu.be/7PeQxfycCaM)

> 💡 Haz clic en la imagen para abrir el tutorial en YouTube.

---


## Los pasos 6 7 y 8 estan en el mismo video


### 6. Crea otro contenedor 'dam_web2' con el mismo bind mount y en otro puerto (ej. 9080).

**Comando:**

```bash
docker create -p 9080:80 -v  C:\Userrs\samue\Documents\Dam2\SXE\Docker-Tarea04\src:/usr/local/apache2/hdocs --name secondone httpd

```

### 7. Comprueba que los dos servidores 'sirven' la misma página.

### 8. Realiza modificaciones de la página y comprueba que los dos servidores 'sirven' la misma página.

**Video**:

[![Miniatura del video](https://img.youtube.com/vi/1DNhh_65DKI/0.jpg)](https://youtu.be/1DNhh_65DKI)

> 💡 Haz clic en la imagen para abrir el tutorial en YouTube.
---
