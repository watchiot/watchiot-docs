---
title: 'Introducion'
description: 'Introducion'

layout: blank
---

Bienvenido a la documentacion the **WatchIoT**. Vamos a intentar mantener la documentacion lo mas
escueta y sencilla posible.

### Que es WatchIoT?

**WatchIoT** es un servicio en la nube que brinda la posibilidad de monitorear y recolectar datos de nuestros activos (aplicaciones,
servicios, dispositivos, IoT, etc) comprobando si los datos obtenidos estan dentro de un patron aceptado previamente
configurado y si no lo estan, notificar por distintas vias en tiempo real de la anomalia.

**WatchIoT** almacena un historial de como se va comportando nuestros activos en el transcurso del tiempo.
Brindado graficas avanzadas donde usted puede tener una pespectiva global y realizar tomas
de deciciones basados en el comportamiento de sus activos. Por ejemplo que dias de la semana sus servicios demanda
mayor memoria RAM, en que fechas sus clientes realizan mas compras o en cuales no, etc.

### Organizacion de la documentacion

* **General:** Explica los diferentes conceptos manejados por **WatchIot**. Tales como *espacios*, *proyectos*,
*notificaciones*, *equipos*, *graficas*, *agentes* y *configuraciones predefinidas*

* **[Config](#/config/):** Define como configurar un proyecto con las diferentes opciones para recolectar metricas
y enviar notificaciones

* **[API](#/api/):** Detalla nuestra **API** de recoleccion de metricas e integracion con los agentes.

* **[SDK](#/sdk/):** Brinda un panorama de como utilizar diferentes **SDK** para distintos lenguajes y plataformas con la
finalidad de lograr una mayor y segura integracion con nuestra **API**

* **[Agentes](#/agent-repo/):** Describe los agentes y configuraciones predefinidas presente como parte de los servicios que
brinda **WatchIot** ademas de como agregar nuevos agentes y configuraciones predefinas al repositorio de **WatchIot**
