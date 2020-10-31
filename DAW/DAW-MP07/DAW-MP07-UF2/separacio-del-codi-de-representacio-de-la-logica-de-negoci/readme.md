# Separació del codi de representació de la lògica de negoci
## DAW-MP07-UF2 - Exercici de Generació dinàmica de pagines web.
Separar el codi de representació de la lògica de negoci és un objectiu ambiciós. En una aplicació web tenim:

1. **La interfície d'usuari**. Capa que s'encarrega del diàleg amb l'usuari.
2. **La lògica de control**. Capa que s'encarrega del diàleg entre la interfície d'usuari i la lògica de negoci.
3. **Els models de dades**. Capa que s'encarrega de la representació de les dades, el seu control i la seva persistència.

Aquestes tres capes poden estar més o menys imbricades. Per exemple si fem servir PHP sense cap framework tindrem les tres capes completament barrejades, si utilitzem un framework o patrons, podrem organitzar la nostre aplicació independitzant aquestes capes.

Tot i això, en aquest punt s'amaga una petita trampa, on posem les 'regles de negoci'. Per exemple: *'No es pot afegir una línia de factura a una factura ja servida'*. 
La manera fàcil de fer-ho és implementar aquesta regla a la lògica de control, si ho fem així ens haurem d'enrecordar de fer-ho a tots els punts on s'editi aquest model. Però, de manera ideal, aquesta regla hauria de ser implementada a la capa del model, d'aquesta manera la validació sempre es farà. Hi ha frameworks que això ens ho permeten fer:

* Exemple de validació de regles de negoci amb la [fluent api de entity framework](http://msdn.microsoft.com/en-us/data/gg193959.aspx)

* Exemple de definició de [regles de negoci al propi model amb django](https://docs.djangoproject.com/en/dev/ref/models/instances/#django.db.models.Model.clean).

**Exercicis**:

1. On hem d'escriure les regles de negoci, a la capa de lògica de control o a la capa de model?
1. Identifica la línia de codi que fan servir a l'exemple de django per 'disparar' un error de validació i explica, quina regla han comprovat a l'exemple.
1. Identifica la línia de codi que fan servir a l'exemple de Entity Framework per 'disparar' un error de 'regles de negoci' i explica, quina regla han comprovat a l'exemple.
1. Consulta la pàgina [Writing your first Django app, part 3](https://docs.djangoproject.com/en/1.6/intro/tutorial03/) i contesta les següents preguntes:
    1. Què és una vista a django?
    1. Qui s'encarrega de fer de *controlador* a django?
    1. Què és un template a django?

2. Consulta la pàgina [ASP.NET MVC](http://www.asp.net/mvc)
    1. Navega fins a 'What is MVC i contesta: què és una vista? Que és un controlador? Què és un model?
    2. Dins aquesta mateixa pàgina, quin considera microsoft més complexe d'usar per a un desenvolupador? El MVC o el Web Forms?
    





---

#FpInfor #Daw #DawMp07 #DawMp07Uf02

* Resultats d'aprenentatge 1.a
* Continguts 1.1
---

###### Autor: daniel herrera 2013.11.27 09:17:17
###### Editat per: daniel herrera 2013.11.27 09:22:34
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
