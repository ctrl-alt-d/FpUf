# Consulta de dues taules: Comprensió Lectora  ( Enunciat xungu )
## DAW-MP02-UF2 - Exercici de Llenguatges SQL: DML i DDL
Cada centre educatiu emmagatzema la informació dels seus alumnes en una base de dades relacional accessible només pel personal de secretaria. El personal de secretaria disposa d’una aplicació que permet enviar consultes directes a la base de dades i recollir el resultat. Aquesta base de dades està protegida amb contransenya i el servidor amb un tallafocs per evitar accessos no desitjats.

La base de dades té informació sobre multitud de coses, per exemple, l’assistència a classe dels alumnes, les incidències, les expulsions, les activitats i sortides etc.

La taula d’alumnes és diu ‘Alumnes’ i és referenciada per moltes taules, per exemple, es referenciada des de la taula d’incidències, de manera que una incidència és d’un alumne i un alumne pot acumular moltes incidències. Una de les taules que referencia alumnes és Notes. La taula d’alumnes també està en relació N:M a altres taules, per exemple amb la taula d’activiats o sortides, de manera que a una sortida s’apunten molts alumnes i un alumne s’apunta a moltes sortides. La taula alumnes conté el nom i cognoms de l’alumne, també al grup que està matriculat i la seva data de naixement.

Dins la taula sortides, a més del preu de la sortida hi ha altra informació com ara el dia, el títol, etc. Dins la taula incidència, hi ha la data i hora de la incidència i una explicació del que ha passat, també dues claus forànes, una a professor que posa la incidència i una altra a alumne que rep la incidència. Dins la taula de Notes, a més de la clau forana a alumne, també trobaràs altres dades, com ara, el trimestre al qual correspon aquella nota, l’assignatura i la pròpia nota. Quan es desconeix la nota, per exemple perquè l’alumne no s’ha presentat a l’examen, llavors s’utilitza el valor null.

El departament d’ensenyament està molt preocupat per la comprenesió lectora dels alumnes. S’ha detectat que quan l’enunciat dels exercicis és llarg això incidèix negativament a la nota. També s’ha observat que, si l’alumne ha de ser capaç de diferenciar la part rellevant per resoldre l’exercici de la part supèrflua la nota també es resenteix.

Per aquests motius exposats, el departament d’ensenyament demana a cada centre educatiu que prepari una relació de tots els alumnes que han suspés algun trimestre d’alguna de les assignatures relacionades amb la comprensió lectora, en concret ‘castellà’ i ‘català’.

L’inspector revisarà aquestes llistes per comprovar que tot està bé i que no hi hagi noms repetits. S’ha comprovat que hi a centres que no saben transformar el llenguatge natural en llenguatge SQL, de vegades al llenguatge natural apareix una conjunció coordinada copulativa (i) quan al llenguatge SQL en realitat busquen una conjunció coordinada disjuntiva (o). Per sort, el nostre centre disposa d’informàtics com tu.

Escriu la sentència SQL que ha d’escriure secretaria per poder obtenir les dades que el departament demana.


Enunciat relacioinat: [Consulta de dues taules: Comprensió Lectora  ( Enunciat clar )](/DAW/DAW-MP02/DAW-MP02-UF2/consulta-de-dues-taules-comprensio-lectora-enunciat-clar/readme.md)

---

#FpInfor #Daw #Dam #Asix #AsixMp02 #DawMp02 #DamMp02 #DawMp02Uf02 #AsixMp02Uf02 #DamMp02Uf02

---

###### Autor: daniel herrera 2018.01.18 18:22:03
###### Editat per: daniel herrera 2018.01.18 18:22:03
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
