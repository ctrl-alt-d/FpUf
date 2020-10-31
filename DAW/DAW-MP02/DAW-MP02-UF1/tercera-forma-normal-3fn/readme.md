# Tercera forma normal (3FN)
## DAW-MP02-UF1 - Exercici de Introducció a les bases de dades
**Definició**

>A table is in 3NF if and only if both of the following conditions hold:
>* The relation R (table) is in second normal form (2NF)
>* Every non-prime attribute of R is non-transitively dependent on every key of R.
>A non-prime attribute of R is an attribute that does not belong to any candidate key of R.[3] A transitive dependency is a functional dependency in which X → Z (X determines Z) indirectly, by virtue of X → Y and Y → Z (where it is not the case that Y → X).[4]

**Interpretació**

La tercera forma normal ens diu que no poden haver dependències transitives ( i que cal que es compleixi la 2a forma normal )

Una dependència transitiva es dona quan un atribut depen d'un altre atribut o conjunt d'ells que no formen part de la clau primària.

Per solucionar la tercera forma normal el que farem serà endur-nos els atributs que depenen transitivament de la clau primària a una altre relació juntament amb una còpia del seu determinant, que actuarà com a clau primària a la nova taula.

**Exemple**

Suposem aquesta taula:

```bash
Alumnes
_Alumne   Població     Comarca
  Pere       Roses  Alt Empordà
  Pere       Roses  Alt Empordà 
  Pere       Roses  Alt Empordà 
 Marta        Olot  La Garrotxa 
```

La clau primària està formada per Alumne. Però trobem un camp, Comarca, que depen transitivament d'Alumne, perquè depen de Població. Per tant, aquesta relació no està en tercera forma normal. Per passar-la a 3a forma normal crearem una altre taula:

```bash
Alumnes
_Alumne   Població     Comarca
  Pere       Roses  Alt Empordà
  Pere       Roses  Alt Empordà 
  Pere       Roses  Alt Empordà 
 Marta        Olot  La Garrotxa 
```

    Poblacions
    _Població        Comarca
        Roses    Alt Empordà
         Olot    La Garrotxa


**Exercicis**

1) Passa a tercera forma normal la següent relació:

```bash
_Jugador       Country       _Dia    MàximaPuntuació   Continent  
    Zoom           Cat   1/9/2016                24K      Europe
    Zoom           Cat   2/9/2016                23K      Europe
   Creep         Italy   1/9/2016                45K      Europe
   Creep         Italy   2/9/2016                13K      Europe
  Nation        Algery   2/9/2016                78K      Europe
  Smoker  Saudi Arabia   2/9/2016                67K        Asia
```

2) Observa aquestes tres preguntes d'stackoverflow, totes tres estan relacionades amb la violació de la primera forma normal. Documenta com proposen els OP's les taules i com quedarien un cop normalitzades. Si cal normalitzar fins a segona forma normal recorda fer la normalització pas a pas, primer 'despivotar' la taula per tal de cumplir amb la primera forma normal i, un cop fet això, passar a segona forma normal i a tercera si cal.

* [How can I have multiple items or element in a sql cell?](http://stackoverflow.com/questions/8593609/how-can-i-have-multiple-items-or-element-in-a-sql-cell)
* [T-SQL text sorting](http://stackoverflow.com/questions/8976703/t-sql-text-sorting)
* [SQL Server 2008 R2 Multiple Row Maths](http://stackoverflow.com/questions/18631178/sql-server-2008-r2-multiple-row-maths)




>
>######Aquest exercici està extret del llibre [d'exercicis Introducció a les Bases de Dades. UF1 MP2 DAM DAW ASIX](https://www.amazon.es/Introducci%C3%B3-Bases-Dades-asix-MP02-UF1/dp/153735096X) amb permís del seu autor. 
>

---

#FpInfor #Daw #Dam #Asix #AsixMp02 #DawMp02 #DamMp02 #DawMp02Uf01 #AsixMp02Uf01 #DamMp02Uf01

---

###### Autor: daniel herrera 2016.08.27 17:02:48
###### Editat per: daniel herrera 2016.08.30 16:58:37
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
