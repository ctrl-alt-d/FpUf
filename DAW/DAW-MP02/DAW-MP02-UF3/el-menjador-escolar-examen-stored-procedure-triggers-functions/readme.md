# El menjador escolar - Examen - Stored Procedure - Triggers - Functions
## DAW-MP02-UF3 - Exercici de Llenguatges SQL: DCL i extensió procedimental
## El menjador escolar - Examen
### Stored Procedure - Triggers - Functions

Un menjador escolar té a la base de dades quants de nens hi ha apuntats cada dia i quin menú es servirà:

* `torns` ( `dia` pk, `num_nens_apuntats`, `nom_menú` )
* `ingredients` ( `id_ingredient` pk, `nom`, `calories` )

Entre les taules `torns` i `ingredients` hi ha una relació `N:M` amb atribut `quantitat`. 

Exemple, el dia 11 de maig hi ha 'bacallà amb tomata'. Els ingredients són 300 de bacallà i 100 de tomàta. El bacallà té 1 caloria i la tomata 0.5. Total calories = 300 * 1 + 100 * 0.5 = 350 calories.

1. **Funcions** Escriu la funció `total_calories`. Rep per paràmetre un `dia` i retorna quantes calories té el menú aquell dia ( cal multiplicar `quantitat` per `calories` de tots els ingredients del menú d'aquell dia )

2. **Procediments emmagatzemats** Escriu un procediment emmagatzemant `afegeix ingredient a torn`. Rep tres paràmetres: `id_ingredient`, `quantitat` i `dia`. **Important** No permet fer menús de més de 2000 calories.

3. **Triggers** Afegeix el camp `total_calories` a `torns`. Crea un trigger de manera que sempre que hi hagi canvis d'ingredients en un menú es recalculi aquest camp de la taula `torns`.

4. Argumenta dues avantatges i un inconvenient de posar el codi de programació a la base de dades vs posar-lo en el programa que consulta la base de dades.

**Solució**


```sql
use menjador;

drop table if EXISTS ingredients_torn;
drop table if EXISTS torns;
drop table if EXISTS ingredients;

create table torns 
( dia date not null primary key, 
num_nens_apuntats int not null default 0, 
nom_menú varchar(100) default '' );

create table ingredients ( 
id_ingredient int IDENTITY PRIMARY KEY, 
nom varchar(200) not null UNIQUE, 
calories int );

create TABLE ingredients_torn 
( dia date not null  references torns, 
  id_ingredient int not null references ingredients,
  quantitat int not null,
  constraint ingredients_torn_pk
  PRIMARY KEY (dia, id_ingredient));
/* --- */

INSERT INTO torns  values 
('2018-05-14',100, 'Macarrons');
INSERT INTO torns (dia, num_nens_apuntats, nom_menú) 
values ('2018-05-15',100, 'Verdureta');


INSERT INTO ingredients values 
('pasta macarrons', 100 ), --1
('tomata', 100 );          --2

INSERT INTO ingredients values 
('sucre', 400 ); --3

INSERT INTO ingredients values 
('carrota', 50 ); --4


INSERT INTO ingredients_torn values
( '2018-05-14', 1, 10), -- 1000 calories
( '2018-05-14', 2, 5);  -- +500 calories

/* Exercici num 1 TOTAL CALORIE */

CREATE FUNCTION dbo.total_calories( @dia as DATE ) 
RETURNS int AS
BEGIN
	return ( select sum( i.calories * it.quantitat )
	           from ingredients_torn it 
	         inner join ingredients i
	           on it.id_ingredient = i.id_ingredient
	         where it.dia = @dia)   

END




/* segon exercici - afegeix ingredient a torn */
drop procedure if exists afegeix_ingredient_a_torn;
CREATE PROCEDURE afegeix_ingredient_a_torn
    @id_ingredient as int, 
    @quantitat as int,
    @dia  as date AS
BEGIN
    DECLARE @total_calories int;
	SET TRANSACTION ISOLATION level SERIALIZABLE;
	BEGIN TRANSACTION;
    SELECT @total_calories = dbo.total_calories(@dia);

    SELECT @total_calories = 
                COALESCE(@total_calories,0)  +
                calories*@quantitat
    from ingredients
    where id_ingredient=@id_ingredient;

    IF (@total_calories < 2000 ) BEGIN
	    INSERT INTO ingredients_torn values
       ( @dia, @id_ingredient, @quantitat);	
       	COMMIT;
	END ELSE BEGIN
	    COMMIT;  -- podem fer commit perquè no hem tocat res
        RAISERROR( 50005, 10, 1, 'Massa calories' );
    END;
END;

/* provem */
delete from ingredients_torn where id_ingredient = 4;
select dbo.total_calories( '2018-05-14')
exec afegeix_ingredient_a_torn 4, 100, '2018-05-14';
exec afegeix_ingredient_a_torn 4, 10, '2018-05-14';

/* Trigger */
ALTER TABLE torns ADD total_calories int;
exec afegeix_ingredient_a_torn 4, 10, '2018-05-15';
select * from torns;

UPDATE torns
SET total_calories = dbo.total_calories(dia)

CREATE TRIGGER recalcula_calories on ingredients_torn
AFTER INSERT, DELETE, UPDATE AS
BEGIN
	UPDATE torns
    SET total_calories = dbo.total_calories(dia)
    where dia IN
    ( select dia from inserted
      UNION
      select dia from deleted
    )
END

/* Proves */
delete from ingredients_torn where id_ingredient = 1;
exec afegeix_ingredient_a_torn 1, 1, '2018-05-15';
select * from torns;
```

---

#FpInfor #Daw #Dam #Asix #AsixMp02 #DawMp02 #DamMp02 #DamMp02Uf03 #DawMp02Uf03 #AsixMp02Uf03

---

###### Autor: daniel herrera 2018.05.11 11:09:04
###### Editat per: daniel herrera 2018.05.14 17:31:23
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
