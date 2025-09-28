
# Instalacion de WordPress en Ubuntu Desktop 22.04 LTS

-------------------
Este documento proporciona una guía paso a paso para instalar WordPress en un servidor Ubuntu 22.04 LTS. WordPress es un sistema de gestión de contenido (CMS) popular que permite crear y administrar sitios web fácilmente.
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
## Paso 1: Actualizar el sistema
-----------------------------
```bash
sudo apt update
sudo apt upgrade -y 