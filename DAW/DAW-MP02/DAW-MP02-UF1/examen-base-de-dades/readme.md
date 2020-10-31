# Examen Base de Dades UF1 2017
## DAW-MP02-UF1 - Exercici de Introducció a les bases de dades
**Llegeix atentament aquest Univers de Discurs i fes el seu Model Conceptual
de Dades en format Model Entitat-InterRelació CrowFoot. **

Un ajuntament està molt preocupat perquè darrerament apareixen moltes pintades a les façanes
de les cases. L’ajuntament és qui es fa càrrec de la neteja d’aquestes pintades i vol fer un estudi
de l’impacte que representen. De les pintades ens interessa conèixer la seva posició exacta ( la
longitud i la latitud ), també el moment que es descobreixen (dia, hora, minuts, ...) i els minuts
totals que ha calgut per netejar-les.
És important saber tant qui ha trobat la pintada com qui l’ha netejat. Les pintades les poden trobar
o bé un guàrdia urbà o bé un operari de neteja i són sempre netejades per un operari de neteja.
Dels guàrdies urbans s’emmagatzema a la base de dades el seu rang (Agent, Caporal,
Inspector/a, ... ). Dels operaris de neteja ens interessa saber el tipus de contracte ( 4h, 8h, caps de
setmana, ... ). Tant els operaris de neteja com els guàrdies urbans els podem considerar personal
de l’ajuntament, s’identifiquen pel seu NSS i també emmagatzemem el seu nom. No es donarà
mai el cas en què un operari de neteja sigui també guàrdia urbà.
Les pintades les identifiquem per la persona que l’ha trobat més el moment en què l’ha trobat. Per
exemple: la pintada que va trobar la Marta el dia 5 de desembre de 2017 a les 13:35:44. Cal
també tenir en compte que les podríem identificar per la seva localització exacta més el moment
en què s’ha trobat. Exemple: la pintada que va aparèixer el dia 5 de desembre de 2017 a les
13:35:44 a 42.2655° N, 2.9581° E.

**Llegeix atentament aquest Univers de Discurs i fes el seu Model Conceptual
de Dades en format Model Entitat-InterRelació CrowFoot, després fes el pas a Create Table.**


L’empresa RetFlix és una
plataforma online de
visualització de sèries. Cada
sèrie té un títol més any inici i
any fi ( aquest pot deixar-se en
blanc ), les sèries s’ientifiquen
pel seu títol més any inici
perquè un mateix títol es pot estrenar en diferents anys.

Les sèries tenen capítols.
Que s’identifiquen per
número de capítol, número
de temporada i sèrie a la
que pertanyen. Ens
interessa, a més, el títol de
cada capítol.
Cada capítol té una série de
comentaris que posen els
usuaris. Cada comentari té
un número que l’identifica i
és independent del capítol. A
més té un text amb el text
del comentari. Poden haver
capítols sense comentaris,
però sempre que tenim comentaris seran d’un capítol.
Fés el MCD amb les seves 3 entitats. Fes molta atenció a les dependències i no dependències en
identificació. Escriu els 3 create tables per crear les taules a la base de dades.

---

#FpInfor #Daw #Dam #Asix #AsixMp02 #DawMp02 #DamMp02 #DawMp02Uf01 #AsixMp02Uf01 #DamMp02Uf01

---

###### Autor: daniel herrera 2017.12.11 17:14:10
###### Editat per: daniel herrera 2017.12.11 17:14:10
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
