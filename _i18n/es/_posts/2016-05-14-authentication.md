---
title: 'Autenticacion'
description: 'Autenticacion'

category: 'api'
layout: blank
---

Todas las peticiones a la **API** deberan ser autenticadas utilizando la cabecera **Authorization: API_KEY** en
todas las peticiones.

{% highlight bash %}
Authorization: YOUR_API_KEY
{% endhighlight %}

El **API_KEY** se genera cuando una cuenta es registrada.

El valor de su **API_KEY** lo puede encontrar en la configuracion de su cuenta
[{{site.url}}/{my_account}/setting#api]({{site.url}}/my_account/setting#api) ese valor usted puede modificarlo,
solicitando un **API_KEY** nueva, lo que tiene que modificar todos sus agentes con el nuevo **API_KEY**

El **API_KEY** es unico para cada cuenta en **WatchIoT**, lo que permite una identificacion efectiva de la cuenta
que esta realizando la peticion.

Sino se logra determinar la cuenta, debido a que es incorrecto el **API_KEY** una respuesta de no autorizacion sera
recibido.

{% highlight http %}

HTTP/1.1 401 UNAUTHORIZED
{% endhighlight %}

Para conocer mas sobre los posibles respuesta de errores acceder a [Errores](#/error/)