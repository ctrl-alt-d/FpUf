# Tas-Tas-Tus - Procediments emmagatzemants
## DAW-MP02-UF3 - Exercici de Llenguatges SQL: DCL i extensió procedimental
Es tracta d'un joc de supervivència. Disposem d'una taula amb les dades que poden veure tots els participants:

* `participants` ( id (pk), nom, escuts_consecutius, número_bales_disponibles, estic_viu )

On:

* `id`: número.
* `nom`: nom del participant
* `escuts_consecutius`: quantes vegades a tret escut de manera consecutiva.
* `número_bales_disponibles`: quantes vales pot disparar.
* `estic_viu`: ens diu si està viu o mort.

A cada ronda es preguntarà a cada participant que vol fer. Això es farà invocant la funció que haurà escrit cada jugador: `resposta_pepito( @n as int )` on @n és el teu número de jugador. 

La resposta sermpre serà un `string` que pot contenir una lletra o un número:

* Si és una lletra: 
    * 'E': **Escut** si em disparen no em maten.
    * 'C': **Carregar** aconsegueixo una bala.
* Si és un string amb un número:
    * **Disparar** perdo una bala. És número és a qui estic disparant.

**Regles**

* Si a un participant el disparen mentre està disparant o carregant, aquell participant es mor.
* Cada 13 rondes matem als que portin més escuts consecutius.
 
**Exercici 1**

* Fes la funció `resposta_pepito( @n as int )` amb la teva pròpia estratègia guanyadora.

**Exercici 2**

* Crea el procediment i les estructures de dades que fa competir els participants entre ells.

---

#FpInfor #Daw #Dam #Asix #AsixMp02 #DawMp02 #DamMp02 #DamMp02Uf03 #DawMp02Uf03 #AsixMp02Uf03

---

###### Autor: daniel herrera 2018.05.11 13:33:42
###### Editat per: daniel herrera 2018.05.11 13:33:42
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
