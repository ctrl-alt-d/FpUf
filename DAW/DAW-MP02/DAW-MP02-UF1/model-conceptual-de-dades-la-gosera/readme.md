# Model Conceptual de Dades - La gosera
## DAW-MP02-UF1 - Exercici de Introducció a les bases de dades
###Llegeix aquest Univers de Discurs tot identificant les entitats, atributs i relacions.

Una gossera vol mantenir una BDD amb informació dels gossos que té i ha tingut. Et demanen
que creis a partir del següent Univers de Discurs un MCD en format Martin amb “notació
PowerDesigner”. Et faciliten la següent informació: Tots els gossos tenen un xip (perquè si no
el tenen els hi posen a la gossera) amb un número que identifica el gos. Els gossos poden tenir
nom. El gos pot ser de raça o no, tenim totes les races entrades a la bdd i si el gos és de raça
llavors cal assignar-li. Un mateix gos pot entrar i sortir moltes vegades de la gossera, cal tenir
un registre d'això amb la data d'entrada i de sortida i una descripció de l'estat en que es troba
l'animal a l'entrada a la gossera. Per identificar aquestes instàncies es fa mitjançant el número
de xip del gos més la data d'entrada a la gossera. Mai no s'esborren instàncies de gos, si el gos
és mort cal saber-ho. Comprova que tota instància té AIP (ja sigui mitjançant atributs de la
pròpia instància o d'entitats interrelacionades).

### Exercici:

* Fes el diagrama del MCD amb notació Chen i amb [notació Crow's foot](http://en.wikipedia.org/wiki/Entity%E2%80%93relationship_model#Crow.27s_Foot_Notation)

####Notes:

Aquest exercici és especialment interessant per a tractar la cardinalitat (0,1). Fixeu-vos que el gos pot o no tenir raça. Aquest és un exemple típic que utilitzo per il·lustrar les interrelacions 1:N on una entitat no té perquè tenir correspondència amb l'altre. Fixeu-vos també en la utilitat per a fer *outers joins* .



---

#FpInfor #Daw #Dam #Asix #AsixMp02 #DawMp02 #DamMp02 #DawMp02Uf01 #AsixMp02Uf01 #DamMp02Uf01

---

###### Autor: daniel herrera 2013.09.07 09:54:16
###### Editat per: daniel herrera 2013.09.07 09:54:16
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
