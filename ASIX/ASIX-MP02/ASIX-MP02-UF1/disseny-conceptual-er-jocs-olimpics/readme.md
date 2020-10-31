# Disseny conceptual E/R - JOCS OLÍMPICS
## ASIX-MP02-UF1 - Exercici de Introducció a les bases de dades
**Els Jocs Olímpics són una competició esportiva a nivell mundial per uns certs esports considerats olímpics.** 

* D’aquests esports en volem guardar el nom i el logotip que representa l’esport dins els Jocs, com per exemple els següents: Equitació, Tenis.

* Els esportistes no realitzen proves d’un esport sinó de les seves disciplines. Cada esport pot tenir una sèrie de disciplines. Per exemple l’esport d’atletisme té: 100m, 200 m, 4x400 m, 20km marxa, Salt d’alçada, Salt amb perxa, etc... Aquests noms identifiquen de manera única les diferents disciplines.

* De les disciplines se’n deriven les proves que realitzaran els esportistes. Aquestes proves poden ser només de dos tipus (ELIMINATÒRIA i FINAL) i també tenen un sexe associat (MASCULÍ, FEMENÍ, MIXT). Per exemple, en una disciplina hi hauran moltes eliminatòries abans d’arribar a la prova final a on es decidirà qui obté medalla. Totes les proves reben un número seqüencial dins de la seva disciplina per identificar-les entre les altres de la mateixa disciplina.

* Els participants de les proves poden ser esportistes de forma individual, com per exemple 100m llisos, esgrima, les anelles,.. o bé per equips: futbol, bàsquet,...

* Els esportistes i els equips poden participar en més d’una prova.

* Una informació rellevant per la nostra BD és saber de quins esportistes estan formats els diferents equips dels diferents països.

* Tots els esportistes i equips pertanyen a un país que és qui els representa en els Jocs. De cada país en volem saber el seu nom i el logotip de la bandera per mostrar-la als vídeomarcadors dels diferents estadis o emplaçaments a on es realitzen les proves. El nom del país l’identifica envers els altres.

* Per tal d’identificar un esportista en tot el recinte dels jocs se’ls hi entrega una acreditació a on conté el nom i cognoms de l’esportista, el sexe i el país que el representa. També s’hi afegeix un codi de barres per tal d’identificar l’esportista envers els altres i que servirà per accedir en els diferents recintes dels Jocs.

* A la BD no volem guardar països que no participin en els Jocs i  no tots els països tenen representants per totes les proves de les diferents disciplines.

* Durant el transcurs dels Jocs els esportistes viuen a la Vila Olímpica, aquesta  està formada per edificis. Els edificis s’identifiquen per un codi i ens interessa saber-ne l’adreça dins la ciutat. Els edificis estan dividits en blocs i aquests se’ls hi assigna una lletra per cada edifici per identifcar-los. Per exemple tenim el bloc 001A corresponent al bloc A de l’edifici 001 i tenim el bloc 002A corresponent al bloc A de l’edifici 002.
Dels blocs hem de saber-ne el nº d’habitacions per tal d’assignar-hi els esportistes a mesura que arriben a la Vila.

* Un país estarà assignat a un sol edifici, però els esportistes poden estar assignats en diferents blocs.

* No tots els edificis disposen de menjador a on els esportistes hi podran realitzar els àpats. Per tant, hem de saber quins d’ells en disposen per tal d’informar-ho en els esportistes a mesura que arribin a la Vila.

* De cada esportista o equip ens hem de guardar la posició que han quedat en cadascuna de les proves per llavors realitzar l’assignació de les medalles. 1r=Or, 2n=Plata,3r=Bronze.

* Cal portar un control del medaller de tots els països. Volem saber de cada país el número de cada tipus de medalla (or, plata, bronze).

* Les proves es disputen en un dia i hora concrets en un emplaçament dins d’una ciutat. Per diferenciar els diferents emplaçaments se’ls hi assignarà un nom i a més a més en volem saber la l’adreça i l’aforament limitat que tenen.

* Degut a que totes les proves no es poden realitzar al mateix lloc els emplaçaments poden estar en diferents ciutats del país a on es celebren els Jocs. 

**El nostre sistema cal que permeti. Entre altres coses, fer consultes del tipus:**

* Quantes proves s’han realitzat en una data concreta.
* Quantes proves eliminatòries hi ha de tipus mixt.
* Llistat de noms de ciutats a on s’hi disputen proves de les diferents disciplines.
* De cada edifici en volem saber el número de blocs que el componen i el número total d’habitacions que té.

---

#FpInfor #Daw #Asix #Dam #AsixMp02 #DawMp02 #DamMp02 #AsixMp02Uf01 #DawMp02Uf01 #DamMp02Uf01

---

###### Autor: Robert Ventura 2018.10.06 14:19:15
###### Editat per: Robert Ventura 2018.10.06 14:19:15
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
