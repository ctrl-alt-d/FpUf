# Els GAMERS vanidosos
## DAW-MP07-UF2 - Exercici de Generació dinàmica de pagines web.
Un famòs youtuber vol crear un portal on els gamers comparteixin captures de pantalla de les seves partides. I tu encarrega a tu.

Un cop fet l'anàlisi detectes que et calen els següents models:

**Estructura de dades:**

* Joc:
    * Nom del joc
    * Icona ( camp opcional )
* Logro:
    * Títol
    * Captura
    * Descripció
    * Joc
    * Data
    * Gamer ( Usuari )
* Comentari:
    * Logro ( sobre quin logro és el comentari )
    * Gamer ( Usuari que penja el comentari )
    * Text
    * Data
* Like:
    * Logro ( sobre quin logro és el like )
    * Gamer
    * *Restricció unique Logro-Gamer*
    * Data

**Estructura de la web:**

* Pàgina principal llista de tots els logros ordre data invers.
* Punxant en un `logro` es pot veure la captura de pantalla, la descripció i, a sota, tots els comentaris en ordre data descendent.
* Afegir/editar logro.  `/logro/editar/25`
* Afegir/editar/esborrar comentari sobre logro. `/logro/25/editarcomentari/120`

**Restriccions:**

* Els usuaris només poden modificar les dades que ells publiquen o totes si ets super usuari.

**Millores:**

* Manteniment de Jocs ( CRUD )
* La pàgina principal es pot ordenar per data ( llistat per defecte, el més nou a dalt ) o bé per likes. `/?ordenacio=likes`
* La pàgina principal permet filtrar per Joc. Ex: `/?filtre=agar` mostraria només captures d'[agar](http://agar.io/)
* "Pag**í**na" la pàgina principal.
* "Pag**í**na" els comentaris.

**Tecnologia:**

* Pots desenvolupar el sistema amb django.
* Utilitza l'autenticació que et proporciona el framework.
* Utilitza crispy-forms per a integració amb bootstrap.
* Utilitza sistema de missatgeria amb usuari del framework per notificar sobre les seves accions ( ex: *dada desada correctament* )
* Utilitza al patró Post-Redirect-Get amb els formularis.
* Utilitza **Post** per esborrar dades, pots fer servir formulari del framework per a crear el formulari d'esborrat ( o senzillament formulari manual al template )
* Utilitza el sistema de formularis del framework per al formulari d'autenticació.

**Entregables:**

* Documenta la teva solució en un únic pdf amb el codi més rellevant així com captures de pantalla del sistema en funcionament.



 

---

#FpInfor #Daw #DawMp07 #DawMp07Uf02

---

###### Autor: daniel herrera 2016.02.03 15:33:59
###### Editat per: daniel herrera 2016.02.03 17:28:33
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
