---
title: 'Peticiones de un agente'
description: 'Peticiones de un agente'

category: 'api'
layout: blank
---

Cada **[proyecto](#/project/)** puede tener N-agentes recolectando las metricas en distintos servidores o *endpoints*.
La *API* solo puede recibir 60 peticione por hora en cada proyecto en el plan *free*, osea que si tenemos 4 agentes recolectando
informacion de los recursos como el disco duro o la memoria, cada uno podra enviar las metricas cada 4 minutos. Si se excede
las 60 peticiones por hora, se recibe la siguiente respuesta, hasta que pase la hora:

{% highlight http %}
HTTP/1.1 429 TOO MANY REQUESTS
Content-Type: application/json

{
    "code": 429,
    "msg": "TOO MANY REQUESTS",
    "error": {
        "description": "You limit request per project is 60/hr. You have to wait for 135654 sec"
    }
}
{% endhighlight %}

Si usted necesita aumentar la frecuencia de recoleccion de metricas, por favor pongase en contacto con nosotros para que conozca
como poder incrementarla.

Si se tiene configurado en el **proyecto** las restriccion desde que **IPs** se pueden enviar las peticiones, los agentes
deben enviar las metricas detras de las **IPs** configuradas. Para saber mas sobre restricciones de **IPs** acceder a la pagina
**[IPs](#/ip/)**

La peticion envia los datos en **JSON**. El siquiente es un ejemplo de
peticion enviada por un agente:

{% highlight bash %}
curl --request POST \
  --url {{site.url_api}}/{MY_SPACE}/{MY_PROJECT} \
  --header 'Authorization: {USERNAME} {API_KEY}'
  --data '{
            metrics:
            {
                param1: "value1",
                param2: "value2",
                param3: "value3",
                ...
            }
          }'
{% endhighlight %}

La peticion se realiza por *POST* a la *URL* "/{MY_SPACE}/{MY_PROJECT}" para refenciar el proyecto
al cual se le envia las metricas.

Como se observa contamos con la entrada *metrics* que es obligatoria y dentro los nombre de las metricas con sus 
respectivos valores *param1: "value1"*.

Si algunos de los nombres de las metricas que se envian no coinciden con las que estan configuradas en el **YAML** o
presentan un tipo de dato no esperado se obtiene como respuesta

{% highlight http %}
HTTP/1.1 400 BAD REQUEST
Content-Type: application/json

{
    "code": 400,
    "msg": "BAD REQUEST",
    "error": {
        "description": "Errors into the metrics.",
        "fields": {
            "param1": "The metric param1 does not exist into the configuration yml project.",
            "param2": "The value type of metric param2 has to be number."
        }
    }    
}
{% endhighlight %}
