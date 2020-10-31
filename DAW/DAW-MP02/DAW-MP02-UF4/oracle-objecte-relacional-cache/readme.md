# Oracle Objecte-Relacional - Cache 
## DAW-MP02-UF4 - Exercici de Bases de dades objectes-relacionals
**La cache d'artistes**

![Imgur](http://i.imgur.com/nmf9GFN.png)

Twin Peaks necessita una base de dades per triar els artistes de la propera temporada. Cal prepar-la.

1) Crea usuari i connexio a base de dades, otorga els permisos mínims ( connect i resource ). Connectat amb l'usuari que has creat.

2) (1 punt) Crea el tipus `persona` no final i no instanciable amb:

    nom VARCHAR2(500 )
    cache NUMERIC( 8,2)
    FUNCTION descripcio RETURN varchar2 --no cal fer body

3) (1 punt) Crea el tipus músic que hereti de persona. Sobreescriu la descripció per tal que retorni el nom i l'instrument que toca.

4.1) (0.5 punt) Crea el tipus pel·lícula:

    titol varchar2( 200 ),
    any_estrena int

Crea una `collecio_pelicules` tipus col·lecció taula.

4.2) (2 punt) Crea el tipus actor que hereti de persona. Afegeix-li el camp `pelicules`  de tipus `collecio_pelicules`. Sobreescriu la descripció per tal que retorni el nom i les pel·lícules on ha aparescut. Recorda que l'operador concatenació és ||

5)  (0.5 punt) Crea taula d'objectes persona. ( No li cal NESTED TABLE )

6) (1 punt) Inserta un actor i dos músics:

```bash
  'Trent Reznor', 1000, 'Cantant' 
  'Eddie Vedder', 2000, 'Guitarra'
  'Monica Anna Maria Bellucci', 3000, 
    ha aparescut a: 'The Matrix Reloaded', 2003
                    'The Passion of the Christ', 2004
```

recorda fer commit.

7) (1 punt ) Selecciona el nom i la descripció de totes les persones amb cache superior a 1500.

![Imgur](http://i.imgur.com/LJVYvNd.png)

**Entregables**

* Captura de pantalla de totes les instruccions que has realitzat.


**Solucio**


```sql
create user ex2016 identified by i 
default tablespace users
temporary tablespace temp;

GRANT connect, resource TO ex2016;

--- persona ---

CREATE TYPE persona AS OBJECT (
  nom VARCHAR2(500 ),
  cachete NUMERIC( 8,2),
  MEMBER FUNCTION descripcio RETURN varchar2
) NOT FINAL NOT INSTANTIABLE;

--- music ---

CREATE TYPE music UNDER persona  (
  instrument varchar2(500 ),
  OVERRIDING MEMBER FUNCTION descripcio RETURN varchar2
);

CREATE OR REPLACE TYPE BODY music AS 
OVERRIDING MEMBER FUNCTION descripcio RETURN VARCHAR2 IS
    aux_desc varchar(1000);
  BEGIN
    aux_desc := nom || ' toca el ' || instrument;
    return aux_desc;
  END;
END;

--- pelicules i actor ---

CREATE TYPE pelicula AS OBJECT (
  titol varchar2( 200 ),
  any_estrena int
);

CREATE TYPE collecio_pelicules AS TABLE OF pelicula;  


CREATE TYPE actor UNDER persona  (
  pelicules collecio_pelicules,
  OVERRIDING MEMBER FUNCTION descripcio RETURN varchar2
);

CREATE OR REPLACE TYPE BODY actor AS 
OVERRIDING MEMBER FUNCTION descripcio RETURN VARCHAR2 IS
    aux_pelis varchar(1000);
  BEGIN
    aux_pelis := '';
    FOR i IN 1..pelicules.COUNT LOOP
       aux_pelis := aux_pelis || pelicules(i).titol || ', ';
    END LOOP;
    return aux_pelis;
  END;
END;

--- taula persones ---

CREATE TABLE persones OF persona; -- sense nested table IDK why.

--- insertar un actor i dos músics

INSERT INTO persones VALUES (
   music( 'Trent Reznor', 1000, 'Cantant' )
);

INSERT INTO persones VALUES (
   music( 'Eddie Vedder', 2000, 'Guitarra' )
);

INSERT INTO persones VALUES (
   actor( 'Monica Anna Maria Bellucci',
          3000, 
          collecio_pelicules( 
              pelicula( 'The Matrix Reloaded', 2003 ),
              pelicula( 'The Passion of the Christ', 2004 )
          )
         )
);


COMMIT;

--- selecciona el nom i la descripció de totes les persones amb cachete superior a 1500.

select p.nom, p.descripcio() from persones p where p.cachete > 1500;














--- capitols i persones

CREATE TYPE aparicio AS OBJECT (
  ref_persona REF persona,
  sou NUMERIC(8,2)
);


CREATE TYPE colleccio_aparicions AS TABLE OF aparicio;

CREATE TABLE capitols (
   seasson int,
   episode int,
   title varchar2( 100 ),
   aparicions colleccio_aparicions
) NESTED TABLE aparicions STORE AS capitols_aparicions_nt;

--- insertar les persones del primer capítol.


DECLARE
   T ref persona;
   E ref persona;
   M ref persona;
begin
   select ref( p ) into T from persones p where p.nom like 'T%';
   select ref( p ) into E from persones p where p.nom like 'E%';
   select ref( p ) into M from persones p where p.nom like 'M%';
   INSERT INTO capitols VALUES (
       1,
       2,
      'IMPOSSIBLE',
      colleccio_aparicions( aparicio( T, 1000.2 ) , aparicio( M, 2000.1 ) )
    );  
end;



--- selecciona les perones del primer capítol que cobrin més de 1000









```




---

#FpInfor #Daw #DawMp02 #DawMp02Uf04

---

###### Autor: daniel herrera 2016.04.27 14:34:00
###### Editat per: daniel herrera 2016.04.29 16:22:31
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
