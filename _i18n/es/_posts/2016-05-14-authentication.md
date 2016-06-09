---
title: 'Autenticacion'
description: 'Autenticacion'

category: 'api'
layout: blank
---

Todas las peticiones necesitan ser autenticada. Para esto se envia las peticiones con la cabecera
**Authorization: {USERNAME}_{API_KEY}**

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
{% endhighlight %}

Solo se le puede realizar 3 peticiones cada 10 minuto que devuelvan **UNAUTHORIZED** para evitar ataques de fuerza bruta.
Si realizamos mas de 3 intentos fallidos en menos de 10 minutos recibiremos como respuesta.

{% highlight http %}
HTTP/1.1 429 Too Many Requests
{% endhighlight %}

Para conocer mas sobre los posibles respuesta de errores acceder a [Errores](#/error/)