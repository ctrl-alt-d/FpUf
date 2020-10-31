# django - Definint models
## DAW-MP07-UF3 - Exercici de Tècniques d’accés a dades.
Un cop [familiaritzat amb django](/DAW/DAW-MP07/DAW-MP07-UF3/django-introduccio-als-models/readme.md) pots passar a fer aquest exercici.

Consulta el punt [Models](https://docs.djangoproject.com/en/1.8/topics/db/models/) per a fer aquest exercici. ( No treballarem amb herència, tampoc amb proxy models.)

Crea els models:

* Client ( nif, nom )
* Categoria ( nom )
* Producte ( nom, talla, preu )
* Factura ( data, descripció, lloc d'entrega, data_cobrament )
* LiniaDeFactura ( quantitat )

De manera que:

* Deixa que django crei els identificadors dels models.
* Una factura referencia un client ( clau forana a client )
* Un *producte* pot pertànyer a diverses *categories*.
* El *NIF* a client i el nom de la *categoria* és únic.
* *LiniaDeFactura* és una relació many-to-many entre *factura* i *producte* amb atributs (quantitat).
* Dins de *LiniaDeFactura*, el parell *factura* i *producte* és únic.
* A la *factura* apareix la *data*, una *descripció* i el *lloc d'entrega*, aquest darrer es pot deixar en [blanc](https://docs.djangoproject.com/en/1.8/ref/models/fields/#django.db.models.Field.blank). Els texts amb longitud màxima 120.
* Dins productes trobem un '[choice](https://docs.djangoproject.com/en/1.8/ref/models/fields/#django.db.models.Field.choices)' que ens diu la *talla* (Metit, Mitjà, Gran).
* Tots els atributs han de tenir *[help_text](https://docs.djangoproject.com/en/1.8/ref/models/fields/#help-text)*, el necessitarem més endavant quan fem formularis.
* Els atributs que sigui necessari cal que tinguin *verbose_name* ( *lloc d'entrega*, *descripció* )
* Les *factures* s'[ordenen](https://docs.djangoproject.com/en/dev/ref/models/options/#django.db.models.Options.ordering) per *data* de més nou a més vell.
* Els *productes* per ordre alfabètic
* Les *factures* tenen *data de cobrament* que pot ser [null](https://docs.djangoproject.com/en/1.8/ref/models/fields/#null).
* Crea [custom method](https://docs.djangoproject.com/en/1.8/topics/db/models/#model-methods) que et digui si una *factura* està cobrada.
* Tots els models tindràn definit [__unicode__](https://docs.djangoproject.com/en/1.8/ref/models/instances/#django.db.models.Model.__unicode__) (o __str__ si ho fas amb python 3)

Inserta les següents dades als models:

* Categories: Refrigerats, Món bebé, Higene, Roba, Espies
* Productes: Batut fresc 0 anys, Bolquers, Bolígraf espia, Samarreta AC DC (posa les talles que vulguis i les categories apropiades)
* Clients: Julian (Nif: 1234A), Claude (Nif: 9876B)
* Factures: 
    * 1/10/2013 Julian compra el 3 Batuts i 6 Bolquers
    * 3/10/2013 Julian compra 2 Samarreta AC DC
    * 8/11/2013 Claude compra Bolígraf espia

**Videotutorials**

* [Introducció django - Creació de l'entorn](http://youtu.be/6W6hyn3tpwU) 4'
* [Introducció django - Creació dels models](http://youtu.be/F2MbJAIwHY0) 23'
* [Introducció django - Creació dels models OMG (Oh my God)](http://youtu.be/KAxGKwdPErY) 4'
* [Introducció django - Inserció dades](http://youtu.be/5i0sn5fcijc) 11'
* [Introducció django - Bonus Track django admin](http://youtu.be/5DADoivl2Jc) 3'

** Resolució exercici django - Definint models **

1. Creació entorn virtual  

    1. Instal·lar requeriments virtualenv  ✓
    1. Creació entorn virtual              ✓
    1. Activar entorn                      ✓
    1. Instal·lació requeriments django    ✓

2. Creació del projecte i les aplicacions

    1. Creació del projecte                                ✓
    1. Creació de les aplicacions i posar-les al projecte  ✓
    1. Creació dels models                                 ✓
    1. Creació de la base de dades                         ✓

3. Insertant dades 

    1. Insertant dades amb nou model: Client()                ✓
    1. Insertant dades amb el manager: Client.object.create() ✓
    1. Informant relacions N:M sense atributs                 ✓
    1. Informant relacions N:M amb atributs                   ✓

4. Bonus track. django admin ✓

    


---

#FpInfor #Daw #DawMp07 #DawMp07Uf03

* Resultats d'aprenentatge 1.b 1.c 1.d 1.e
* Continguts 1.2 1.3 1.4 1.5
---

###### Autor: daniel herrera 2013.11.11 14:38:04
###### Editat per: daniel herrera 2015.11.02 16:14:52
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
