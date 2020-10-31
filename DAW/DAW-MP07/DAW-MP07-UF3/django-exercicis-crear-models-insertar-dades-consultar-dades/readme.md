# ORM: exercicis crear models, insertar dades, consultar dades.
## DAW-MP07-UF3 - Exercici de Tècniques d’accés a dades.
Tant amb Entity Framework de Microsoft com amb django fes el següent:

**Prepara aquests models:**

* Crea els models `Gos` i `Raça` amb tipus de correspondència 1:N. 
* Podem trobar un `Gos` que no sigui de `Raça`, per tant, al cap foreign key hauràs de posar `null=True, blank=True`. Consulta: [ForeignKey.on_delete](https://docs.djangoproject.com/en/1.10/ref/models/fields/#django.db.models.ForeignKey.on_delete)
* `Gos` té per camp `número de xip` ( qué ha de ser `unique`) , data neixement i nom.
* `Raça` ha de tenir el camp `nom` i `preu`.

**Inserta les següents dades:**

* Pastor Alemany -> 100€
* Xiguagua -> 350€
* Baset -> 150€

**Inserta els següents gosos. Django: dos mètodes, a partir de la col·leció o com a nou objecte i save():**

* Boby, numero de xip 25, va nèixer el 1/4/2012, és un Pastor Alemany.
* BigBoy, numero de xip 26, va nèixer el 1/5/2012, és un Xiguagua.
* Xuxu, numero de xip 27, va nèixer el 1/8/2012 no te raça.
* Salxi, numero de xip 28, va nèixer el 1/7/2012, és un Baset.
* Pipon, numero de xip 29, va nèixer el 1/8/2012, és un Pastor Alemany.

**Consultes:**

* Tots els gossos nescuts més tard de l'1 de juny del 2012.
* Tots els Pastor Alemany buscant la raça i accedeix a gosos_set.
* Tots els Pastor Alemany buscant la raça i fent filter des de `Gos`.
* La mitjana de preu de totess les races.
* La suma del preu de tots els Pastors Alemanys.
* Els gossos que contenen la lletra o al seu nom, acompanyat del nom de la raça.
* Els gossos que no són de raça.
* Tots els gossos ordenats per nom.
* Tots els gossos ordenats per data de neixement.
* Cada raça amb el seu nom i el total de gossos d'aquella raça, dos mètodes: usant annotate i usant .count() a cada iteració.

**Vídeos amb la solució**

* **[Video solució amb django 2016](https://youtu.be/uCjr4aNxVNs)**
* **[Video solució amb dbcontext 2016](https://youtu.be/jUW23Hp-uT4)**
* **[Video solució amb dbcontext models 2017](https://youtu.be/YUnJVUag03w)**
* **[Video solució amb dbcontext insercions 2017](https://youtu.be/l0vsEDLAe-o)**
* **[Video solució amb dbcontext seleccions 2017](https://youtu.be/p2Iz7dohP5Y)**

**Codi solució amb dbcontext**:

```C#
using gossera.Models;
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace gossera
{
    class Program
    {
        static void Main(string[] args)
        {
            var ctx = new GosseraContext();

            /*
                    Pastor Alemany -> 100€
                    Xiguagua -> 350€
                    Baset -> 150€             
             */

            var pastor = new Rassa();
            pastor.nom = "Pastor Alemany";
            pastor.preu = 100;
            ctx.rassa_set.Add(pastor);

            var xiguagua = ctx.rassa_set.Create();
            xiguagua.nom = "xiguagua";
            xiguagua.preu = 350;
            ctx.rassa_set.Add(xiguagua);

            var baset = ctx.rassa_set.Create();
            baset.nom = "Baset";
            baset.preu = 350;
            ctx.rassa_set.Add(baset);

            ctx.SaveChanges();

            /*
                Boby, numero de xip 25, va nèixer el 1/4/2012, és un Pastor Alemany.
                BigBoy, numero de xip 26, va nèixer el 1/5/2012, és un Xiguagua.
                Xuxu, numero de xip 27, va nèixer el 1/8/2012 no te raça.
                Salxi, numero de xip 28, va nèixer el 1/7/2012, és un Baset.
                Pipon, numero de xip 29, va nèixer el 1/8/2012, és un Pastor Alemany.

             * */

            var pastor = ctx.rassa_set.Where(x => x.nom == "Pastor Alemany").First();

            var g1 = ctx.gos_set.Create();
            g1.nom = "Boby";
            g1.numero_de_xip = 25;
            g1.data_naixement = new DateTime(2012,4,1);
            g1.rassa = pastor;

            var g2 = ctx.gos_set.Create();
            g2.nom = "Xuxu";
            g2.numero_de_xip = 27;
            g2.data_naixement = new DateTime(2012, 8, 1);

            ctx.gos_set.Add(g1);
            ctx.gos_set.Add(g2);

            ctx.SaveChanges();
```

            //Tots els gossos nescuts abans del'1 de juny del 2012.
            var q1 = ctx
                    .gos_set
                    .Include( x => x.rassa )
                    .Where(gos => gos.data_naixement < new DateTime(2012, 6, 1))
                    ;

            foreach (var gos in q1)
            {
                Console.WriteLine(" * " + gos.nom + " - " + gos.rassa.nom );
            }

            //
            Console.WriteLine(" * Tots els Pastor Alemany buscant la raça i accedeix a gosos_set.");
            var pastor = ctx.rassa_set.Where(rassa => rassa.nom == "Pastor Alemany").First();
            var q2 = pastor.gos_set;
            ctx.Entry(pastor).Collection(x => x.gos_set).Load();
            foreach (var gos in q2)
            {
                Console.WriteLine(" * " + gos.nom + " - " + gos.rassa.nom);
            }

            // Totes les races, tots els gossos de cada raça
            var totes_les_races = ctx.rassa_set;
            foreach (var r in totes_les_races)
            {
                Console.WriteLine("Raça: " + r.nom);
                ctx.Entry(r).Collection(x => x.gos_set).Load();
                foreach (var g in r.gos_set)
                {
                    Console.WriteLine("Gos: " + g.nom);
                }
            }
    
            }
        }
    }


**Altres consultes**

```java
        Gossera ctx = new Gossera();
```

            //raça pastor alemay
            Raça pa = ctx
                        .Races
                        .Where(r => r.Nom == "Pastor Alemany ")
                        .First();


            //mitjana de preu de les races
            decimal mitjana = ctx.Races.Select(x => x.Preu).Average();

            //suma del preu dels gossos pastor alemany
            decimal suma = ctx
                            .Gossos
                            .Where(x => x.Raça.Nom == "Pastor Alemany")
                            .Select(r => r.Raça.Preu)
                            .Sum();

            //nom del gos i nom de la raça dels gossos que contenen una o al seu nom
            var gossos_amb_o = ctx
                              .Gossos
                              .Where(g => g.NomDelGos.Contains("o"))
                              .Select(x => new
                              {
                                  gos = x.NomDelGos,
                                  raça = x.Raça.Nom
                              });

            foreach (var g in gossos_amb_o)
            {
                Console.WriteLine(g.gos + " " + g.raça);
            }

            //Gossos sense raça
            var gosos_que_no_tenen_raça = ctx
                                          .Gossos
                                          .Where(x => x.Raça == null)
                                          .ToList();

            //Gossos ordenats per data naixement
            var gossos_per_nom = ctx
                                 .Gossos
                                 .OrderBy(x => x.diaNeixament)
                                 .ToList();

            //races amb número de gossos d'aquella raça
            var races = ctx
                        .Races
                        .Select(x => new
                                {
                                    nom = x.Nom,
                                    numero_gossos = x.Gossos.Count(),
                                })
                        .ToList();

            //gossos nascuts després de juny de 2012
            var tots_els_gossos_despres_juny_2012 = ctx
                .Gossos
                .Where(g => g.diaNeixament > new DateTime(2012, 6, 1));

---

#FpInfor #Daw #DawMp07 #DawMp07Uf03

---

###### Autor: daniel herrera 2016.11.15 15:36:42
###### Editat per: daniel herrera 2017.11.14 20:14:25
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
