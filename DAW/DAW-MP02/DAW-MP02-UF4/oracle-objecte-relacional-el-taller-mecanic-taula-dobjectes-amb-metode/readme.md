# Oracle Objecte-Relacional - Estoc d'articles - Taula d'objectes amb mètode
## DAW-MP02-UF4 - Exercici de Bases de dades objectes-relacionals
**Objectiu didàctic**

 * Treballar amb taules d'objectes.
 * Invocar mètodes de l'objecte

**Pràctica**

Mantenir una taula d'articles, per cada `article` emmagatzemem, a més del nom, l'estoc ( `quantitat` ) i el `preu`. Disposem del mètode `sumar` que ens calcula el valor de l'estoc ( quantitat * preu ):

DDL: Creació dels tipus i la taula:

```SQL
CREATE OR REPLACE TYPE article AS OBJECT (
  quantitat NUMBER,
  preu NUMBER,
  nom VARCHAR2(100),
  codi NUMBER,
  MEMBER FUNCTION sumar RETURN NUMBER
  );
  
CREATE OR REPLACE TYPE BODY article AS
  MEMBER FUNCTION sumar RETURN NUMBER IS
  BEGIN
    RETURN quantitat * preu;
  END;
END;

CREATE TABLE inventari OF article;
```

Inserció d'objectes dins la taula d'objectes:



```SQL
INSERT INTO inventari VALUES(article(70,2,'pomes',1));
INSERT INTO inventari VALUES(article(150,1,'peres',2));
INSERT INTO inventari VALUES(article(60,3,'maduixes',3));
INSERT INTO inventari VALUES(article(30,4,'cireres',4));
```

Selecció del valor de cada article:

```SQL
SELECT i.nom, i.sumar() as "Valor de l'estoc" 
FROM inventari i;
```

Agregació del valor de tot l'estoc d'articles:

```SQL
SELECT sum(i.sumar()) as TOTAL FROM inventari i;
```

Actualitzacions:

```SQL
UPDATE inventari i SET i.quantitat = 70 
WHERE i.codi = 1;
```

Esborrat:

```SQL
DELETE FROM inventari i WHERE i.codi = 2;
```

**Exercicis**

Executa aquestes sentències al teu entorn Oracle tot comprovant i entenent els resultats.

*By G.Gassó & Senglar Salvatge (DAW'2014)*

---

#FpInfor #Daw #DawMp02 #DawMp02Uf04

* Resultats d'aprenentatge 1.B 1.D 1.F 1.G
* Continguts 1.1 1.3 1.4 1.8 1.9 1.10
---

###### Autor: daniel herrera 2014.04.11 13:44:51
###### Editat per: daniel herrera 2014.04.11 15:41:28
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
