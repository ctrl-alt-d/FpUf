# Oracle Objecte-Relacional - Consum combustible i autonomia - Taula amb objecte i mètode
## DAW-MP02-UF4 - Exercici de Bases de dades objectes-relacionals
**Objectiu didàctic**

 * Treballar amb taules amb columna de tipus objecte.
 * Invocar mètodes de l'objecte

**Pràctica**

Volem calcular el autonomia d'un cotxe amb un determinat consum de carburant als 100km i amb una capacitat de dipòsit de carburant determinada.

Per fer-ho, haurem de crear un tipus, el tipus es dirà "consum_typ" i hi guardarem la capacitat del dipòsit i també el consum als 100km amb decimal, també tindrà una funció, la qual calcularà l' autonomia fent la operació (capacitat_diposit/consum)*100 com veurem més endavant:

```SQL
create or replace type consum_typ as object (
  capacitat_diposit   number,
  consum              float,
  member function autonomia return float
);
```

Ara creem la implementació de la funció `autonomia`, la qual ens retornarà la operació convenient en decimals: 

```SQL
create or replace type body consum_typ as
  member function autonomia return float is
  begin
    return (capacitat_diposit/consum)*100;
  end;
end;
```

Un cop fet tot això, crearem una taula anomenada `COTXE` per guardar diferents propietats dels cotxes en questió.
Les propietats són: `Marca`, `Tipus_vehicle` i `any_fabricació`. A més, tindrem l'objecte `consum` dins de la nostre taula.
*Recordem que estem fent l'exemple de crear una taula amb una columna objecte*

```SQL
CREATE TABLE COTXE ( 
  Marca             varchar2(25),
  tipus_vehicle     varchar2(25),
  any_fabricacio    number,
  consum            consum_typ
);
```

Un cop creada la taula, procedirem a fer els inserts pertintents per omplir els camps de la nostra taula, ho farem de la següent manera:

```SQL
insert into cotxe (Marca, tipus_vehicle, any_fabricacio, consum ) values
( 'HUMMER', 'tot terreny', 2014,
consum_typ ( 80, 17.8 )
);

insert into cotxe (Marca, tipus_vehicle, any_fabricacio, consum ) values
( 'Renault', 'berlina', 2014,
consum_typ ( 50, 5.5 )
);

insert into cotxe (Marca, tipus_vehicle, any_fabricacio, consum ) values
( 'Shellby', 'muscle car', 1967,
consum_typ ( 55, 16.4 )
);
```

Un cop fet tot això, i per acabar, fem la select cridant a la nostre funció per comprovar que funciona correctament i ens calcula l'autonomia de cada cotxe, ho fem de la següent manera:

```SQL
Select c.marca, c.tipus_vehicle, c.any_fabricacio, ROUND(c.consum.autonomia(),2) as     Autonomia 
from cotxe c;
```

El resultat serà el següent:


--------------------------------------------------------------------------------
|MARCA       |              TIPUS_VEHICLE      |       ANY_FABRICACIO  |   AUTONOMIA  |
|:------------|:-----------------------------|---------------------------:|-------:|
|HUMMER      |              tot terreny    |                     2014  |      449.44| 
|Renault     |              berlina        |                     2014  |      909.09| 
|Shellby     |              muscle car     |                     1967  |      335.37|

**Exercicis**

Executa aquestes sentències al teu entorn Oracle tot comprovant i entenent els resultats.

*By X.Oliveres & J.Pujol (DAW'2014)*

---

#FpInfor #Daw #DawMp02 #DawMp02Uf04

* Resultats d'aprenentatge 1.B 1.D 1.F 1.G
* Continguts 1.1 1.3 1.4 1.8 1.9 1.10 1.11
---

###### Autor: daniel herrera 2014.04.11 13:28:20
###### Editat per: daniel herrera 2016.04.01 16:36:17
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
