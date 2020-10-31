# django - Fent consultes sobre models
## DAW-MP07-UF3 - Exercici de Tècniques d’accés a dades.
La [QuerySet API](https://docs.djangoproject.com/en/dev/ref/models/querysets/) és la funcionalitat de django que ens permet realitzar consultes sobre models.

Exercicis:

1. Donada una query, exemple: `Clients.objects.all()`, en quin moment s'executa? ( ['When query is evaluated?'](https://docs.djangoproject.com/en/dev/ref/models/querysets/#when-querysets-are-evaluated) )
2. Crea al menys 5 consultes sobre els models de l'exercici [django - Definint models](/DAW/DAW-MP07/DAW-MP07-UF3/django-definint-models/readme.md) utilitzant [mètodes que retornin querysets](https://docs.djangoproject.com/en/dev/ref/models/querysets/). Exemples:
    2. Tots els clients.
    2. Totes les Factures.
    2. Totes les Factures d'un determinat client:
        2. A partir del client amb la propietat de navegació: `unClient.factura_set.all()`
        2. Filtrant per client: `Factura.objects.filter( client = unClient ).all()`
    2. Tots els productes d'una determinada categoria a través de la propietat de navegació.
    2. Tots els clients que hagin comprat un determinat producte: `Client.filter( factura__liniadefactura__producte = unProducte ).distinct().all()` 
2. Modifica les consultes anteriors afegint [mètodes que no retornin querysets](https://docs.djangoproject.com/en/dev/ref/models/querysets/#methods-that-do-not-return-querysets). Exenples:
    2. Número total de Factures.
    2. En comptes de retornar el model `Client` que retorni una llista únicament amb els noms dels clients. `values_list( 'nom' , flat=True )`
2. Modifica les consultes del punt 2 tot afegint [field lookups](https://docs.djangoproject.com/en/dev/ref/models/querysets/#field-lookups). Exemples:
    2. Tots els clients que [continguin](https://docs.djangoproject.com/en/dev/ref/models/querysets/#contains) la lletra 'A' al seu nom. 
    2. Tots els clients que [continguin](https://docs.djangoproject.com/en/dev/ref/models/querysets/#icontains) la lletra 'A' al seu nom. Sense tenir en compte majúscules o minúscules.
    2. Tots els clients que hagin comprat algun producte  d'import superior a 10€. `Client.filter( factura__liniadefactura__producte__preu__gt = 10 ).distinct().all()`
1. Aconsegueix veure la consulta SQL que generarà la query anterior.

    
    





---

#FpInfor #Daw #DawMp07 #DawMp07Uf03

* Resultats d'aprenentatge 1.c
* Continguts 1.3
---

###### Autor: daniel herrera 2013.11.20 14:46:36
###### Editat per: daniel herrera 2015.11.09 13:44:45
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
