# Oracle Objecte-Relacional - Herència i Col·leccions - Agar.io 
## DAW-MP02-UF4 - Exercici de Bases de dades objectes-relacionals
Es tracta d'ampliar l'exercici [Oracle Objecte-Relacional - Herència - Agar.io](/DAW/DAW-MP02/DAW-MP02-UF4/oracle-objecte-relacional-herencia-agario/readme.md) per tal de treballar amb col·leccions de cèl·lules.

Cal declarar un nou tipus `cellules_colleccio` que serà una col·lecció cèl·lules.

Cal crear una taula `partides` que tindrà dos camps, un anomenat `codi` de tipus char(5) amb el codi de la partida i un altre anomenat `cellules` de tipus `cellules_colleccio` amb les cèl·lules de la partida.

* Inserta 3 partides.
* Actualitza la massa d'algun jugador.
* Selecciona el codi de partida, la massa i el nom de la cèl·lula més grossa.

**Solució  ( by Sergio Rovira 2016' )**



```sql
--crear tipus col·lecció, consultar tipus celula_typ a la pràctica anterior
CREATE TYPE celules_typ AS TABLE OF celula_typ;

--crear taula de partides. Taula relacional amb una columna tipus objecte 
CREATE TABLE partides (
  codi_partida VARCHAR2(5),
  coleccio celules_typ
) NESTED TABLE coleccio STORE AS coleccio_nt;

--insertar una partida
INSERT INTO partides VALUES (
  '00001', 
  celules_typ(
      jugador_typ(100, posicio_typ(23,45), 'Sergio', '#ffffff'), 
      jugador_typ(4000, posicio_typ(600,35), 'Pepe', '#243546')
  )
);

--insertar un virus en una partida ja creada
INSERT 
  INTO 
    TABLE(SELECT t.coleccio FROM partides t WHERE t.codi_partida = '00001') 
  VALUES (
    virus_typ(150, posicio_typ(500,500)
    )
);

--actualitzar la massa d'un jugador en una partida ja creada
DECLARE
  celula celula_typ;
  m integer;
BEGIN

  --seleccionar un jugador
  SELECT 
    treat( value(s) as jugador_typ) into celula   
  FROM 
    TABLE(SELECT t.coleccio FROM partides t WHERE t.codi_partida = '00001') S 
  WHERE 
    S.massa = 4000;

  --incrementar la massa cridant el mètode corresponent
  celula.incrementa_massa(50);

  --actualitzar la massa del jugador a la taula
  UPDATE 
    TABLE(SELECT t.coleccio FROM partides t WHERE t.codi_partida = '00001') S 
  SET 
    S.massa = celula.massa
  WHERE 
    S.massa = 4000;
  
  COMMIT;
END;

```

---

#FpInfor #Daw #DawMp02 #DawMp02Uf04

---

###### Autor: daniel herrera 2016.04.20 16:26:10
###### Editat per: daniel herrera 2016.04.22 09:50:20
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
