---
title: 'Autenticacion'
description: 'Autenticacion'

category: 'api'
layout: blank
---

Todas las peticiones necesitan ser autenticada. Para esto se envia las peticiones con la cabecera
**Authorization: {USERNAME} {API_KEY}**

{% highlight bash %}
Authorization: {USERNAME}_{API_KEY}
{% endhighlight %}

El **API_KEY** se genera cuando una cuenta es registrada.

El valor de su **API_KEY** lo puede encontrar en la configuracion de su cuenta
[{{site.url}}/{USERNAME}/setting#api]({{site.url}}/{USERNAME}/setting#api) ese valor usted puede modificarlo,
solicitando un nueva **API_KEY**, lo que no es recomendable ya que tiene que actualizar todos sus agentes con el nuevo **API_KEY**

El **API_KEY** es unico para cada cuenta en **WatchIoT**, lo que permite una identificacion efectiva de la cuenta
que esta realizando la peticion.

Sino se logra determinar la cuenta, debido a que es incorrecto la combinacion de **USERNAME** y **API_KEY** una respuesta
de no autorizacion sera recibido.

{% highlight http %}
HTTP/1.1 401 UNAUTHORIZED
Content-Type: application/json

{
    "code": 401,
    "msg": "UNAUTHORIZED",
    "error": {
        "description": "USERNAME or API_KEY incorrect."        
    }    
}
{% endhighlight %}

Solo se le puede realizar 10 peticiones cada 10 minuto que devuelvan **UNAUTHORIZED** para evitar ataques de fuerza bruta.
Si realizamos mas de 10 intentos fallidos en menos de 10 minutos recibiremos como respuesta auque la autenticacion sea correcta.

{% highlight http %}
HTTP/1.1 429 TOO MANY REQUESTS
Content-Type: application/json

{
    "code": 429,
    "msg": "TOO MANY REQUESTS",
    "error": {
        "description": "Many unauthorized request. You have to wait for 3242423 sec"
    }
}
{% endhighlight %}

Para mas detalles ver la pagina **[Limite de peticiones](#/rate-limit/)**

Para conocer mas sobre los posibles respuesta de errores acceder a [Errores](#/error/)