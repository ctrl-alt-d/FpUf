# MVC Microsoft - El help desk ( Fluent Api i Validacions )
## DAW-MP07-UF2 - Exercici de Generació dinàmica de pagines web.
El help desk
=============

En aquesta pràctica treballarem:

* Declaració d'interrelacions mitjançant Fluent Api
* Validacions a diferents nivells.
* Adaptació de les vistes 'Create', 'Details' i 'Edit'.


Crea els models `Tècnic` i  `Incidència`:

* Tècnic:
    * ID
    * Nom
    * Actiu ( booleà )
    * *No oblidis les 2 propietats de navegació inversa cap a inicidències*
* Incidència
    * ID
    * Data alta incidència
    * Descripció curta
    * Tècnic que obra la incidència
    * Tècnic que tanca la incidència
    * *No oblidis crear tant les propietats de clau forana com les propietats de navegació*

Per tal de declarar les interrelacions et caldrà fer servir la fuent api.

* 0) Crea els models, tingues en compte els punts 1 i 2.
* 1) Fes obligatori el tècnic que Obra la incidència.
* 2) Fes opcional el tècnic que tanca la incidència.
* 3) Fés l'escaffolding dels controladors.
* 4) No permetis esborrar tècnics que tinguin incidències relacionades, en comptes d'esborrar el sistema el marcarà com a 'No actiu' ( Mira *Ajuda Esborrar Tècnic* ). Ho anomenarem 'soft-delete'.
* 5) Quan crees una incidència **no** has de preguntar pel tècnic que la tanca.
* 6) Quan modifiques una incidència **no** has de preguntar pel tècnic que la obra (mirar Ajuda dades imcompletes )
* 7) Tant quan obres com quan tanques incidències només has de presentar els tècnics actius.
* 8) Anota el model `Incidència` de manera que els atributs corresponents a les claus foranes a tècnics tinguin nom entenedor ( Mira ajuda canviar prompt de camps).
* 9) Al detall de cada tècnic ha d'apareixer una llista amb les darreres 10 incidències que ha obert i les darreres 10 incidències que ha gestionat (Mirar ajuda `@For Each` )
* 10) Validacions: Per motius de qualitat de servei no es permet obrir noves incidències a un tècnic que ja tingui 3 incidències sense tancar, és a dir, tres incidències on ell aparegui com a técnic que obra i que estigui obertes. O bé, que tingui una incidència sense tancar amb més d'una setmana d'antiguitat. (Quin tipus de validació es tracta? Implementa-la )

###Ajuda

**Videos**

* [Creació de models. Exercicis: 0,1,2](https://youtu.be/5P5wDzanNEQ). YT 39'
* [Scaffolding i soft delete. Exercicis: 3, 4](https://youtu.be/flafgcs3E8s). YT 27'
* [Modificar controladors. Exercicis 5, 6](https://youtu.be/YCpgP-us99Y). YT 19'
* [Modificar controladors. Exercici 7](https://youtu.be/1HinIHgEbfk). YT 19'
* [Modificar controladors. Exercici 8](https://youtu.be/iy_p4_fG0nY). YT 19'
* [Modificar vista, afegir dades de la propietat de navegació inversa. Exercici 9](https://youtu.be/GeFQimehpjA)
* [Modificar dbcontext, afegir validació. Exercici 10](https://youtu.be/CXxHZqVEffg)


Com que les relacions no les podem definir seguint les convencions per nom cal usar attributs o millor encara la Fluent API:

    modelBuilder.Entity<Incidencia>() 
        .HasRequired(t => t.TecnicObra) 
        .WithMany(t => t.IncidenciesQueObra) 
        .HasForeignKey(d => d.TecnicObraID) 
        .WillCascadeOnDelete(false);
    //Recorda que aquesta entitat té dues interrelacions i que
    //cal declarar-les totes dues.

*Ajuda Esborrar Tècnic*

Has de fer un `if` per comprovar si té o no incidències relacionades. Això ho has de fer al mètode on ja ha quedat confirmat l'esborrat:

    if ( tecnic.incidenciesObertes.any() ... ) {
        //Té incidències relacionades
        tecnic.esActiu = false;
        db.saveChanges();
        return //redirigir cap a una vista nova que informi del que hem fet
    } else {
        //el codi que crea l'scaffolding

*Ajuda `@For Each`:* (En notació razor per VBNET, la notació C# és una mica diferent)

    <dt>
        @Html.DisplayNameFor(Function(model) model.Incidencies_obrir)
    </dt>
    <dd>
        @For Each item As Incidencia In Model.Incidencies_obrir.Take(10)  <- cal ordenar-les                  
               @item.descripcio_curta 
               @<br>                    
        Next               
    </dd>

*Ajuda dades incompletes* ( Quan actualitzem incidència no ens arriba la dada 'Tècnic que la Obra' i l'hem de prendre de la base de dades) 

Si des del formulari no t'arriben totes les dades del model, pots anar a buscar les dades que et faltin a la base de dades:

                //busco a la bdd els valors que em falten
                var valors_de_la_bd = db.Incidencies
                                        .Where(x => x.ID == incidencia.ID)
                                        .Select(x => new { x.ObreIncidenciaID } )
                                        .FirstOrDefault();

                //omplo la entitat amb els valors que falten
                incidencia.ObreIncidenciaID = valors_de_la_bd.ObreIncidenciaID;

                //li dic al context que em manegui la entitat
                db.Entry(incidencia).State = EntityState.Modified;

                //deso els canvis
                db.SaveChanges();

                //si tot va bé, redirigeixo cap a Index
                return RedirectToAction("Index");



*Ajuda canviar 'prompt' dels camps*

Al model anotem la Incidencia:

```c++
[Display(Name = "Tènic que tenca")]
public int? Cas_TencatID { set; get; }
```

Modifiquem les vistes:

A la vista **index.cshtml**: 
    `@Html.DisplayNameFor(model => model.Cas_Tencat.nom)` 
cal canviar la propietat `Cas_Tencat.nom` per `Cas_TencatID`.

A la vista **Edit.cshtml**:

        <div class="form-group">
            @Html.LabelFor(model => model.Cas_ObertID,  new { @class = "control-label col-md-2" })
            <div class="col-md-10">
                @Html.DropDownList("Cas_ObertID", String.Empty)
                @Html.ValidationMessageFor(model => model.Cas_ObertID)
            </div>
        </div>

Aqui hem d'eliminar el String que esta a continuació de model.Cas_Obert i cambiar la propietat de `Cas_Obert` per `Cas_ObertID`.

A la vista **Details.cshtml** hem de cambiar la variable `Cas_Obert.nom` per `Cas_ObertID`.

---

#FpInfor #Daw #DawMp07 #DawMp07Uf02

---

###### Autor: daniel herrera 2015.01.12 16:28:08
###### Editat per: daniel herrera 2017.11.29 07:41:41
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
