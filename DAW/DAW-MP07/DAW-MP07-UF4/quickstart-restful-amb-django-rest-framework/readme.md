# Quickstart RESTful amb django-rest-framework
## DAW-MP07-UF4 - Exercici de Serveis web. Pàgines dinàmiques interactives. Webs Híbrids.
Un cop completat l'exercici [Introducció a ReST i ReSTful](/DAW/DAW-MP07/DAW-MP07-UF4/introduccio-a-rest-i-restful/readme.md) pots passar a implementar un servei ReSTful amb django.

Per tal de mantenir-nos en la filosofia DRY i no haver de reinventar la roda, utilitzarem un paquet REST ja existent. En aquest cas farem servir django-rest-framework.org

En aquesta pràctica primer prepararem dades de prova i després crearem un servei ReSTful per tal que es puguin manipular.

Creació de l'entorn de proves
====

Ens cal un nou projecte anomenat `testrest`. En aquest projecte crearem l'aplicació `Persones`. Crearem 10.000 persones a la base de dades. El model persona és el següent:

```python
# encoding: utf-8
from __future__ import unicode_literals
from django.db import models
```

    class Persona (models.Model):
        nom=models.CharField(max_length=300, help_text="Nom.")
        cognom=models.CharField(max_length=400, help_text="Cognom.")

