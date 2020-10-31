# Entitat inter-relació - Problema: La piulada
## DAW-MP02-UF1 - Exercici de Introducció a les bases de dades
**Introducció**

Problema molt tècnic on tot gira al voltant de dues entitats fortes molt definides: Usuari i Piulada. Cal ser capaç d'identificar correctament totes les relacions N:M, algunes amb atributs, d'aquestes dues entitats. Així com ser capaç d'identificar l'entitat subtipus de piulada que apareix al text.

**Univers de Discurs**

Un **grup de visionaris** d'Internet ha tingut una gran idea, crear la empresa **'Piula-la'**. Serà una **xarxa social** on els **usuaris** es registren i interaccionen entre ells. 

Per motius de rendiment del sistema a cada usuari se li assignarà un **identificador únic**, també se li permet a l'usuari triar un **nom d'usuari** i un **abatar**. Aquest darrer camp és opcional. El sistema emmagatzema a més la **data d'alta** dels usuaris.

Els usuaris poden fer **piulades**. Consisteixen en un text de màxim 140 caràcters. Els visionaris tenen pensat per més endavant permetre piular també amb fotos i videos, però per ara és suficient amb el text. A les piulades se'ls dona un **identificador únic de piulada** per trobar-la fàcilment si algú la vol compartir en altres xarxes socials. El sistema emmagatzema la **data** en que s'ha fet la piulada. També cal considerar crear un camp per emmagatzemar si aquella piulada és considerada pel sistema com a contingut ofensiu o per +18 anys. Aquest camp inicialment quedarà buit però més endavant, quan estigui més madur, el sistema ja l'informarà.

Qualsevol usuari pot veure piulades (sota uns algorismes que governaran el sistema). Ens interessa saber cada piulada quins usuaris l'han visualitzat i quan. També saber quins usuaris i quan han fet **'Like'** 
a la piulada o bé l'han **'repiulada'** (han pres un botó per a que altres usuaris la vegin).

Els usuaris es poden **seguir** els uns als altres. Un 'follow' representaria que un usuari comença a seguir un altre. Ens interessa conèixer els 'follows' i el **moment** en que es produeixen.

Hi ha un cas particular de Piulades que s'anomenen **'Piulades Patrocinades'**. És quan un usuari qualsevol inverteix diners per tal que l'algorisme del sistema faci que una determinada piulada la vegin més usuaris. Depenent de l'**import invertit** en el patrocini la veuran més o menys usuaris. Ens interessa saber quines piulades estan patrocinades, qui les patrocina i quans diners hi inverteix.

**Exercici**

* A partir de l'Univers de Discurs fel el Model Conceptual de dades mitjançant el diagrama ER.

>
>######Aquest exercici està extret del llibre [d'exercicis Introducció a les Bases de Dades. UF1 MP2 DAM DAW ASIX](https://www.amazon.es/Introducci%C3%B3-Bases-Dades-asix-MP02-UF1/dp/153735096X) amb permís del seu autor. **Al llibre hi trobareu la solució a l'exercici**.
>

---

#FpInfor #Daw #Dam #Asix #AsixMp02 #DawMp02 #DamMp02 #DawMp02Uf01 #AsixMp02Uf01 #DamMp02Uf01

---

###### Autor: daniel herrera 2016.07.04 13:04:53
###### Editat per: daniel herrera 2016.08.30 16:56:18
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
