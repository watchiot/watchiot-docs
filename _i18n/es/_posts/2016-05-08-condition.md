---
title: 'Condiciones'
description: 'Condiciones'

category: 'config'
layout: blank
---

Una condicion dentro de un [estado](#/states/) es la que determina si las metricas pertenecen a ese estado,
parar que las metricas se etiqueten como un estado es necesario que la evaluacion de la condicion sea  verdadera.

Cada estado solo puede definir una condicion y puede hacer uso de todas las metricas (variables), definiendo un predicado
como cualquier lenguaje de programacion con sus operadores mas comunes, mas el operador de expresion regular.

* Operadores booleanos: **&&**, **\|\|**, **!**
* Operadores binarios de comparacion: **==**, **<**, **>**, **<=**, **>=**, **!=**
* Operadores de precedencia: **()**

Ejemplo de condicional dentro de un estado

{% highlight yaml %}
...

critical:
     when: (server == "my_server1" && free_space < 10) ||
           (server == "my_server2" && free_space <= 7)

     ...
...
{% endhighlight %}

Dentro de un estado definimos una etiqueta **when:** donde se configura la condicion que tiene que cumplir para que
las metricas pertenezcan a este estado.

Como se puede apreciar evaluamos que la variable **server** definida como parte de las metricas sea igual a la cadena
**"my_server1"** y tambien utilizamos operadores booleanos como **&&** y **\|\|** y de precedencia **()**