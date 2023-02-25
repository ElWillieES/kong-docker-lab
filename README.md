# Kong Docker Lab

## Introducción

Este repo comparte un pequeño laboratorio en formato de Docker Compose, con el que podemos arrancar varios componentes:

* **Kong Gateway** como servidor API Manager (la versión Community)
* **Konga** como Dashboard y herramienta gráfica de administración
* **PostgreSQL** como base de datos para Kong y Konga, utilizando un volumen Docker
* **Varios contendores NGINX** para simular servicios que deseamos exponer al exterior a través de Kong

Algunos contenedores tienen IP fija (dentro de la red Docker), de tal modo que podamos hacer pruebas de filtrado de IP.

De esta forma, podemos arrancar este laboratorio y trastear, probar a publicar servicios (Services + Routes), balanceo (Upstreams), plugins de autenticación (ej: API Key), etc, de forma rápida y sencilla, en tu portátil (necesario Docker y Docker Compose, claro).

**Puedes apoyar mi trabajo siguiéndome, haciendo "☆ Star" en el repo, o nominarme a "GitHub Star"**. Muchas gracias :-) 

[![GitHub Star](https://img.shields.io/badge/GitHub-Nominar_a_star-yellow?style=for-the-badge&logo=github&logoColor=white&labelColor=101010)](https://stars.github.com/nominate/)

En mi Blog personal ([El Willie - The Geeks invaders](https://elwillie.es)) y en mi perfil de GitHub, encontrarás más información sobre mi, y sobre los contenidos de tecnología que comparto con la comunidad.

[![Web](https://img.shields.io/badge/GitHub-ElWillieES-14a1f0?style=for-the-badge&logo=github&logoColor=white&labelColor=101010)](https://github.com/ElWillieES)

# Docker - Ejecución en local con Docker Compose

Los siguientes comandos ejecutados en la raíz del Proyecto, muestra cómo arrancar todos los contenedores con Docker Compose, como comprobar su estados, así como la forma de poder comprobar los logs de su ejecución.

```shell
docker-compose up -d
docker-compose ps
docker-compose logs
```

En caso necesario, podemos parar (sin eliminar) y volver a arrancar todos los contenedores Docker con los siguientes comandos:

```shell
docker-compose stop
docker-compose start
```

Si deseamos parar y/o arrancar un único contenedor (ej: service_a), podemos utilizar comandos como los siguientes:

```shell
docker-compose stop service_a
docker-compose start service_a
```

Podemos parar y eliminar todos los contenedores con el siguiente comando:

```shell
docker-compose down
```