Insertarem persones amb noms i cognoms a l'atzar. Pots agafar llista de noms i cognoms de l'[aplicació djAu](https://github.com/ctrl-alt-d/django-aula/blob/master/demo/helpers/nomsICognoms.py):

```python
import nomsICognoms
for _ in range(0,10000)
    p=Persona()
    p.nom = random.choice( nomsICognoms.noms ).capitalize(),
    p.cognom = u"{c1} {c2}".format( c1 = random.choice( nomsICognoms.cognoms ).capitalize() ,
                                     c2 = random.choice( nomsICognoms.cognoms ).capitalize() )
    p.save()
```


Creació del servei ReSTful
====

Seguirem el [quickstart de django-rest-framework](http://www.django-rest-framework.org/tutorial/quickstart/) tot adaptant-lo al nostre model Personas.

Instal.lació de django-rest-framework
=====

    pip install djangorestframework

Creació dels serializers
=====

Crearem el fitxer `testrest/persones/serializers.py` amb el següent contingut:

```python
from rest_framework import serializers
from persones.models import Persona
```

    # Serializers define the API representation.
    class PersonaSerializer(serializers.HyperlinkedModelSerializer):
        class Meta:
            model = Persona
            fields = ('id', 'nom', 'cognom')

Creació de les vistes
=====

Al fitxer `testrest/persones/views.py` inclourem les vistes ReST:

```python
from persones.models import Persona
from rest_framework import viewsets
from persones.serializers import PersonaSerializer
```

    # ViewSets define the view behavior.
    class PersonaViewSet(viewsets.ModelViewSet):
        queryset = Persona.objects.all()
        serializer_class = PersonaSerializer

Fixa't que prodriem crear múltiples views, però per aquest exemple fem servir un ViewSet que les engloba totes. Caldrà crear views specialitzades quan els requeriments així ens ho indiquin.

URLs
=====

Cal tocar el fitxer `urls.py` del projecte per tal que serveixi les vistes creades:

```python
from django.conf.urls import url, include
from persones import views as persones_views
from rest_framework import routers
router = routers.DefaultRouter()
router.register(r'rest-persones', persones_views.PersonaViewSet)
urlpatterns = [
    #url(r'^persones/', include('persones.urls', namespace="persones")),
    url(r'^', include(router.urls)),
    url(r'^api-auth/', include('rest_framework.urls', namespace='rest_framework'))
]
```

Com que estem treballant amb viewset i no pas amb views, podem generar automàticament la configuració d'URL per a la nostre API simplement registrant el viewset amb una classe router.

De nou, si necessitem més control sobre les URLs de l'API ens caldria esmicolar la API en classes individuals ( en comptes de la classe general ViewSet ) i escriure configuració específica per a les URLs.

A més de registrar el *router* també es registren les vistes de login i logut que es poden usar amb el navegadorself.

Settings
=====

Cal modificar el fitxer settings de l'aplicació per tal de que els resultats ens apareguin paginats ( no volem una única resposta amb les 10.000 persones, les volem paginades ). També definim quin tipus de seguretat volem:

```python
INSTALLED_APPS = (
    ...
    'rest_framework',
)
```

    REST_FRAMEWORK = {
        #'DEFAULT_PERMISSION_CLASSES': ('rest_framework.permissions.DjangoModelPermissionsOrAnonReadOnly'),
        #'DEFAULT_PERMISSION_CLASSES': ('rest_framework.permissions.IsAdminUser',),
        'DEFAULT_PERMISSION_CLASSES': ( 'rest_framework.permissions.AllowAny',),
        'DEFAULT_PAGINATION_CLASS': 'rest_framework.pagination.LimitOffsetPagination',
        'PAGE_SIZE': 15
    }

Fixa't en les opcions comentades i investiga per a que serveixen.

>Ja tens el teu servei ReSTful a punt!

Provant el servei
=====

Pots provar el servei amb la comanda curl:

```bash
curl -H 'Accept: application/json; indent=4' -u paco:malagon "https://ajax-danihp.c9users.io/rest-persones/"
```

![consumir amb curl](http://i.imgur.com/CPMyjUO.png)

Aquest framework també ens ofereix una interface d'usuari web per a consumir el servei:

![interface web](http://i.imgur.com/QnbEhXP.png)

![interface web 2](http://i.imgur.com/aFqVgVv.png)

Prova també desborrar dades via curl: [How to delete an object using Django Rest Framework](http://stackoverflow.com/a/26445632/842935):

    curl -X DELETE "https://ajax-danihp.c9users.io/rest-persones/3/"

Entregables
====

* Cal entregar la documentació de la pràctica, un pdf amb el codi i les captures de pantalla de l'app en funcionament, amb diferents testos a les diferents crides.
* Per a fer aquesta pràctica hem fet servir un framework que ens allibera d'haver d'escriure codi repetitiu. Però, quin seria aquest codi?
    * Quin seria el codi per detectar el tipus de verb que t'arriba?
    * Quin seria el codi per a serialitzar i enviar els models amb json?
    * Quin seria el codi per fer una actualització de les dades que t'arriben via json?



Segona Part
======

Anem ara a provar la [API usant class-based views](http://www.django-rest-framework.org/tutorial/3-class-based-views/#rewriting-our-api-using-class-based-views)

Caldrà fer dues classes `PersonaList` i `PersonaDetail`. Fes dues entrades al fitxer `urls.py`, una per cada classe igual que fa la documentació. Cada classe, internament, servirà els diferents verbs. Exemple de la classe que manega un membre:
    
```python
class PersonaDetail(APIView):
    """
    Retrieve, update or delete a Persona instance.
    """
    def get_object(self, pk):
        try:
            return Persona.objects.get(pk=pk)
        except Persona.DoesNotExist:
            raise Http404

    def get(self, request, pk, format=None):
        persona = self.get_object(pk)
        serializer = PersonaSerializer(persona)
        return Response(serializer.data)

    def put(self, request, pk, format=None):
        persona = self.get_object(pk)
        serializer = PersonaSerializer(persona, data=request.data)
        if serializer.is_valid():
            serializer.save()
            return Response(serializer.data)
        return Response(serializer.errors, status=status.HTTP_400_BAD_REQUEST)

    def delete(self, request, pk, format=None):
        persona = self.get_object(pk)
        persona.delete()
        return Response(status=status.HTTP_204_NO_CONTENT)
```

Tercera Part
=============

Prova a serialitzar un model relacionat. Crea el model 'Departament' i assigna cada persona a un 'Departament'. Quan serialitzis la persona inclou el departament.

Caldrà fer el serialitzador de 'Departament' i incloure'l al serialitzador de persona. Aquí tens un exemple amb 'Vi' i 'Ampolla':

[Django Rest Framework - Get related model field in serializer](http://stackoverflow.com/questions/20633313/django-rest-framework-get-related-model-field-in-serializer)

---

#FpInfor #Daw #DawMp07 #DawMp07Uf04

---

###### Autor: daniel herrera 2016.03.08 10:20:54
###### Editat per: daniel herrera 2017.03.21 16:12:43
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
