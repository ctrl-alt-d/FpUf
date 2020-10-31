# La gossera. Diferents tipus de Joins.
## DAW-MP02-UF2 - Exercici de Llenguatges SQL: DML i DDL
Al disseny de base de dades de vegades ens trobem amb dues entitats *fortes* interrelacionades amb tipus de correspondència 1:N i cardinalitats (0:1). Jo sempre poso l'exemple de *la gossera*, on trobem `Raça`i `Gos`. Podem tenir instàncies de `raça` encara que no tinguem gos i instàncies de `Gos` que no siguin de raça.

```bash
Gos: num_xip (pk), nom, codi_raça (fk a Raça)
Raça: codi_raça (pk), nom
```

* [Vídeo introducció i conceptes](https://youtu.be/NKk9LEXqwJs)
* [Vídeo correcció exercici](https://youtu.be/h1YERIeT4yY)

**Exercici:**

* Crea les taules *races* i *gossos*. Crea la restricció d'integritat entre les dues taules, pensa que poden haver gossos sense raça.
* Entra al menys 10 races i 10 gossos ( amb races sense gos i gossos sense raça)
* Observa el diagrama que apareix a [Difference between INNER and OUTER joins](http://stackoverflow.com/a/16598900/842935) i escriu una select per a cada combinació del diagrama.
* Documenta cada select tot indicant quines dades mostrarà, ex: *gossos i races per aquells gossos que són de raça*, *tots els gossos amb les dades de la raça ( en cas que el gos sigui de raça )*, etc.

![sql joins](http://i.stack.imgur.com/1UKp7.png "SQL Joins")
Source: **[Visual-Representation-of-SQL-Joins](http://www.codeproject.com/Articles/33052/Visual-Representation-of-SQL-Joins)** explained in detail by **[C.L. Moffatt](http://www.codeproject.com/script/Membership/View.aspx?mid=5909363)**

---

#FpInfor #Daw #Dam #Asix #AsixMp02 #DawMp02 #DamMp02 #DawMp02Uf02 #AsixMp02Uf02 #DamMp02Uf02

---

###### Autor: daniel herrera 2014.12.14 21:31:51
###### Editat per: daniel herrera 2018.01.19 15:27:37
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
