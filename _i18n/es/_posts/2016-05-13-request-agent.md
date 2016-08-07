---
title: 'Peticiones de un agente'
description: 'Peticiones de un agente'

category: 'api'
layout: blank
---

Cada **[proyecto](#/project/)** puede tener N-agentes recolectando las metricas en distintos servidores o **EndPoint**.
La **API** solo puede recibir dos peticiones por minutos en el plan **free**, osea que si tenemos 4 agentes recolectando
informacion de los recursos como el disco duro o la memoria, cada uno podra enviar las metricas cada dos minutos.

Si usted necesita aumentar la frecuencia de recoleccion de metricas, por favor pongase en contacto con nosotros para que conozca
como poder incrementarla.

Si se tiene configurado en el **proyecto** las restriccion desde que **IPs** se pueden enviar las peticiones, los agentes
deben enviar las metricas detras de las **IPs** configuradas. Para saber mas sobre restricciones de **IPs** acceder a la pagina
**[IPs](#/ip/)**

