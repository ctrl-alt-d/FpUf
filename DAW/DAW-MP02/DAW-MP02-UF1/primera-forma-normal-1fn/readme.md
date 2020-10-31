# Primera forma normal (1FN)
## DAW-MP02-UF1 - Exercici de Introducció a les bases de dades
**Definició**

First normal form (1NF) is a property of a relation in a relational database. A relation is in first normal form if and only if the domain of each attribute contains only atomic (indivisible) values, and the value of each attribute contains only a single value from that domain.[1] 

**Interpretació**

No podem trobar atributs multivaluats. És a dir, camps on hi entaforem més d'un valor.

**Solució**

Cal despivotar les dades que no estan en primera forma normal. Exemple:

```bash
Nom  Telf1   Telf2  Telf3
Pere    12      42     -
Marta   15       -
```

Un cop normalitzat:

    _Nom  Telf
    Pere    12
    Pere    42
    Marta   15


**Experiència**

Sempre arriba algun llest que vol reinventar la roda. I llavors proposa posar en un camp de la base de dades un conjunt d'informació separades per comes. Tot sembla una gran idea fins que la base de dades creix i aquella taula cal relacionar-la amb una altre mitjançant aquell camp. Una base de dades que no està en primera forma normal és diu Non First Normal Form  == NFNF == NF²

**Exercici**

Llegeix [Is storing a delimited list in a database column really that bad?](http://stackoverflow.com/questions/3653462/is-storing-a-delimited-list-in-a-database-column-really-that-bad) i contesta:

* Si emmagatzemem dades separades per comes en un camp de la base de dades. Quin forma normal estem incomplint?
* Observa la resposta a la pregunta d'stacoverflow i documenta perquè és tant dolent treballar en NF²




>
>######Aquest exercici està extret del llibre [d'exercicis Introducció a les Bases de Dades. UF1 MP2 DAM DAW ASIX](https://www.amazon.es/Introducci%C3%B3-Bases-Dades-asix-MP02-UF1/dp/153735096X) amb permís del seu autor. 
>

---

#FpInfor #Daw #Dam #Asix #AsixMp02 #DawMp02 #DamMp02 #DawMp02Uf01 #AsixMp02Uf01 #DamMp02Uf01

---

###### Autor: daniel herrera 2016.08.27 16:26:29
###### Editat per: daniel herrera 2016.08.30 16:58:16
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
