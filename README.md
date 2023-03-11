# Kong Docker Lab

![Docker](https://img.shields.io/badge/Docker-2496ED?&style=flat&logo=docker&logoColor=ffffff)&nbsp;
![Kong](https://img.shields.io/badge/Kong-1AA687?style=flat&logo=Kongregate&logoColor=FFFFFF)&nbsp;
![Postgresql](https://img.shields.io/badge/Postgresql-FFFFFF?style=flat&logo=postgresql&logoColor=316192)&nbsp;
![Nginx](https://img.shields.io/badge/nginx-%23009639.svg?style=flat&logo=nginx&logoColor=white)&nbsp;
![Redis](https://img.shields.io/badge/redis-%23DD0031.svg?style=flat&logo=redis&logoColor=white)&nbsp;
![Prometheus](https://img.shields.io/badge/Prometheus-E6522C?style=flat&logo=Prometheus&logoColor=white)&nbsp;
![Grafana](https://img.shields.io/badge/grafana-%23F46800.svg?style=flat&logo=grafana&logoColor=white)

Más ejemplos de Badges en [markdown-badges](https://ileriayo.github.io/markdown-badges/)

## Introducción

Este repo comparte un pequeño laboratorio en formato de Docker Compose, con el que podemos arrancar varios componentes:

* **Kong Gateway** como servidor API Manager (la versión Community)
* **Konga** como Dashboard y herramienta gráfica de administración
* **PostgreSQL** como base de datos para Kong y Konga, utilizando un volumen Docker
* **Varios contendores NGINX** para simular servicios que deseamos exponer al exterior a través de Kong, apoyándose en el uso de [variables de NGINX](http://nginx.org/en/docs/varindex.html) para ayudar a depurar en las pruebas
* **Redis** que podemos utilizarlo para pruebas con el Plugin de Rate Limiting, por ejemplo.
* **Prometheus** y **Grafana** para pruebas de monitorización, ambos utilizando volúmenes Docker

Algunos contenedores tienen IP fija (dentro de la red Docker), de tal modo que podamos hacer pruebas de filtrado de IP.

De esta forma, podemos arrancar este laboratorio y trastear, probar a publicar servicios (Services + Routes), balanceo (Upstreams), plugins de autenticación (ej: API Key), etc, de forma rápida y sencilla, en tu portátil (necesario Docker y Docker Compose, claro).

Aunque este Docker Compose arranca varios NGINX que podemos utilizar para simular micro-servicios en nuestras pruebas, si lo deseamos también podemos utilizar [Mockbin](https://mockbin.org/), un servicio gratuito que permite mockear endpoints HTTP, que también nos puede resultar de utilidad para hacer nuestras pruebas de laboratorio, y publicar a través de Kong lo servicios fake de Mockbin a modo de laboratorio.

**Puedes apoyar mi trabajo siguiéndome, haciendo "☆ Star" en el repo, o nominarme a "GitHub Star"**. Muchas gracias :-) 

[![GitHub Star](https://img.shields.io/badge/GitHub-Nominar_a_star-yellow?style=for-the-badge&logo=github&logoColor=white&labelColor=101010)](https://stars.github.com/nominate/)

En mi Blog personal ([El Willie - The Geeks invaders](https://elwillie.es)) y en mi perfil de GitHub, encontrarás más información sobre mi, y sobre los contenidos de tecnología que comparto con la comunidad.

[![Web](https://img.shields.io/badge/GitHub-ElWillieES-14a1f0?style=for-the-badge&logo=github&logoColor=white&labelColor=101010)](https://github.com/ElWillieES)

# Docker - Ejecución en local con Docker Compose

Lo primero, en la raíz del repo, debemos **editar el fichero .env** donde se establecen variables que podemos utilizar en los contenedores definidos en el Docker Compose, como sería la Zona Horaria. 

Por ejemplo, para usar Madrid deberíamos dejar así la variable TZ en el ficher .env

```shell
TZ=Europe/Madrid
```

Los siguientes comandos ejecutados en la raíz del Proyecto, muestra cómo arrancar todos los contenedores con Docker Compose, como comprobar su estado, así como la forma de poder comprobar los logs de su ejecución.

```shell
docker-compose up -d
docker-compose ps
docker-compose logs
```

Podemos abrir una sesión bash en cualquiera de los contenedores ejecutando con comando como el siguiente:

```shell
docker exec -it kong-docker-lab-service_a-1 bash
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
