# Exercicis entrenament examen
## DAW-MP01-UF1 - Exercici de Instal·lació, configuració i explotació del sistema informàtic
Exercicis entrenament examen:

1) L'hospital Jackson Memorial de Miami ha decidit crear una base de dades amb registre d'accidents derivats de la
pràctica nàutica. És per això que li cal un disseny de base de dades per poder després emmagatzemar aquests fets. La
entitat més important serà **accident**. Els accidents estan classificats, i cada accident només pot estar dins d'una
**classificació**. Les classificacions, per ara, són pesca, suft, winsurf, taurons i rem. Tanmateix s'espera que s'amplii el número de classificacions. Cada
classificació té un codi de dues lletres que l'identifica. Els accidents s'identifiquen per un número que és correlatiu i únic dins
cada categoria (accident 1 de pesca, accident 1 de winsurt, ... ). Ens interessa la data de l'accident i un text del que ha passat.

![Imgur](http://i.imgur.com/97tYJBv.png)

Quan un pacient arriba a l'hospital se li fa l'**ingrés**,
ens cal saber quina persona (**personal sanitari**)
li fa l'ingrés. I el seu cas (durant l'**ingrès** ) el porta un metge, ens
cal saber quin metge el porta (**doctor**). Tant el
metge com el personal sanitari són **empleats** de
l'hospital i els identifiquem pel nif i
emmagatzemem nom i cognoms. Però dels
metges, a més, emmagatzemem el número de
col·legiat i del personal sanitari una descripció de
la seva titulació.

Pot arribar gent a l'hospital que se el seu ingrés no hagi estat degut a un accident, però en cas de ser degut a un accident ens cal saber quin accident ha estat.

Dels pacients ens interessa el nom i cognoms i el seu número de tarja sanitària. Els identifiquem per un codi intern. Una persona no és pacient fins que no ha estat ingressada al menys un cop a l'hospital. No cal dir que un mateix pacient pot haver estat ingressat varies vegades.

Els metges estan organitzats en departaments (neonats, transplantaments, cardiologia, etc). Cada departament té un codi que l'identifica. Un metge pot estar
en més d'un departament. Ens cal un **històric** del
pas dels metges pels diferents departaments
(data inici i data fi). Un metge pot marxar d'un departament i tornar més endavant, tigues-ho en compte a l'hora de determinar l'AIP de l'**històric**.

Entregables:

MCD: es valorarà que les relacions siguin
correctes, les cardinalitats, els tipus de
correspondència i, molt especialment, la
identificació dels accidents.
Create table de classificació i accident: es valorarà els tipus de dades triats, la composició de claus primàries i claus foranes

**Versió correcció a la pizarra**:

![Imgur](http://i.imgur.com/vAlBurk.jpg)

**Versió Hamza Saddouki**:

![Imgur](http://i.imgur.com/DD92dE7.png)

2) Fes dos diagràma / gràfic / dibuix, el primer que representi tot l'escenari de construcció / disseny / posada en marxa
d'un sistema informàtic (acotat a la part de BDD). Posant a l'esquerra el món dels negocis amb els requeriments més
abstractes i a la dreta el móm més físic de sistemes informàtics. Entre els dos extrems representa els elements intermitjos
que utilitza un informàtic per arribar del món del negoci al món dels ordinadors. El segon que representi un sistema de base
de dades amb els usuaris accedint-t'hi. Tingues en compte els nivells ansi / x3 / sparc. Es valorarà que l'alumne conèix totes
les passes per arribar del món del negoci al món informàtic. Es valorarà que l'alumne conèix els elements i actors d'un
sistema informàtic amb bdd i el model ansi / x3 / sparc

3) Una empresa vol el disseny d'una base de dades on emmagatzemar les vendes que realitza als seus clients. Els clients
estan identificats pel seu cif i a més emmagatzemem el nom, telèfon, n fax i adreça. De cada client emmagatzemem
varies persones de contacte. Les persones de contacte s'identifiquen pel seu nom i cognoms (pot haver persones que
es diguin igual a diferents empreses, però mai dins una mateixa empresa. Això cal tenir-ho en compte) De les
persones de contacte emmagatzemem a més l'e-mail (que de vegades no el tenim) i el mòbil. L'empresa ven
productes que s'indentifiquen pel seu nom i a més ens cal emmagatzemar el preu actual. El sistema emmagatzema
factures, cada factura té un identificador únic. Una factura té una data, una descripció i unes línies de factura. Cada
línia de factura ens informa de quin producte ha venut l'empresa, en quina quantitat i a quin preu. Un mateix producte
no es repeteix a dins una factura, això ens ajuda a trobar un identificador únic per a les línies de factures doncs
aquestes no tenen codi línia.

Fes el MCD i fes els create table de factura i línia de factura.

4) L'empresa LiberaTuMobil.com funciona de la següent manera: un client porta un mòbil, llavors prenen les dades del
client i creen un ParteDeLiberación (PL a partir d'ara). El PL ens indica: de quin model de mòbil es tracta, de quin client
es tracta, quin empleat fa la recollida del mòbil, la data de recollida i el presssupost per liberar el mòbil. Cada PL té un
codi.

La base de dades també té totes les marques i models de mòbil del mercat. També totes les operadores. Per a cada
model de mòbil i operadora tenim un preu de referència d'alliberament.
Quan es fa l'alliberament també s'anota al PL el tècnic que ha fet l' alliberament (aquesta informació és diferent a
l'empleat que recull el mòbil, calen totes dues (sempre tindrem qui recull, no sabrem qui allibera fins que no s'hagi fet
l'operació). Tant els tècnics com empleats es consideren treballadors. Aquests s'identifiquen pel seu NSS i també
emmagatzemem la data de contractació.

Fes el MCD i fes els create table de treballador i PL.

---

#FpInfor #Daw #Dam #Asix #AsixMp01 #DamMp01 #DawMp01 #AsixMp01Uf01 #DawMp01Uf01 #DamMp01Uf01

---

###### Autor: daniel herrera 2016.11.22 15:12:34
###### Editat per: daniel herrera 2016.11.23 10:24:52
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
