---
title: 'Peticiones de un agente'
description: 'Peticiones de un agente'

category: 'api'
layout: blank
---

Cada **[proyecto](#/project/)** puede tener N-agentes recolectando las metricas en distintos servidores o *endpoints*.
La *API* solo puede recibir dos peticiones por minutos en cada proyecto en el plan *free*, osea que si tenemos 4 agentes recolectando
informacion de los recursos como el disco duro o la memoria, cada uno podra enviar las metricas cada dos minutos. Si se excede
el numero de peticiones por minuto, se recibe la siguiente respuesta:

{% highlight http %}
HTTP/1.1 429 TOO MANY REQUESTS
Content-Type: application/json

{
    code: 429,
    msg: "Rate limit exceeded"
}
{% endhighlight %}

Si usted necesita aumentar la frecuencia de recoleccion de metricas, por favor pongase en contacto con nosotros para que conozca
como poder incrementarla.

Si se tiene configurado en el **proyecto** las restriccion desde que **IPs** se pueden enviar las peticiones, los agentes
deben enviar las metricas detras de las **IPs** configuradas. Para saber mas sobre restricciones de **IPs** acceder a la pagina
**[IPs](#/ip/)**

La peticion envia los datos en **JSON** siendo obligatorio los valores dentro de *params*. El siquiente es un ejemplo de
peticion enviada por un agente:

{% highlight bash %}
curl --request POST \
  --url {{site.url_api}}/{MY_SPACE}/{MY_PROJECT} \
  --header 'Authorization: {USERNAME} {API_KEY}'
  --data '{
            params:
            {
                param1: "value1",
                param2: "value2",
                param3: "value3",
                ...
            },
            notifOnly:
            {
                when: "critical"
                type: "email",
                data:
                {
                    to: "other_email@company.com",
                    subject: "Nuevo subjects"
                }
            }
          }'
{% endhighlight %}

La peticion se realiza por *POST* a la *URL* "/{MY_SPACE}/{MY_PROJECT}" para refenciar el proyecto
al cual se le envia las metricas.

Como se observa contamos con la entrada *params* que es obligatoria y dentro los nombre de las metricas con sus respectivos valores
*param1: "value1"*.

Opcional tenemos la entrada *notifOnly* que su funcion es sobreescribir el comportamiento definido
en la **YAML** de la configuracion del **proyecto** para la recolecion de metricas de un agente en especifico.

El parametro *notifOnly* es util para cuando queremos que uno de los agentes notifique solo cuando un estado sea valido y que se notifique
por una sola via, en ves de como puede estar configurado el **YAML** en el proyecto, que puede estar configurado para que
notifique en diferentes estados, por diferentes vias y a varias personas.

Si algunos de los nombres de las metricas que se envian no coinciden con las que estan configuradas en el **YAML** se obtiene como respuesta

{% highlight http %}
HTTP/1.1 400 BAD REQUEST
Content-Type: application/json

{
    code: 400,
    msg: "The param(s) {param1, param2} do(es) not exist"
}
{% endhighlight %}

Si alguno de los parametros de *notifOnly* no son validos se ignora, pero recibe una alerta como respuesta.

{% highlight http %}
HTTP/1.1 200
Content-Type: application/json

{
    code: 200,
    msg: "The value of parameter 'type' in notifOnly is not valid"
}
{% endhighlight %}

## Sobreescribiendo la configuracion

Sobreescribir el comportamiento de notificacion a la hora de procesar las metricas enviadas depende del tipo de
notificacion y los parametros que este maneja. Por ejemplo en el tipo de notificacion *email*, podemos sobreescribir
los parametros de destino o subject. Los parametros que se van a sobreescribir en dependencia del tipo de notificacion
se agrupan dentro del *Object* data

{% highlight json %}
data:
{
    to: "other_email@company.com",
    subject: "Nuevo subjects"
}
{% endhighlight %}

### Parametros que se pueden sobreescribir en la notificacion de email

 * **to:** Los correos que se deben notificar
 * **subject:** El asunto del correo
 * **body:** El cuerpo del correo

### Parametros que se pueden sobreescribir en la notificacion de webhook

 * **url:** La URL que se debe llamar