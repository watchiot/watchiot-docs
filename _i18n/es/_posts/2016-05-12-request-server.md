---
title: 'Peticiones del servidor'
description: 'Peticiones del servidor'

category: 'api'
layout: blank
---

El servidor puede enviar peticiones hacia un **WebServices** o algun servicio que tengas publicado para obtener las metricas.

Para esto es necesario configurar en el **YAML** del proyecto.

{% highlight yaml %}
...

get:
     url: "https://www.my_site/my_user/my_key"
     freq: 2

...
{% endhighlight %}

La respuesta se espera que sea la misma que envia los agentes como peticion, para mas detalles ver la pagina **[peticion de los agentes](#/request-agent/)**
