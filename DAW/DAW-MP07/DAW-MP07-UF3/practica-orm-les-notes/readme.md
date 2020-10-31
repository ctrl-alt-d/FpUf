# Pràctica ORM: Les notes
## DAW-MP07-UF3 - Exercici de Tècniques d’accés a dades.
Observa aquest model entitat relació:

![Els estudiants i les notes](http://i.imgur.com/VKzAAhn.png)

* Entre Cicle i Assignatura hi ha una relació N:M
* Entre Estudiant i Assignatura hi ha una relació N:M amb atributs.
* Els noms dels estudiants no es poden repetir.
* La Nota pot ser null si l'estudiant no s'hi presenta.
* No es poden donar dues qualificacions per al mateix estudiant, assignatura i qualificació.

### Entregables:

Fitxer PDF amb:

* Codi documentat per crear les classes ORM d'aquest model entitat interrelació.

* Instruccions documentades per insertar les següents dades:
    * Estudiants **Guillermo** i **Gustavo** amb 20 i 22 anys respectivament.
    * Cicles **DAW**, **DAM** i **SMX**
    * Assignatura **Base de Dades** que es cursa a **DAW** i **SMX**
    * Assignatura **Xarxes** que es cursa a **SMX**
    * Gustavo ha tret un 9 a la primera convocatòria de Base de Dades i Guillermo no s'ha presentat.
    * Guillermo ha tret un 10 a la segona convocatòria de Base de Dades.
    
* Instruccions documentades per seleccionar les següents dades:
    * Estudiants que tenen més de 22 anys.
    * Totes les qualificacions de'n Guillermo:
        * A partir de la classe **Qualificacio**
        * A partir de l'objecte *Guillermo*
    * Les edats de tots els alumnes en una llista (flat)





---

#FpInfor #Daw #DawMp07 #DawMp07Uf03

---

###### Autor: daniel herrera 2015.11.18 08:09:30
###### Editat per: daniel herrera 2015.11.18 08:25:44
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
