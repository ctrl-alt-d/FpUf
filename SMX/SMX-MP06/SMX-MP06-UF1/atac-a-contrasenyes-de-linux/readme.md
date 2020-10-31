# Atac a contrasenyes de Linux
## SMX-MP06-UF1 - Exercici de seguretat passiva. 
Una de les formes d'accedir al un sistema és conèixer les contrasenyes dels usuaris que conté. El sistema operatiu mentre està funcionant protegeix els fitxers de contrasenyes perquè els usuaris no autoritzats no hi tinguin accés. 

Però si s'inicia un sistema amb un LiveCD o un Pendrive els mecanismes de protecció del sistema operatiu no funcionen i per tant tothom pot aconseguir copiar-los

Un cop aconseguits caldrà descobrir les contrasenyes. El més simple és fer el que es coneix com atacs de força bruta que consisteix en provar totes les combinacions de contrasenyes possibles esperant que una sigui la correcta. 

Com que els atacs de força bruta normalment normalment tardarien massa el que es més habitual és recórrer a reduir les possibilitats provant contrasenyes que són més “provables”. Per fer aquest atac normalment s'intenta aprofitar el fet de que les persones normalment fan servir contrasenyes senzilles o relacionades amb ells o simplement paraules en el seu idioma

Per facilitar la tasca de descobrir les contrasenyes dèbils s'han creat una sèrie de llistes de paraules anomenades diccionaris o wordlists que solen estar agrupades per temes o idiomes i que se'n poden trobar molts a Internet

###Atacar fitxers de contrasenyes de Linux
Les contrasenyes en els fitxers en els sistemes Unix o Linux estan en el fitxers /etc/passwd o /etc/shadow. Per tant un atacant que aconsegueixi aquests fitxers tindrà la possibilitat d'aconseguir les contrasenyes en el seu ordinador sense que en quedi cap rastre

Per defecte el sistema protegeix els fitxers dels accessos dels usuaris no autoritzats però l'administrador i sol tenir accés.

El programa més usat per atacar les contrasenyes de Linux és “John the ripper” (que també es pot fer servir per atacar contrasenyes de Windows).

Generalment s'aconsella començar l'atac amb la opció *-single* que prova contrasenyes per defecte

    $ ./john  -single /etc/shadow

Per atacar contrasenyes amb un diccionari s'especifica amb el paràmetre -w

    $ ./john  --wordlist:diccionari /etc/shadow

També permet provar contrasenyes de subconjunts predefinits amb -i. Per exemple -i:Alpha prova totes les combinacions de caràcters en minúscules fins a 8 caràcters,  i -i:Digits fa el mateix amb els números

    $ ./john  -i:Digits /etc/shadow

Tasca
------------
1. En una màquina virtual en Linux afegiu 10 usuaris al sistema amb contrasenyes diverses (però no molt complexes)
2. Localitzeu a Internet pàgines en les que s'ofereixin wordlists per descarregar
3. Recupereu el fitxer de contrasenyes del sistema. Quina informació obteniu d'aquest fitxers?
4. Explica detalladament el procediment que et faria falta per recuperar els fitxers de contrasenyes d'un sistema en Linux (feu la prova amb una màquina virtual) i fes-ho amb John the ripper. Quantes contrasenyes per segon prova en el vostre sistema?
5. Localitzeu algun entorn gràfic per John, com Johnny, i expliqueu com es fan les diferents opcions

---

#FpInfor #Smx #SmxMp06 #SmxMp06Uf01

* Resultats d'aprenentatge 1.8
* Continguts 1.7
---

###### Autor: Xavier Sala 2013.10.28 11:49:23
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
