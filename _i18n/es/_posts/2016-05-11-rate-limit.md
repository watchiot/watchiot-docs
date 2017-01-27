---
title: 'Limite de peticiones'
description: 'Limite de peticiones'

category: 'api'
layout: blank
---

Cada peticion al servidor devuelve en la cabecera de la respuesta 4 llaves:

* **x-ratelimit-limit:** Define la cantidad de request total permitidos para ese *espacio* y *proyecto* 

* **x-ratelimit-remaining:** Define la cantidad de request que todavia puede realizar para ese *espacio* y *proyecto*

* **x-ratelimit-reset:** Define el tiempo en milisegundos restante para reiniciar todo a su valor inicial, por ejemplo
que *x-ratelimit-remaining* sea igual al total de request permitidos *x-ratelimit-limit*

* **retry-after:** Solo se devuelve como respuesta cuando *x-ratelimit-remaining* es igual a 0, o sea que el servidor
esta devolviendo *429 TOO MANY REQUESTS* y define la cantidad de segundos restante para que nuevamente se pueda realizar
un request sin que se devuelva *429 TOO MANY REQUESTS*

Ejemplo de cabecera de la respuesta:

{% highlight http %}

'x-ratelimit-limit': '10'
'x-ratelimit-reset': '1470008878'
'x-ratelimit-remaining': '0'
'retry-after': '433.202'

{% endhighlight %}