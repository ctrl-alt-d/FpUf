# La Jota de Oro. Treballant amb Models, Vistes, Templates i Formularis.
## DAW-MP07-UF2 - Exercici de Generació dinàmica de pagines web.
L'associació que aglutina els esbarts dansaires de Jotas ha organitzat el concurs internacional 'La Jota de Oro'. Es vol premiar el millor ballador de Jotas.

Dels `esbarts` ens interessa en quina `província` estan, el *telèfon de contacte*, el *nom* que ha de ser únic dins la *província* i els `balladors` d'aquell esbart. Dels `balladors` ens interessa el seu *nom i cognoms*, la seva *adreça de correu* i la *categoria* a que pertanyen ( "Alevin", "Juvenil" o "Senior" ). També tenim el model `Vot` dins l'aplicació "votacions". Del vot ens interesssa el ballador i a quina hora s'ha votat.


###Primera part

Crea les següents vistes amb els respectius templates:

* Tots els esbarts: Listat amb tots els esbarts, per província. Ordre alfabètic.
* Detall d'esbart: Dades de l'esbart amb el detall dels seus membres. Amb botó per votar. Només es pot votar pels "Seniors".
* Scoreboard: Llistat ordenat de tots els seniors amb el nom, esbart ( amb enllaç ) i la seva puntuació.

**Notes**

* Seria més interessant que calgués estat registrat per poder votar, però per ara no ho sabem fer.

**Restriccions**

* Només es pot votar els seniors.


**Solució de l'exercici al Youtube**

>Aquests videos **no** són un manual. És la gravació en directe de la resolució dels exercicis a classe amb els alumnes. Els videos són 'raw', sense editar, hi ha estones mortes i preguntes i comentaris dels alumnes.

1. [Creació dels models i inserció de dades. 30'](https://youtu.be/wDdlAdajpkc)
2. [Primera vista "Tots els esbarts". 15'](https://youtu.be/h7WoNfm1TrQ)
3. [Posant un valor per defecte al template. 13'](https://youtu.be/6UUINUjq-FM)
4. [Detall d'un esbart. 17'](https://youtu.be/Hk5jFoDW8UU)
5. [Votar. 22'](https://youtu.be/laldW5YM4Fo)
6. [Scoreboard. 14'](https://youtu.be/7KNHoEMAryA)
7. [Afegint template base. 12'](https://youtu.be/cyi_MRrZMH0)


###Segona Part

* Crea una vista amb la llista de províncies. Posa-hi un enllaça a `crear nova província`. 
* Crea un formulari per a crear una nova província. Un cop creada redirigeix l'usuari a la vista anterior.

**Solució de l'exercici al Youtube**

>Aquests videos **no** són un manual. És la gravació en directe de la resolució dels exercicis a classe amb els alumnes. Els videos són 'raw', sense editar, hi ha estones mortes i preguntes i comentaris dels alumnes.

1. [Creant formulari alta de provincies. 22'](https://youtu.be/--G5kSedljM)
2. [Modificant la vista per tal de poder fer altes però també edicions 18'](https://youtu.be/BHbqOfj1UUU)

---

#FpInfor #Daw #DawMp07 #DawMp07Uf02

---

###### Autor: daniel herrera 2016.12.05 14:20:24
###### Editat per: daniel herrera 2016.12.19 16:34:21
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
