# Àrbitres i partits
## DAW-MP02-UF1 - Exercici de Introducció a les bases de dades
Es vol dissenyar una base de dades per emmagatzemar **partit**s de fultbol de la lliga.

Es disposa de la relació d'**equip**s amb el nom de l'equip (AIP). Cada **partit** s'identificaper la temporada, el número de jornada i el partit que juga a casa. A més del partit ens cal saber els gols a favor i gols en contra. Els partits s'entren a la base de dades abans de ser disputats, per aquest motiu, de vegades, no es disposa d'aquesta informació.

Tenim la relació de col·legiats amb el número de col·legiat com AIP i el seu nom.

Un col·legiat **pita** entre 0 i molts partits. I un partit és **pita**t per un número indeterminat de col·legiats, mínim 1, cadascun d'ells fent una funció diferent al camp. Aquesta interrelació N:M amb atributs s'identifica a partir de la dependència en identificació de les dues interrelacions: cap a arbitre i cap a partit. La funció que fa cada arbitre al partit així com si l'arbit ja ha cobrat o no aquell desplaçament són atributs de la interrelació.

Aquí éstà l'SQL DDL de la base de dades:


```sql
CREATE TABLE equips (
    nom varchar(200) not null,
	CONSTRAINT equip_pk PRIMARY KEY ( nom )
);
CREATE TABLE partits (
    temporada int not null,
	num_jornada int not null,

	-- FK a equip local
	nom_equip_local varchar(200) not null,

	-- FK a equip visitant
	nom_equip_visitant varchar(200) not null,

	gols_equip_local int null,
	gols_equip_visitant int null,

	CONSTRAINT partit_a_equip_local_fk
	   FOREIGN KEY ( nom_equip_local )
	   REFERENCES equips ( nom ),

    CONSTRAINT partit_a_equip_visitant_fk
	   FOREIGN KEY ( nom_equip_visitant )
	   REFERENCES equips ( nom ),

	CONSTRAINT partit_pk
	   PRIMARY KEY ( temporada, num_jornada, nom_equip_local  )
);
CREATE TABLE arbits (
  num_collegiat int not null,
  nom varchar(400 ) not null,
  numero_de_compte_bancari varchar(40) null,
  CONSTRAINT arbit_pk
     PRIMARY KEY ( num_collegiat )
);
CREATE TABLE pita (
   --FK a arbit
   num_collegiat int not null,

   --FK a partit
    temporada int not null,
	num_jornada int not null,
	nom_equip_local varchar(200) not null,

   --atributs de la relació
   funcio_del_collegiat_al_partit varchar(500) not null,
   data_de_pagament date,

   --constraints
   CONSTRAINT pita_a_collegiat_fk
      FOREIGN KEY ( num_collegiat )
	  REFERENCES arbits ( num_collegiat ),

   CONSTRAINT pita_a_partit_fk
      FOREIGN KEY ( temporada, num_jornada, nom_equip_local )
	  REFERENCES  partits ( temporada, num_jornada, nom_equip_local ),

   CONSTRAINT pita_pk
      PRIMARY KEY (num_collegiat, temporada, num_jornada, nom_equip_local   )

);
```


**Recorda**: 

1. Recorda que una cardinalitat (1,1) implica una clau forana `not null`. En canvi una cardinalitat (0,1) implica una clau forana `null`.
2. Quan hi ha dependència en identificació, els atributs propagats, a més de ser clau forana, fomen part de la clau primària.
3. Les taules tindran tantes restricció `foreign key` com interrelacions els 'arribin'.

**Exercici**:

Crea el MCD a partir d'aquest univers de discurs i d'aquest SQL.

**Physical data model**:

![PDM partits de futbol](http://i.imgur.com/gb7g2Jv.png)

---

#FpInfor #Daw #Dam #Asix #AsixMp02 #DawMp02 #DamMp02 #DawMp02Uf01 #AsixMp02Uf01 #DamMp02Uf01

---

###### Autor: daniel herrera 2016.11.21 18:52:41
###### Editat per: daniel herrera 2016.11.21 19:44:46
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
