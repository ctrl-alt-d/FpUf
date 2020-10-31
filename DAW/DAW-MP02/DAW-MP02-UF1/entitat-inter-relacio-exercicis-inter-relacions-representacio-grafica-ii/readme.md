# Entitat inter-relació - Exercicis inter-relacions representació gràfica II
## DAW-MP02-UF1 - Exercici de Introducció a les bases de dades
Aquestes són les passes que algunes metodologies proposen pel diseny de l'estructura d'una base de dades:

![Del món real a la base de dades](http://i.imgur.com/kWhaeYO.png)

1. Contemplar el **món real**.
1. Redactar l'**Univers de Discurs**.
1. Fer el **CDM** (Model Conceptual de les Dades)
1. Fer el **LDM** (Model Lògic de les Dades)
1. Fel el **PDM** (Model Físic de les Dades)
1. Escriure les sentències per crear la DB ( Base de Dades)

Tanmateix, cal tenir em compte que el MCD és una eina molt poderosa que ens permet fer-nos una idea ràpida de les estructures de dades que conté una DB.

Per aquest motiu, tot i que la BD ja existeixi, de vegades ens interesa escriure el diagrama entitat inter-relació per compendre millor el sistema.

Això és el que es proposa en aquest exercici. A partir d'unes relacions que trobem en una base de dades cal fer enginyeria inversa fins arribar al MCD. 

**Exercici**

Observa detingudament aquestes relacions que ens proposa [@S-Buzz](http://stackoverflow.com/users/501636/s-buzz) a la seva pregunta d'stakoverflow [Correctly join 1:n:1:1 relation in mysql database](http://stackoverflow.com/questions/38137961/correctly-join-1n11-relation-in-mysql-database/38138213#38138213).

![Sistema de lloguers](http://i.imgur.com/F0fs50T.png)

1. Digues tots els objectes que ha llogat en John Doe i si ja els a tornat o no.
1. Construeix el PDM ( necessitaràs haver fet abans l'exercici [Entitat inter-relació - Exercicis inter-relacions representació gràfica](/DAW/DAW-MP02/DAW-MP02-UF1/entitat-inter-relacio-exercicis-inter-relacions-representacio-grafica/readme.md) ). 
2. Construeix el MCD. 
3. Comprova que al MCD no has inclòs, a les entitats, cap atribut que sigui forani elles. Per exemple, a l'entitat `rental` no ha d'apareixer l'atribut `person_person_id` (sí que ha d'apareixer la relació a `person`). 
4. L'entitat `rental2object` és, en realitat, una inter-relació sense atributs amb tipus de correspondència N:M entre `rental` i `object`. Tant si has creat l'entitat que representa la inter-relació com si només has fet la inter-relació N:M és correcte. Tantmateix, si has creat l'entitat, recorda incloure les dependències en identificació.
5. Escriu l'Univers de Discurs a partir del MCD.




>
>######Aquest exercici està extret del llibre [Introducció a les Bases de Dades](https://www.amazon.es/Introducci%C3%B3-Bases-Dades-asix-MP02-UF1/dp/153735096X) amb permís del seu autor.
>


#### Solució

**PDM**

![PDM](http://i.imgur.com/5wqqq6p.png)

**CDM**

![CDM](http://i.imgur.com/wpto7Zx.png)

Cal fixar-se que entre Object i Rental hi ha una inter-relació amb tipus de correspondència N:M.

---

#FpInfor #Daw #Dam #Asix #AsixMp02 #DawMp02 #DamMp02 #DawMp02Uf01 #AsixMp02Uf01 #DamMp02Uf01

---

###### Autor: daniel herrera 2016.07.04 09:07:27
###### Editat per: daniel herrera 2017.10.23 17:13:45
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
