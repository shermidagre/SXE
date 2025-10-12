
---

# Práctica: Servidores Web con Docker y Apache

Este documento describe los pasos realizados para configurar dos contenedores de Apache usando Docker, con un volumen compartido mediante *bind mount*, de forma que ambos sirvan el mismo contenido web.

---



### 1. Descarga la imagen 'httpd' y comprueba que está en tu equipo.

**Comando:**
```bash
docker pull httpd:2.4
```
---
**Video**:
[![Miniatura del video](https://img.youtube.com/vi/5n6v1jvXG7o/0.jpg)](https://youtu.be/5n6v1jvXG7o)
> 💡 Haz clic en la imagen para abrir el tutorial en YouTube.
---

Esto muestra la imagen `httpd` con la etiqueta `2.4` en la lista local.

---



### 2. Crea un contenedor con el nombre 'dam_web1'.

**Comando:**
```bash


```
---
**Video**:
[![Miniatura del video](https://img.youtube.com/vi/5n6v1jvXG7o/0.jpg)](https://youtu.be/5n6v1jvXG7o)
> 💡 Haz clic en la imagen para abrir el tutorial en YouTube.
---


---

### 3. Si quieres poder acceder desde el navegador de tu equipo, ¿qué debes hacer?



```bash

```
---
**Video**:
[![Miniatura del video](https://img.youtube.com/vi/5n6v1jvXG7o/0.jpg)](https://youtu.be/5n6v1jvXG7o)
> 💡 Haz clic en la imagen para abrir el tutorial en YouTube.
---


---

### 4. Utiliza bind mount para que el directorio del Apache 'htdocs' esté montado en un directorio que tú elijas.


```bash

```
---
**Video**:
[![Miniatura del video](https://img.youtube.com/vi/5n6v1jvXG7o/0.jpg)](https://youtu.be/5n6v1jvXG7o)
> 💡 Haz clic en la imagen para abrir el tutorial en YouTube.
---



### 5. Realiza un 'hola mundo' en HTML y comprueba que accedes desde el navegador.


```bash
```

---
**Video**:
[![Miniatura del video](https://img.youtube.com/vi/5n6v1jvXG7o/0.jpg)](https://youtu.be/5n6v1jvXG7o)
> 💡 Haz clic en la imagen para abrir el tutorial en YouTube.
---


### 6. Crea otro contenedor 'dam_web2' con el mismo bind mount y en otro puerto (ej. 9080).

**Comando:**

```bash

```

---
**Video**:
[![Miniatura del video](https://img.youtube.com/vi/5n6v1jvXG7o/0.jpg)](https://youtu.be/5n6v1jvXG7o)
> 💡 Haz clic en la imagen para abrir el tutorial en YouTube.
---

---

### 7. Comprueba que los dos servidores 'sirven' la misma página.

---
**Video**:
[![Miniatura del video](https://img.youtube.com/vi/5n6v1jvXG7o/0.jpg)](https://youtu.be/5n6v1jvXG7o)
> 💡 Haz clic en la imagen para abrir el tutorial en YouTube.
---

---

### 8. Realiza modificaciones de la página y comprueba que los dos servidores 'sirven' la misma página.

```bash
```
---
**Video**:
[![Miniatura del video](https://img.youtube.com/vi/5n6v1jvXG7o/0.jpg)](https://youtu.be/5n6v1jvXG7o)
> 💡 Haz clic en la imagen para abrir el tutorial en YouTube.
---
