# Herència amb Oracle Objects. L'Orquestra.
## DAW-MP02-UF4 - Exercici de Bases de dades objectes-relacionals
1) Crea usuari i connexio a base de dades, otorga els permisos mínims ( connect i resource ). Connectat amb l'usuari que has creat.

2) (1 punt ) Crea el tipus `instrument` amb els següents camps: nom (cadena de caràcters), tessitura (cadena de caràcters), sound (cadena de caràcters ). I el mètode play que retorna sound.

3) (1 punt ) Crea els subtipus:

3.1) `corda`: número de cordes ( numèric )

3.2) `vent`: és conic ( booleà ó numeric si booleà no és suportat per la base de dades )

3.3) `percusió`: és de membrana ( booleà ó numeric si booleà no és suportat per la base de dades )

4) (2 punt ) Crea una taula d'objectes i inserta els següents intruments que són de corda, vent i percusió respectivament:

4.1) violi, Sol3-Do7, 'tiruriruriru', 4

4.2) clarinet, Re3-Do6, 'buuup', no és cònic

4.3) marimba, Do2-Do6, 'bum bim', no és de membrana

5) (1 punt ) Crea la taula `Orquestra` amb els camps: DNI ( clau primària ), Nom (cadena de caracters) , Instrument ( de tipus instrument ).

6) (1 punt ) Posa el violi, clarinet i marimba en variables i inserta a la taula Orquestra un músic per a cada instrument.

---

#FpInfor #Daw #DawMp02 #DawMp02Uf04

---

###### Autor: daniel herrera 2017.04.04 14:20:18
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
