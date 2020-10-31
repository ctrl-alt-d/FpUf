# Oracle Objecte-Relacional - Els soldats - Treballar amb col·leccions
## DAW-MP02-UF4 - Exercici de Bases de dades objectes-relacionals
**Objectiu didàctic**

 * Treballar amb col·leccions d'objectes.
 * Invocar mètodes de l'objecte.

**Pràctica**

*UNIVERS DE DISCURS*

L'exerici que farem serà una taula d'exercits. Cada exercit conté una divisió
que al mateix temps conté soldats.

Els soldats són objectes de tipus soldat, que contenen numero d'identicació, nom i rang.

Les divisions son taules de tipus divisió que contenen soldats (*col·leccions*)

Els exercits son objectes de tipus exercit que contenen un id, un pais, un tipus 
d'exercit ('terra', 'aire'...) i una divisió

La taula exercits conté un exercit i té una taula aniuada amb les divisions

Desprès modificarem l'exercit per afegir-li un mètode que ens retorni el capità de 
la seva divisió.

```SQL
--CREAR TIPUS SOLDAT 
CREATE TYPE soldat_tip AS OBJECT (
ni VARCHAR2(30),
nom VARCHAR2(20),
rang VARCHAR2(10)
);
/

--CREAR LA DIVISIÓ QUE CONTÉ SOLDATS 
CREATE TYPE divisio_tip AS TABLE OF soldat_tip;
/

--CREAR L'EXERCIT QUE CONTÉ DIVISIÓ
CREATE OR REPLACE TYPE exercit_tip AS OBJECT (
id VARCHAR2(10),
pais VARCHAR(15),
tipus_exercit VARCHAR2(10),
divisio divisio_tip,
MEMBER FUNCTION getCapita RETURN soldat_tip);
/
CREATE OR REPLACE TYPE BODY exercit_tip AS
MEMBER FUNCTION getCapita RETURN soldat_tip IS
BEGIN
   FOR i in 1..SELF.divisio.COUNT LOOP  
         IF (divisio(i).rang = 'capita')
           THEN
             RETURN SELF.divisio(i);
         END IF;
      END LOOP;  
 END;
END;


--CREAR TAULA EXERCITS AMB LA NESTED TABLE DIVISIÓ
CREATE TABLE exercits OF exercit_tip
NESTED TABLE divisio STORE AS divisio_nt;
/

```
**DML** inserció de dades i col·leccions

```SQL
--INSERIR EXERCITS A LA TAULA  JUNTAMENT AMB DIVISIONS I SOLDATS 
INSERT INTO exercits
VALUES(
exercit_tip('usaaire', 'usa', 'aire',
	divisio_tip(soldat_tip('002', 'John Price', 'capita'), 
	    	    soldat_tip('003', 'John Soap', 'general'),
		    soldat_tip('004', 'Adam Sandler', 'sniper'),
		    soldat_tip('006', 'Derek Westbrook', 'camper'))));


INSERT INTO exercits
VALUES(exercit_tip('rusiaterra', 'rusia', 'terra',
divisio_tip(soldat_tip('004', 'Alena Vorshevsky', 'capita'), 
	    soldat_tip('010', 'Andrei Harkov', 'general'),
	    soldat_tip('014', 'Vladimir Makarov', 'tinent'),
	    soldat_tip('A34', 'Imram Zakhaev', 'soldat ras'))));
```


**DML** execució del mètode de l'objecte:

```SQL
--EXECUTAR EL MÈTODE CREAT
DECLARE
exercit exercit_tip;
capita soldat_tip;
BEGIN
  SELECT deref(ref(e)) INTO exercit FROM exercits e WHERE e.id = 'usaaire';
  capita := exercit.getCapita();
  DBMS_OUTPUT.PUT_LINE(capita.nom);
END;
```

**Exercicis**

Executa aquestes sentències al teu entorn Oracle tot comprovant i entenent els resultats.

*By D.Llop & B.Ahmed & A.Rey (DAW'2014)*



---

#FpInfor #Daw #DawMp02 #DawMp02Uf04

* Resultats d'aprenentatge 1.B 1.C 1.E 1.F 1.G
* Continguts 1.1 1.3 1.4 1.7 1.10
---

###### Autor: daniel herrera 2014.04.11 14:05:14
###### Editat per: daniel herrera 2014.04.11 15:38:19
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
