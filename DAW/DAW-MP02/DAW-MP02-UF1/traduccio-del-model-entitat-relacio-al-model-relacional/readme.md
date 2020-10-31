# Traducció del model entitat-relació al model relacional I
## DAW-MP02-UF1 - Exercici de Introducció a les bases de dades
Anem a repassar com es fa per traduir element a element del model entitat inter-relació a model relacional.

* Dominis: Normalment no es declaren dominis, es treballa amb els tipus pre establerts que cada fabricant proporciona ( INT, VARCHAR, etc ).
* Entitat: Cada entitat es converteix a una relació i, en el cas de base de dades, en una taula.
* Atributs: Cada atribut del model entitat inter-relació serà un atribut del model relacional, a les bases de dades es correpon amb una columna.
* AIP: Serà una clau primària.
* AIC: Serà una restricció de tipus UNIQUE.

Anem a fer un exemple fins aquí, suposem l'entitat:

![Exemple entitat](http://i.imgur.com/HDAqNll.png)

La relació seria:

```sql
CREATE TABLE professors (
   Inicials char(3) NOT NULL,
   DNI varchar(9) NOT NULL,
   Nom varchar(200) NOT NULL,
   email varchar(200) NOT NULL,
   data_neixement date NULL,
   CONSTRAINT professors_pk PRIMARY KEY ( Inicials ),
   CONSTRAINT professors_dni_unique UNIQUE ( DNI ),
   CONSTRAINT professors_nom_unique UNIQUE ( nom ),
   CONSTRAINT professors_email_unique UNIQUE ( email )
)

```
* Fixa't bé amb l'ús de les comes. És un error frequent equivocar-se amb les comes.
* Si un AIP estés format per més d'un atribut els posariem tots dintre dels parèntesi.

![Exemple](http://i.imgur.com/4XzB5TW.png)

```sql
CREATE TABLE activitats (
   data date NOT NULL,
   nom NOT NULL,
   quantitat_de_public int,
   cost money,
   ingressos money,
   CONSTRAINT activitats_pk PRIMARY KEY (data, nom )
)
```

Per últim la traducció de les inter-relacions. Per traduir una inter-relació del model entitat inter-relació a model relacional el que fem, en aquest darrer, és una **propagació de claus**. És a dir, els atributs que formen la clau primària a la taula referenciada es copien, en forma de clau forana, a la taula que referencia. Exemple:

![Exemple](http://i.imgur.com/c7UKEXP.png)

La taula referenciada és piscina i la taula que referencia és tractament. El resultat seria:

```sql
CREATE TABLE piscines (
    Codi char(5) NOT NULL,
    ...,
    CONSTRAINT  piscines_pk PRIMARY KEY ( Codi )
);

CREATE TABLE tractaments (
    data_i_hora datetime not null,
    codi_tecnic char(3) not null,
    explicacio text,
    codi_piscina char(5) NOT NULL,
    CONSTRAINT tractaments_pk 
        PRIMARY KEY (data_i_hora, codi_tecnic ),
    CONSTRAINT piscina_fk 
        FOREIGN KEY ( codi_piscina )
        REFERENCES piscines ( Codi )
);
```

**Quan una entitat és dèbil, té dependència en identificació, la clau forana formarà part de la clau primària**

Exercicis:

Pasa a model relacional en notació SQL els següents models entitat inter-relació:

1) **[Video solució YT](https://youtu.be/5KZLlox2HTY)**

![](http://i.imgur.com/i8KhNy0.png)

2) **[Video solució YT](https://youtu.be/pQcMId4yG6w)**

![](http://i.imgur.com/MpUoGWy.png)

3)

![](http://i.imgur.com/kSyiPqw.png)

4)

![](http://i.imgur.com/Ik0JnYQ.png)

[Video Solució al YT](https://youtu.be/VhWpxztVdM0)

5)

[La lligueta](/DAW/DAW-MP02/DAW-MP02-UF1/entitat-inter-relacio-problema-la-lligueta/readme.md)  

* [MCD d'ajuda a l'imgur](https://i.imgur.com/ssN7a62.png) )
* [Video Solució al YT. Part 1](https://youtu.be/8qyF0JhOkQY) | [Video Solució al YT. Part 2](https://youtu.be/eiEcr9lGBwA)
* [SQL Solució al PasteBin](https://pastebin.com/14g81UFP)

>
>######Aquest exercici està extret del llibre [d'exercicis Introducció a les Bases de Dades. UF1 MP2 DAM DAW ASIX](https://www.amazon.es/Introducci%C3%B3-Bases-Dades-asix-MP02-UF1/dp/153735096X) amb permís del seu autor. 
>

---

#FpInfor #Daw #Dam #Asix #AsixMp02 #DawMp02 #DamMp02 #DawMp02Uf01 #AsixMp02Uf01 #DamMp02Uf01

---

###### Autor: daniel herrera 2016.08.25 17:17:53
###### Editat per: daniel herrera 2017.12.03 16:37:23
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
