---
title: 'Condiciones'
description: 'Condiciones'

category: 'config'
layout: blank
---

Una condicion dentro de los estados es la que determina si las metricas pertenecen a ese estado,
parar que las metricas se etiqueten como un estado es necesario que al evaluar la condicion se evalue como verdadera.

Cada estado solo puede definir una condicion y puede hacer uso de todas las metricas (variables), definiendo un predicado
como cualquier lenguaje de programacion con sus operadores mas comunes, mas el operador de expresion regular.

* Operadores booleanos: **&&**, **\|\|**, **!**
* Operadores binarios de comparacion: **==**, **<**, **>**, **<=**, **>=**, **!=**
* Operador binario de comparacion con expresiones regulares: **~=**
* Operadores de precedencia: **()**

Ejemplo de condicional dentro de un estado

{% highlight yaml %}
...

critical:
     when: (server_name == "my_server1" && free_space < 10) ||
           (server_name == "my_server2" && free_space <= 7)

{% endhighlight %}

Dentro de un estado definimos una etiqueta **when:** donde se configura la condicion que tiene que cumplir para que
las metricas pertenezcan a este estado.

Como se puede apreciar evaluamos que la variable **server_name** definida como parte de las metricas sea igual a la cadena
**"my_server1"** y tambien utilizamos operadores booleanos como **&&** y **\|\|**