# django - Formularis IV
## DAW-MP07-UF2 - Exercici de Generació dinàmica de pagines web.
Records Arcade
====

Un grup d'amics vol una base de dades per emmagatzemar els rècords que fan als jocs arcade.

Per això es creen aquests models:

* Gamer ( Nick, nom, cognoms, email, nivell )
* Joc ( Nom, Released (és un enter), Developer, Publisher )
* Rècord ( gamer, joc, dia i hora, lloc, punts )

*Nota: els nivells només poden ser: megamaster, master, pardillo.*

![Imatge de la wikipedia](http://upload.wikimedia.org/wikipedia/en/1/1d/SF2_JPN_flyer.jpg)


**Es demana**

1. Script python per a crear 4 gamers i 3 jocs (mirar ajuda).
1. Home page amb la llista tots els records ordenats per joc i puntuacio  `records=Record.objects.order_by( 'joc__nom', '-puntuacio').all() `. Podeu mostrar el nom del joc, la puntuació i el gamer: `{% for r in records %}{{ r.gamer.nic}} - ... - {% endfor %}`. Cada record tindrà enllaç per poder-lo editar: `{% url 'records:edita_record' r.id %}`
2. Vista amb modelForm per editar ó crear rècords segons parametre opcional 'id_record' 

**Requerimets**

1. El projecte es dirà 'arcade' seguit de les teves inicials. Si et dius 'Jaume Garcia' serà 'arcadejg'.
1. El projecte tindrà dues aplicacions: 'gamers' i 'records'
1. L'aplicació `gamers` tindrà els gamers, els altres models seran a `records`.
1. Les urls de l'aplicació `records` tindran el seu propi namespace.
1. Per crear nous rècords usarem al template: `{% url 'recordsns:nou_record' %}
1. Per editar entrades de rècords usuarem al template: `{% url 'recordsns:edita_record' r.id %}`
1. Un cop donat d'alta un rècord anirem a l'arrel, opcional fer-ho amb `reverse` o hardcoded.
1. La vista que crea / edita rècords es dirà `vw_record`



**Ajuda**


    Nom, Released, Developer, Publisher = 0, 1, 2, 3
    jocs = [ ("Donkey Kong", 1981, "Nintendo", "Nintendo" ),
             ("Ms. Pac-Man", 1981, "General Computer Corp.", "Bally Midway" ),
             ("Street Fighter II: The World Warrior", 1991, "Capcom", "Capcom" ),
           ]
    for joc in jocs:
        print ( joc[Nom], joc[Released], joc[Developer], joc[Publisher] )

Recorda que el patró per a una pantalla de creació / edició és el següent:


    ::bash
    vista vw_record( request, id_record = None ):
        si ens informen id_record llavors:
            record = buscar_record_per_id ( id_record )
        en cas contrari:
            record = nou_record()
    
        si rebo dades via post:
            form = el_model_form( dades_rebudes, instancia = record)
            si form.is_valid() llavors:
                //cas 1
                form.save()
                afegir a missatgeria que tot ha anat bé
                redirecció a alguna banda
            en cas contrari:
                //cas 2
                afegir a missatgeria que tot ha fallat
        en cas contrari:
            //cas 3
            form = el_model_form( instancia = record)
    
        retornar el form renderitzat


**Entregables**

1. Document memòria en format pdf de la pràctica amb:
    1. Captures de pantalla de urls del projecte i de l'aplicació, models i views i forms. També de l'script que crea el joc de proves.
    1. Captura de les pantalles del programa en funcionament.
2. Fes like si l'has entès i RT si l'has acabat.


---

#FpInfor #Daw #DawMp07 #DawMp07Uf02

---

###### Autor: daniel herrera 2014.01.24 16:25:43
###### Editat per: daniel herrera 2014.01.24 16:25:43
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
