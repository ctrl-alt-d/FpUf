# django: primera presa de contacte amb l'ORM de django
## DAW-MP07-UF3 - Exercici de Tècniques d’accés a dades.
1) Crea un entorn virtual ( `virtualenv env` ) i activa'l ( `source env/bin/activate` )

2) Instal·la el django dins aquest entorn virtual ( `pip install django` )

3) Crea un nou projecte ( `django-admin.py startproject blogging` ) i una nova aplicació dins el projecte ( `python manage.py startapp forums` ).

4) Modifica el fitxer `settings.py` per afegir l'aplicació que acabes de fer dins `INSTALLED_APPS`.

5) Crea els dos models dins `models.py`:

```python
from __future__ import unicode_literals
from django.db import models

class Blog( models.Model ):
	name=models.CharField(max_length=200,)

class Post( models.Model ):
	title=models.CharField(max_length=250,)
	content=models.TextField()
	blog=models.ForeignKey(Blog, on_delete=models.CASCADE)

```
6) Prepara les migracions `python manage.py makemigrations`

7) Executa les migracions `python manage.py migrate` i entra amb la shell de la base de dades per comprovar que les taules hi són ( `python manage.py dbshell` )

8) Afegeix un nou camp al model `Post` 

```python
num_likes = models.IntegerField()
```

9) Crea una nova migració ( `makemigrations` ) i executa-la ( `migrate` ).

10) Entrem a la shell ( `python manage.py shell` ) i creem blogs i posts:

```python
from forums.models import Blog, Post
cuina=Blog()
cuina.name = "La cuina de Karlos Arguiñano"
cuina.save()

pollastre_rostit = Post()
pollastre_rostit.title = "Pollastre rostit"
pollastre_rostit.content = """Agafem un pollastre, el pelem i el rostim
Això és tot """
pollastre_rostit.blog = cuina
pollastre_rostit.num_likes = 100
pollastre_rostit.save()

Post.objects.create( 
    title="fish and ships",
    content="pesquem un peix i li posem patates",
    num_likes = 9,
    blog = cuina )
```

11) Anem ara a fer consultes sobre els models persistits a la base de dades, farem servir la [QuerySet API](https://docs.djangoproject.com/en/1.10/ref/models/querysets/).

11.1 ) LLista tots els blogs mitjançant [all()](https://docs.djangoproject.com/en/1.10/ref/models/querysets/#all)

```python
for b in Blog.objects.all():
   print b.name
```

11.2) Llista els posts amb més de 2 likes usant [.filter](https://docs.djangoproject.com/en/1.10/ref/models/querysets/#filter)  i [__gte](https://docs.djangoproject.com/en/1.10/ref/models/querysets/#gte):

```python
for p in Post.objects.filter( likes__gte = 2 ):
   print p.blog.name, p.title
```

11.3) Llista tots els blogs amb un post que contingui la paraula 'pollastre' al títol, cal fer servir [__icontains](https://docs.djangoproject.com/en/1.10/ref/models/querysets/#icontains):

```python
for b in ( Blog
          .objects
          .filter( post__title__icontains = 'pollastre')
          .distinct()
          ):
   print b.name
```

11.4) Llista tots els blogs amb un post que contingui la paraula 'pollastre' al títol o al contingut, cal fer servir [__icontains](https://docs.djangoproject.com/en/1.10/ref/models/querysets/#icontains) i també [Q() Objects](https://docs.djangoproject.com/en/1.10/ref/models/querysets/#q-objects):

```python
from django.db.models import Q
q_al_titol = Q( post__title__icontains = 'pollastre' )
q_al_contingut = Q( post__content__icontains = 'pollastre' )
```

    for b in ( Blog
              .objects
              .filter( q_al_titol | q_al_contingut )
              .distinct()
              ):
       print b.name

11.5) Pren el blog que té per nom 'Blog de cuina', fer servir [get](https://docs.djangoproject.com/en/1.10/ref/models/querysets/#get):

```python
b = ( Blog
     .objects
     .get( name__iexact = 'Blog de cuina') )
```

    print b.name

11.6) Mostra el títol dels blocs i al costat el número de posts de cada blog:

```python
#opció amb anotacions:
from django.db.models import Count
for b in ( Blog
          .objects
          .annotate( n_blogs=Count( 'post' ) ) 
          ):
   print b.name, b.n_blogs
```

    #opció amb anotacions:
    for b in ( Blog
              .objects
              .all()
              ):
       print b.name, b.post_set.count()

Quina opció et sembla més eficient i per què? En comptes de mostrar el número de blog, ara, compte el total de Likes.

11.7) Proba a consultar l'[sql que hi ha darrera de cada consulta](http://stackoverflow.com/a/3748307):

    >>> queryset = MyModel.objects.all()
    >>> print queryset.query
    SELECT "myapp_mymodel"."id", ... FROM "myapp_mymodel"

11.8) LLegeix sobre com fer agregacions: [Aggregation](https://docs.djangoproject.com/en/1.10/topics/db/aggregation/)

**Solucions**

* [Creant el model i les migracions](https://youtu.be/51wYFWV3J0s)
* [Inserint dades](https://youtu.be/xYaDKuwEQ7U)

---

#FpInfor #Daw #DawMp07 #DawMp07Uf03

---

###### Autor: daniel herrera 2016.11.14 15:03:46
###### Editat per: daniel herrera 2016.11.15 15:05:30
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
