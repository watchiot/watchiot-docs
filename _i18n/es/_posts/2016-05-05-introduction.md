---
title: 'Introducion'
description: 'Introducion'

layout: blank
---

Bienvenido a la documentacion the **WatchIoT**.

### Que es WatchIoT?

**WatchIoT** es un servicio en la nube que brinda la posibilidad de monitorear y recolectar metricas de nuestros activos (aplicaciones,
servicios, dispositivos, IoT, etc) comprobando si las metricas obtenidos estan dentro de un patron aceptado previamente
configurado y si no lo estan **WatchIoT** brinda la posibilidad de notificar por distintas vias en tiempo real de la anomalia.

**WatchIoT** almacena un historial de como se va comportando nuestros activos en el transcurso del tiempo.
Brindado graficas avanzadas donde usted puede tener una pespectiva global y realizar tomas
de deciciones basados en el comportamiento de sus activos. Por ejemplo que dias de la semana sus servicios demanda
mayor memoria RAM, en que fechas sus clientes realizan mas compras o en cuales no, etc.

**WatchIoT** no se puede categorizar como un sistema puramente **[APM](https://en.wikipedia.org/wiki/Application_performance_management)** ya que como no esta anclado a ninguna tecnologia
y es completamente abierto y desacoplado como sistema de monitoreo, puede ser utilizado para propositos mas generales.

### Organizacion de la documentacion

La pirmera parte explica los diferentes conceptos manejados por **WatchIoT**. Tales como *[espacios](#/space/)*, *[proyectos](#/project/)*,
*[notificaciones](#/notification/)*, *[equipos](#/team/)*, *[graficas](#/chart/)* y *[agentes](#/agent/)*

* **[Config](#/config/):** Define como configurar un proyecto con las diferentes opciones para recolectar metricas
y enviar notificaciones

* **[API](#/api/):** Detalla nuestra **API** de recoleccion de metricas e integracion con los agentes.

* **[SDK](#/sdk/):** Brinda un panorama de como utilizar diferentes **SDK** para distintos lenguajes y plataformas con la
finalidad de lograr una mayor y segura integracion con nuestra **API**

* **[Agentes Predefinidos](#/agent-repo/):** Describe los agentes predefinidos presentes en **WatchIoT** como parte de los servicios,
 ademas de como agregar nuevos agentes y configuraciones predefinidos al repositorio de **WatchIoT**
