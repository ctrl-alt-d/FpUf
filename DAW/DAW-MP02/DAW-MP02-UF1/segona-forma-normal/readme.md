# Segona forma normal
## DAW-MP02-UF1 - Exercici de Introducció a les bases de dades
**Definició**

>A table that is in first normal form (1NF) must meet additional criteria if it is to qualify for second normal form. Specifically: a table is in 2NF if it is in 1NF and no non-prime attribute is dependent on any proper subset of any candidate key of the table. A non-prime attribute of a table is an attribute that is not a part of any candidate key of the table.

**Interpretació**

Una relació, per estar en segona forma nomal, ha destar en primera forma normal i, tot atribut ha de dependre de la totalitat dels atributs de la clau primària.

Exemple, suposem aquesta relació:

```bash
Notes
_Alumne   Població  _Avaluació  Nota 
  Pere       Roses           1     8 
  Pere       Roses           2     7 
  Pere       Roses           1     5 
 Marta        Olot           1     8 
```

La clau primària estaria formada per Alumne + Nota. Aquest conjunt d'atributs és determinant de qualsevol altre atribut. Tanmateix detectem que Població no depen de tota la clau primària, només depen d'Alumne. Per tant no està en segona forma normal.

**Pas a segona forma normal**

Cal moure els atributs que no depenen funcionalment de tota la clau primària a una altre taula juntament amb una còpia del seu determinant, en aquest cas el determinant pasarà a ser clau primària. Al nostre exemple:

```bash
Notes
_Alumne  _Avaluació  Nota 
   Pere           1     8 
   Pere           2     7 
   Pere           1     5 
  Marta           1     8 
```

    Alumnes
    _Alumne  Població  
      Pere     Roses
     Marta      Olot


**Exercici**

1) Normalitza aquesta taula:

```bash
_Jugador  Country       _Dia    MàximaPuntuació     
    Zoom      Cat   1/9/2016                24K    
    Zoom      Cat   2/9/2016                23K    
   Creep    Italy   1/9/2016                45K   
   Creep    Italy   2/9/2016                13K   
  Nation   Algery   2/9/2016                78K   
```

Comprova si està en segona forma normal. Si no és així, normalitza-ho.

2) Normalitza aquesta taula:

```bash
_Jugador  Country       _Dia    MàximaPuntuació     ActualRanks
    Zoom      Cat   1/9/2016                24K    Ninja,Savage
    Zoom      Cat   2/9/2016                23K    Ninja,Savage
   Creep    Italy   1/9/2016                45K   Skilled,Loyal
   Creep    Italy   2/9/2016                13K   Skilled,Loyal
  Nation   Algery   2/9/2016                78K       Moderator
```

Comprova si està en segona forma normal. Si no és així, normalitza-ho.



>
>######Aquest exercici està extret del llibre [d'exercicis Introducció a les Bases de Dades. UF1 MP2 DAM DAW ASIX](https://www.amazon.es/Introducci%C3%B3-Bases-Dades-asix-MP02-UF1/dp/153735096X) amb permís del seu autor. 
>



---

#FpInfor #Daw #Dam #Asix #AsixMp02 #DawMp02 #DamMp02 #DawMp02Uf01 #AsixMp02Uf01 #DamMp02Uf01

---

###### Autor: daniel herrera 2016.08.27 16:54:54
###### Editat per: daniel herrera 2016.08.30 16:58:29
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
