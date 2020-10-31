# django - Construcció d'un Web Service senzill
## DAW-MP07-UF4 - Exercici de Serveis web. Pàgines dinàmiques interactives. Webs Híbrids.
Es tracta de crear un Web Service REST sencill.

**Preparatius**

* Fes un nou projecte anomenat `recursos_humans`.
* Fes una nova aplicació anomenada `personal`.
* Fes un nou model anomenat `Persona`, ha de tenir Id (serveix l'implícit del model), Nom, Cognoms.
* Instal·lat alguna llibreria per a crear 'fake data' i crea al menys 1000 persones.

**Desenvolupament**

* Crea una vista que, donats els paràmetres GET `nom` i `max` ens torni, via JSON un màxim de `max` persones que continguin `nom` al seu nom o cognoms.
* També retornarà, al mateix JSON el total de persones que compleixen amb el criteri.

**Proves**

* Provaràs el projecte des del navegador. Exemple de crida:

    http://127.0.0.1:8000/api?nom=smith&max=50

**Entregables**

* Documentació del projecte.
* Documentació de la vista.
* Exemples d'execució.

**Ajuda**



```python
from django.http import HttpResponse
from django.db.models import Q
import json

#recollim els paràmetres
cadena_a_buscar = request.GET.get( 'nom', '' )
max_a_mostrar = request.GET.get( 'max', 100 )
```

    #preparem la consulta, és complexa, fem servir Q  (*1)
    q_str_in_nom = Q( nom__contains = cadena_a_buscar )
    q_str_in_cog = Q( cognom__contains = cadena_a_buscar )
    noms_que_contenen_string = Persona.objects.filter( q_str_in_nom | q_str_in_cognom )

    #preparem la llista de noms a enviar
    llista_persones = [ {"id": p.id, 
                         "nom": "{0}, {1}".format( p.cognom, p.nom )           
                        } for p in noms_que_contenen_string[:max_a_mostrar]
                      ] 

    #preparem el diccionari que retornarem
    response_data = {}
    response_data['total'] = noms_que_contenen_string.count()
    response_data['persones'] = llista_persones

    #Enviem resposta indicant que és json
    return HttpResponse(json.dumps(response_data), content_type="application/json")


(*1) Per a [consultes complexes django utilitza Q](https://docs.djangoproject.com/en/dev/topics/db/queries/#complex-lookups-with-q-objects).    

**I ara què?**

Un cop finalitzada aquesta pràctica has de realitzar aquesta altre: [django - Consumir Web Service senzill amb AJAX](/DAW/DAW-MP07/DAW-MP07-UF4/django-consumir-web-service-senzill-amb-ajax/readme.md)


---

#FpInfor #Daw #DawMp07 #DawMp07Uf04

---

###### Autor: daniel herrera 2014.02.21 14:16:20
###### Editat per: daniel herrera 2014.02.27 07:58:06
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
