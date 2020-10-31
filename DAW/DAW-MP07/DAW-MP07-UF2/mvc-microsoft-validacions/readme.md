# MVC Microsoft - La Casa Rural ( Validacions amb anotacions, iValidatableObject i ValidateEntity )
## DAW-MP07-UF2 - Exercici de Generació dinàmica de pagines web.
La Casa Rural
===============

Una casa rural està posant una web per poder fer les reserves de tota la casa.

L'entitat `Reserva` tindrà els següents camps:

* Data Entrada: dia en que la família entra a la casa ( entren méś tard de les 17:00h )
* Data de Sortida: dia en que la família deixa la casa ( han de sortir abans de les 10:00h )
* Dades del llogater (què és un altre model)

L'entitat `Llogater` tindrà els següents camps:

* Telèfon
* Nom i cognoms
* Codi postal
* NIF

**Validacions:**

1. Cal que la data d'entrada sigui anterior a la data de sortida.
1. Cal que la data d'entrada sigui del futur ( al menys 1 dia més endavant )
1. Telèfon, codi postal i nif es validaran amb expressió regular.
1. Nom i cognoms ha de tenir entre 20 i 200 caracters.
1. Cal que les dates de les diferents reserves no se solapin entre si.

**Ajuda per a la pràcita:**

Per a fer la pràctica llegeix-te l'article [Entity Framework Validation](http://msdn.microsoft.com/en-us/data/gg193959.aspx) D'aquest artícle farem servir les validacions *amb anotacions*, les validacions *IValidatableObject* i les validacions *DbContext.ValidateEntity*.

**Entregables**

1. Per a cada validació demanada a l'exercici argumenta quin tipus de validació faràs servir i perquè ( sempre has de fer servir el sistema més sencill possible )
2. Programa el model i el controlador, afegeix les validacions per *anotacions* comprova que tot funciona tot introduint al menys 5 reseves a la base de dades ( que no se solapin entre elles i que cumpleixin amb les normes que no estàs controlant ) Documenta com respon el teu programa quan intentes entrar dades que no cumpleixen amb les validacions per anotació. Documenta tant el codi i fes captures de pantalla de l'aplicació en execució.
3. Crea les regles de les validacions per *IValidatableObject*, documenta com respon el teu programa quan intentes entrar dades que no cumpleixen amb aquestes validacions. Documenta tant el codi i fes captures de pantalla de l'aplicació en execució.
4. Per últim fes les validacions per *DbContext.ValidateEntity*, documenta com respon el teu programa quan intentes entrar dades que no cumpleixen amb aquestes validacions. Documenta tant el codi i fes captures de pantalla de l'aplicació en execució.

*Nota* quan comprovis solapament recorda excloure de la consulta de models que solapen el propi model que estàs validant. Ho pots per per clau primària. 

**Altres**

Comprova el codi font de la pàginca canviant aquest setting:


```xml
<appSettings> 
    <add key="ClientValidationEnabled"value="false"/> 
    ... 
</appSettings>
```

**Ajuda**

Per poder fer el punt 5 hauràs de sobreescriure el mètode *ValidateEntity* de la teva classe de context:

```java
using System;
using System.Collections.Generic;
using System.Linq;
using System.Web;
using System.Data.Entity;
using System.Data.Entity.Validation;
using System.Data.Entity.Infrastructure;

namespace el_teu_namespace.Models
{
    public class ReservaDBContext : DbContext
    {
        public DbSet<Reserva> Reserves { get; set; }

        protected override DbEntityValidationResult ValidateEntity(DbEntityEntry entityEntry, 
                                                                  IDictionary<object, object> items)
        {
            //preparem una llista buida d'errors de validació
            var result = new DbEntityValidationResult(entityEntry, new List<DbValidationError>());
            
            //si estem validant una reserva
            if (entityEntry.Entity is Reserva && ( entityEntry.State == EntityState.Added || 
                                                   entityEntry.State == EntityState.Modified )) {
                
                Reserva reserva = entityEntry.Entity as Reserva;

                //hi ha solapaments?
                // R = la reserva que estic modificant.  r = reserva de la bdd.
                //--[-r-]-----[---R----]----------- No solapa
                //------------[---R----]---[-r-]--- No solapa
                var q_solapaments = Reserves.Where(r => !(r.Sortida < reserva.Entrada || 
                                                          r.Entrada > reserva.Sortida));
                q_solapaments = q_solapaments.Where(r => r.ID != reserva.ID);
                if (q_solapaments.Any()) {
                    result.ValidationErrors.Add(new DbValidationError("Sortida", 
                                                                      "Ocupada en aquestes dates")); 
                }               

                //altres validacions sobre la reserva 
                //...

            }
            
            if (result.ValidationErrors.Any()){
                //hem afegit errors a la llista d'errors de validació, retornem la llista d'errors
                return result;
            }else {
                //no hi ha hagut errors de validació, fem les validacions automàtiques de la classe base
                return base.ValidateEntity(entityEntry, items);            
            }
        }
    }
}
```

Aquest tipus d'errors no els manega el MVC, llavors, al *saveChanges* hauries de passar els errors des de l'exepció vins als errors del model:

```java
using System.Collections.Generic;
using System.Data;
using System.Data.Entity;
using System.Linq;
using System.Net;
using System.Web;
using System.Web.Mvc;
using _la_teva_aplicacio.Models;
using System.Data.Entity.Validation;
```

    [HttpPost]
    [ValidateAntiForgeryToken]
    public ActionResult Create([Bind(Include = "ID,Entrada,Sortida,telefon,Nom,Cognom,CoditPostal,Nif")] Reserva reserva)
        {
            //si el model passa les validacions d'anotació i de IValidatableObject
            if (ModelState.IsValid)
            {
                db.Reserves.Add(reserva);
                try
                {
                    db.SaveChanges();
                    //tot ha anat bé: redirecció a Index
                    return RedirectToAction("Index");
                }
                catch (DbEntityValidationException ex)
                {
                    //si si ha errors de validació a ValidateEntity els passem al model:
                    foreach( var error in ex.EntityValidationErrors.First().ValidationErrors ) {
                        this.ModelState.AddModelError(error.PropertyName, error.ErrorMessage);
                    }                    
                }
            }
            //hi ha errors de validació, ens quedem a la vista
            return View(reserva);
        }

Pots veure més informació a [Validation failed for one or more entities while saving changes to SQL Server Database](http://stackoverflow.com/a/6258174/842935)

---

#FpInfor #Daw #DawMp07 #DawMp07Uf02

---

###### Autor: daniel herrera 2014.12.19 14:10:01
###### Editat per: daniel herrera 2017.11.28 15:59:12
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
