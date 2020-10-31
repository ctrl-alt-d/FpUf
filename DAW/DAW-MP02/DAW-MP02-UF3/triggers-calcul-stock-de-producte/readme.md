# Triggers càlcul stock de producte
## DAW-MP02-UF3 - Exercici de Llenguatges SQL: DCL i extensió procedimental
Una empresa disposa d'una base de dades amb la següent estructura de taules:

* `MovimentDeMagatzem`: id moviment (pk), data, producte (fk), qtat 
* `Productes`: id producte (pk), nom

La quantitat a `MovimentDeMagatzem` pot prendre valors possitius ( quan entra material al magatzem ) i valors negatius ( quan en surt ).

L'empresa desitja no haver de fer una agregació sobre `MovimentDeMagatzem` per saber la quantitat d'stock d'un producte, de manera que vol afegir la columna `stock` a productes.

Exercici:

1. Crea les taules tal i com són ara a la base de dades.
2. Inserta dades de productes i moviments de magatzem.
3. Afegeix el camp `stock` a producte, not null valor per defecte 0.
4. Actualitza la columna stock des de la taula de moviments. Hauràs de fer un update amb joins. Busca com fer-ho.
5. Crea un trigger de manera que a partir d'ara la columna stock s'actualitzi automàticament quan s'insertin `MovimentDeMagatzem`.
6. Crea un trigger de manera que a partir d'ara la columna stock s'actualitzi automàticament quan s'esborrin `MovimentDeMagatzem`.
7. Crea un trigger de manera que a partir d'ara la columna stock s'actualitzi automàticament quan es modifiquin `MovimentDeMagatzem`.


**Notes importants**: 

* el trigger ha d'actuar incrementalment, no val tornar a sumar tots els moviments de magatzem cada cop.
* si vols, primer fes el trigger suposant que les fileres a `MovimentDeMagatzem` sempre s'inserten, s'esborren o s'actualitzen d'una en una. Després modifica el trigger per a que sàpiga treballar amb insercions de conjunts de fileres.

**Solució parcial**

```sql
;WITH ACUMULAT_MAGATZEM AS
     (SELECT ID_PRODUCTE, SUM(QTAT) AS QTAT
	 FROM MOVIMENTS_MAGATZEMS
	 GROUP BY ID_PRODUCTE)
UPDATE P
SET STOCK =  M.QTAT 
FROM PRODUCTES P
INNER JOIN ACUMULAT_MAGATZEM M
ON P.ID = M.ID_PRODUCTE;

go
CREATE TRIGGER INSERT_MOV_MAGATZEMS
ON MOVIMENTS_MAGATZEMS
AFTER INSERT, UPDATE AS BEGIN
   UPDATE P
     SET STOCK = STOCK + QTAT
	 FROM 
	     PRODUCTES P
	 INNER JOIN 
		 (SELECT ID_PRODUCTE, SUM(QTAT) AS QTAT
		 FROM INSERTED
		 GROUP BY ID_PRODUCTE) M
	 ON P.ID = M.ID_PRODUCTE
END;


go
CREATE TRIGGER DELETE_MOV_MAGATZEMS
ON MOVIMENTS_MAGATZEMS
AFTER DELETE, UPDATE AS BEGIN
   UPDATE P
     SET STOCK = STOCK - QTAT
	 FROM 
	     PRODUCTES P
	 INNER JOIN 
		 (SELECT ID_PRODUCTE, SUM(QTAT) AS QTAT
		 FROM DELETED
		 GROUP BY ID_PRODUCTE) M
	 ON P.ID = M.ID_PRODUCTE
END;
```

---

#FpInfor #Daw #Dam #Asix #AsixMp02 #DawMp02 #DamMp02 #DamMp02Uf03 #DawMp02Uf03 #AsixMp02Uf03

---

###### Autor: daniel herrera 2017.04.19 17:26:56
###### Editat per: daniel herrera 2017.04.24 18:46:07
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
