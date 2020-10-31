# Introducció a la normalització
## DAW-MP02-UF1 - Exercici de Introducció a les bases de dades
**Definició**

La normalització és el procés per organitzar els atributs i relacions d'una base de dades relacionals per tal de reduir la **redundància** de les dades i incrementar la **integritat**.

**Explicació**

Amb els exercicis del tema 1, 2 i 3 hem aprés a crear les estructures que ens serviran de base per emmagatzemar la informació. Si ho hem fet correctament, cada dada apareix només una sola vegada a la seva corresponent relació ( a banda de les claus foranes, naturalment, però en aquest cas la integritat referencial ja s'encarrega de que no hi hagi incoherències ). 

Existeix una altre metodologia més formal i menys intuitiva que aplicant-la a tot el conjunt d'atributs del nostre univers de discurs ens portaria a la mateixa organització en relacions que estem obtenint mitjançant el MCD i el seu pas al MER. Aquesta metodologia s'anomena normalització.

Degut a que el procés de normalització és molt llarg, cal fer-lo pas a pas, ningú fa servir la normalització directament per a disenyar les estructures de dades. No per això hem de deixar d'estudiar-la perquè, al basar-se en definicions molt formals, si que ens serveix per argumentar quan una relació està mal construida. És molt difícil explicar a algú des del MCD perquè ha construit malament una relació, però és totalment definitiu poder dir: "aquesta relació està malament perquè no compleix amb la 2a forma normal". És per aquest motiu que tot informàtic ha de conèixer, al menys, les tres primeres formes normals.

Quan una base de dades està en 3a forma normal, habitualment, està lliure d'anomalies en insersió, actualització i esborrat.

**Exercici**

1) Respon la pregunta: "Per què un informàtic ha de conèixer, al menys, les 3 primeres formes normals?"

2) Un professor emmagatzema informació dels seus alumnes en una taula excel de la següent manera:

```bash
Alumne  Població  Avaluació  Nota 
  Pere     Roses          1     8  
  Pere     Roses          2     7  
  Pere     Roses          1     5  
 Marta  Figueres          1     8
```

Reflexiona sobre el següent:

* Com sap el professor la població dels alumnes fins que els posa la nota?
* Pot contenir aquesta taula incoherències?
* Si un alumne canvia de població, quants canvis hem de fer a la taula? et sembla coherent?
* Se solucionen aquestes incoherències si en comptes de tenir una sola taula 'alumnes'  tenim dues taules: 'alumnes' i 'Notes'? Quins camps tindrien cada taula?

3) Observa la pregunta d'stackoverflow [Normalization in MYSQL](http://stackoverflow.com/questions/1258743/normalization-in-mysql) i contesta a les següents preguntes.

http://stackoverflow.com/questions/1258743/normalization-in-mysql

* Amplia el teu vocabolari anglès, busca quin és el significat de 'layman terms'
* És la normalització un procés específic de cada SGBD comercial?
* Com fa per a normalitzar la taula 'Empleats' l'usuari *Extrakun* ?




>
>######Aquest exercici està extret del llibre [d'exercicis Introducció a les Bases de Dades. UF1 MP2 DAM DAW ASIX](https://www.amazon.es/Introducci%C3%B3-Bases-Dades-asix-MP02-UF1/dp/153735096X) amb permís del seu autor. 
>


---

#FpInfor #Daw #Dam #Asix #AsixMp02 #DawMp02 #DamMp02 #DawMp02Uf01 #AsixMp02Uf01 #DamMp02Uf01

---

###### Autor: daniel herrera 2016.08.27 15:38:36
###### Editat per: daniel herrera 2016.08.30 16:57:55
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
