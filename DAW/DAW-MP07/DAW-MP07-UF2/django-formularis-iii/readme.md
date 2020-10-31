# django - Formularis III
## DAW-MP07-UF2 - Exercici de Generació dinàmica de pagines web.
El taller de cotxes
====

Un taller de cotxes vol tenir registre dels cotxes que repara.

Per això crea aquests models:

* Tècnic ( número de la seguretat social, nom, és baixa )

* Cotxe ( matrícula, nom propietari, nom marca, non model, color , data de matriculació, es importat )

* Reparació ( cotxe, dia entrada al taller, kilòmetres, descripció avaria, tècnic repara, dia sortida del taller )

*Nota: els colors dels cotxes només poden ser: blanc, groc, negre i vermell.*

**Es demana**

1. Script python per a crear 4 tècnics i 6 cotxes per al joc de dades.
1. Home page amb la llista de tots els cotxes que hi ha al taller  `Cotxe.objects.filter( reparacio__dia_sortida_del_taller__isnull = True )` 
2. Vista amb modelForm per editar ó crear reparacions segons parametre opcional 'id_reparacio' 

**Requerimets**

1. El projecte es dirà 'taller' seguit de les teves inicials. Si et dius 'Jaume Garcia' serà 'tallerjg'.
1. El projecte tindrà dues aplicacions: 'personal' i 'cotxes'
1. L'aplicació `personal` tindrà els tècnics, els altres models seran a `cotxes`.
1. Les urls de l'aplicació `cotxes` tindran el seu propi namespace.
1. Per crear noves entrades de reparacions usarem al template: `{% url 'cotxesns:nova_reparacio' %}
1. Per editar entrades de reparacions usuarem al template: `{% url 'cotxesns:edita_reparacio' r.id %}
1. Un cop donada d'alta la reparació anirem a l'arrel, opcional fer-ho amb `reverse` o hardcoded.
1. La vista que crea / edita reparacions es dirà `vw_reparacio`



**Ajuda**

Recorda que el patró per a una pantalla de creació / edició és el següent:

vista vw_reparacio( request, id_reparacio = None ):
    si ens informen id_reparacio llavors
        reparacio = buscar_reparacio_per_id ( id_reparacio )
    en cas contrari
        reparacio = nova_reparacio()

    si rebo dades via post
        form = el_model_form( dades_rebudes, instancia = reparacio )
        si form.is_valid() llavors
            //cas 1
            form.save()
            afegir a missatgeria que tot ha anat bé
            redirecció a alguna banda
        en cas contrari
            //cas 2
            afegir a missatgeria que tot ha fallat
    en cas contrari
        //cas 3
        form = el_model_form( instancia = reparacio)

    retornar el form renderitzat

**Ampliació**

1. Crea el model `Peça` dins l'aplicació `cotxes` ( sense la 'ç', ex: Pessa )
2. Pessa tindrà: nom peça i preu.
3. Modifica el joc de proves per a que es crein 4 peces.
3. Defineix la relació n:m entre `Reparacio` i  `Pessa`.

**Cal entregar**

1. Document memòria de la pràctica amb:
1. Captures de pantalla de urls del projecte i de l'aplicació, models i views i forms. També de l'script que crea el joc de proves.
1. Captura de les pantalles del programa en funcionament.


---

#FpInfor #Daw #DawMp07 #DawMp07Uf02

---

###### Autor: daniel herrera 2014.01.22 17:10:00
###### Editat per: daniel herrera 2014.01.24 16:22:52
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
