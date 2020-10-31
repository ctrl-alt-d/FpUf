# django - Introducció a les aplicacions II
## DAW-MP07-UF2 - Exercici de Generació dinàmica de pagines web.
Un cop finalitzat l'exercici [django - Introducció a les aplicacions](/DAW/DAW-MP07/DAW-MP07-UF2/django-introduccio-a-les-aplicacions/readme.md) el que farem és afegir lògica a la nostra aplicació.

1. Fes que es mostri, per a cada enquesta, les possibles opcions i els vots de cadascuna d'elles.
1. Fes que es pugui votar una opció en una enquesta. Per fer-ho, crea un enllaç a la url de votar.
1. Fes que només es pugui votar com a màxim 15 cops cada enquesta.
1. Mitjançant el framework de missatges de django fes que el programa confirmi la votació o mostri l'error.

Aquí una mica d'ajuda:

Vista per a votar:

```python
from django.http.response import HttpResponseRedirect
from django.core.urlresolvers import reverse
from django.contrib import messages
def vote(request, choice_id ):
    opcio = get_object_or_404(Choice, pk = choice_id)
    opcio.votes = opcio.votes + 1
    if opcio.votes > 15:
        #missatge error
        messages.error(request, 'Superat el màxim de votacions')
    else:
        #missatge ok
        opcio.save()
        messages.success(request, 'Has votat correctament')
    #Mostrar les vots d'aquesta enquesta:
```

        #Aproximació molt dolenta: No url friendly.
        #return detail(request, opcio.poll.pk )
        
        #Aproximació dolenta: url hardcoded
        #url_next = "/polls/" + str(opcio.poll.pk)
        #return HttpResponseRedirect( url_next )
        
        #ben fet:
        url_next = reverse( 'polls:detail', 
                            kwargs= { 'poll_id': 
                                      opcio.poll.pk } )
        return HttpResponseRedirect( url_next )
 
Template de l'enquesta que permet votar:

    <h1>{{ poll.question }}</h1>
    {% if messages %}
    <ul class="messages">
        {% for message in messages %}
        <li{% if message.tags %} class="{{ message.tags }}"{% endif %}>{{ message }}</li>
        {% endfor %}
    </ul>
    {% endif %}
    <ul>
    {% for choice in poll.choice_set.all %}
        <li><a href="{% url 'polls:vote' choice.id %}">{{ choice.choice_text }}</a> 
         --> {{choice.votes}}</li>
    {% endfor %}
    </ul>

---

#FpInfor #Daw #DawMp07 #DawMp07Uf02

* Resultats d'aprenentatge 1.g
* Continguts 1.7
---

###### Autor: daniel herrera 2013.12.11 17:47:07
###### Editat per: daniel herrera 2013.12.11 18:25:17
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
