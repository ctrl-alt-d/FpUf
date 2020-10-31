# El nen que no es va poder menjar una Kangreburguer perquè no quedava amor
## DAW-MP02-UF3 - Exercici de Llenguatges SQL: DCL i extensió procedimental
### Primera part

**Efecte desitjat**: Estem preparant una comanda de 2 CocaLoques i 2 Kangreburguer però en posar la segona Kangreburguer el sistema ens avisa que no es pot fer la comanda perquè s'ha acabat l'ingredient secret de la Kangreburguer, l'amor.

Aquesta pràctica la farem usant TDD: Prepararem un joc de proves reproduïble per tal de comprovar que funciona correctament el nostre codi.

Entregables: 

* Cal fer l'stored procedure `Afegir ítem a comanda`. 
* Joc de proves i captures de pantalla.

Taules que tenim actualment:

* Productes: Id, nom
* Components: Id, nom, calories, unitats expressades en (ens indica en què estan expressades les unitats: grams, quilos, unitats, ... )
* Composicions: Id_producte, Id_component, qtat
* Variacions Stock: Id, data_hora, Id_component, qtat, motiu (ex: reposició, venda )
* Estats Comanda: Id, nom ( nova, marxant, servida )
* Comandes: Id, num_tarja_fidelitat, data_hora, Id estat
* Línies de comanda: Id comanda (pk), Id Producte (pk), qtat

Exemple:

* La Kangreburguer es compon de:
    * Llonguet ( 1 unitat )
    * Enciam ( 200 grams )
    * Carn picada ( 220 grams )
    * Amor ( 10 unitats )
* La ColaLoca es composa de:
    * ColaLoca ( 220 mml )

Regles de negoci:

* L'estoc va variant quan posem productes a les comandes (l'stored procedure se n'encarrega).
* Si afegim producte a la comanda i no queda stock ha de saltar un error.
* Si afegim a una comanda un producte que ja hi és no es crea una nova línia sinó que s'incrementa la `qtat`

Regles per a programar-ho:

* Cal plantejar la pràctica amb metodologia TDD.
* Tot ha de ser repetible ( fent copy-paste és suficient però millor mitjançant un script )
* Cal trencar el codi en unitats petites, per exemple cal crear una funció que donat un component ens digui quant en queda, la funció que donat un producte i una quantitat ens digui si el podem servir.
* Cada unitat s'ha de provar que funciona, ha de tenir els seus testos.
* Val (cal) inserir dades de prova a les taules mitjançant inserts.
* Només es poden afegir línies d'ordres a les comandes en estat 'nova'.
* Totes les instruccions han d'estar comentades. Feu servir `GO` entre instruccions per anar executant talls de codi. 

Exemple:

    
    --inserim Productes de prova
    Insert into Productes values ( .... )
    ...
    GO
    
    --Insertem components de prova
    Insert into Components values (... )
    ...
    GO
    
    --inserim Stock
    Insert into VariacionsStock values ( ... )
    ...
    GO
    
    --Creem funció que ens diu l'stock d'un producte
    create funcion ....
    GO
    
    --Provem la funció amb les dades actuals;
    declare @stock_producte_enciam as integer;
    set @stock_producte_enciam = select sum(....
    If (@stock_producte_enciam <> 1200 ) raiserror ( ...
    GO
    
    --Etc
    
**IMPORTANT** La metodologia d'aquesta pràctica és TDD. Sempre abans de picar cap línia de codi has de tenir un joc de proves dissenyat.

### Segona part

Fes l'stored `cancel·la comanda`:

* Si la comanda està en estat 'Nova', a més d'esborrar la comanda, retorna stock (insertar variacions d'estoc positives amb motiu 'anul·lació de comanda').
* Si la comanda està en estat marxant (l'estan cuinant) no retornarà stock però s'esborrarà la comanda.
* Si la comanda està en estat servida donarà un error, no es poden cancel·lar.

Aquesta segona part també cal fer-la amb metodologia TDD.


** Solució primera part **

    
```sql
--Esborro les taules si existeixen
DROP TABLE IF EXISTS LiniesDeComandes;
DROP TABLE IF EXISTS Comandes;
DROP TABLE IF EXISTS EstatsComanda;
DROP TABLE IF EXISTS VariacionsEstoc;
DROP TABLE IF EXISTS Composicio;
DROP TABLE IF EXISTS Components;
DROP TABLE IF EXISTS Productes;
drop function if EXISTS getEstoc;
drop PROCEDURE if EXISTS afegir_item_a_la_comanda;
--DDL: Creació de taules
CREATE TABLE Productes (
	id int NOT NULL IDENTITY(1,1),
	nom varchar(200),
	CONSTRAINT producte_pk PRIMARY KEY (id)
)

CREATE TABLE Components (
	id int NOT NULL IDENTITY(1,1),
	nom varchar(200),
	calories int,
	unitats_expressades_en varchar(100),
	CONSTRAINT component_pk PRIMARY KEY (id)
) 

CREATE TABLE Composicio (
	id_producte int NOT NULL,
	id_component int NOT NULL,
	quantitat int NOT NULL,
	CONSTRAINT composicio_pk PRIMARY KEY (id_producte,id_component),
	CONSTRAINT composicio_a_component_fk FOREIGN KEY (id_component) REFERENCES Components(id) ,
	CONSTRAINT composicio_a_producte_fk FOREIGN KEY (id_producte) REFERENCES productes(id) 
           
)

CREATE TABLE VariacionsEstoc (
	id int NOT NULL IDENTITY(1,1),
	data_i_hora datetime DEFAULT (getdate()) NOT NULL,
	id_component int NOT NULL,
	quantitat int NOT NULL,
	motiu varchar(100) DEFAULT ('') NOT NULL,
	CONSTRAINT variacioestoc_pk PRIMARY KEY (id),
	CONSTRAINT variacioestoc_a_component_fk FOREIGN KEY (id_component) REFERENCES Components(id) 
) 

CREATE TABLE EstatsComanda (
	id char(1) NOT NULL,
	nom varchar(100),
	CONSTRAINT estatcomanda_pk PRIMARY KEY (id)
) 

CREATE TABLE Comandes (
	id int NOT NULL IDENTITY(1,1),
	num_tarja_fidelitat varchar(100),
	data_hora datetime DEFAULT (getdate()) NOT NULL,
	id_estat char(1) DEFAULT ('N') NOT NULL,
	CONSTRAINT comanda_pk PRIMARY KEY (id),
	CONSTRAINT comanda_a_estat_comanda_fk FOREIGN KEY (id_estat) REFERENCES EstatsComanda(id) 
);

CREATE TABLE LiniesDeComandes (
  id_comanda int not null,
  id_producte int not null,
  quantitat int,
  CONSTRAINT liniadecomanda_pk
     PRIMARY KEY ( id_comanda, id_producte ) ,
  CONSTRAINT liniadecomanda_a_comanda_fk
     FOREIGN KEY (id_comanda)
     REFERENCES Comandes (id),
  constraint liniadecomanda_a_producte_fk
     foreign key (id_producte)
     references productes ( id )
   );

--DML: Inserció de dades de proves
insert into productes (nom) 
values 
 ('Kangreburguer'),
 ('KolaLoka'),
 ('Fluxiplus');

insert into Components values 
('Llonguet',20,'unitats'),
('Enciam',7,'grams'),
('Carn Picada',100,'grams'),
('Amor',1000,'tones'),
('KolaLoka',2000,'mililitres'),
('Nata',1500,'grams');

Insert into Composicio 
(id_producte,id_component,quantitat )
VALUES
(1,1,1 ),
(1,2,200),
(1,3,220),
(1,4,10),
(2,5,220),
(3,6,300),
(3,4,9);

insert into variacionsEstoc
(id_component,quantitat,motiu ) 
VALUES
(1,6,'Compra (reposició)'), --Llonguet
(2,200*6,'Compra (reposició)'), --Enciam
(3,220*6,'Compra (reposició)'), --Carn Picada
(4,1000*1.5,'Compra (reposició)'), --Amor
(5,5000,'Compra (reposició)'), --KolaLoka
(6,5000,'Compra (reposició)'), --Nata
(6,5000,'Compra (reposició)'); --Nata

-----------------------------
GO
create function getEstoc(
   @id_component int
) RETURNS int as BEGIN
	declare @estoc int;
    set @estoc = (select sum(quantitat)
                  from variacionsEstoc
                  where id_component = @id_component)
    return coalesce(@estoc, 0);              
END;

--TDD---------------------------
GO
BEGIN
	declare @comprova_funcio_estoc int;
	set @comprova_funcio_estoc = (select dbo.getEstoc( 6 ) );
	if @comprova_funcio_estoc <> 10000 begin 
	   raiserror( 'La funció calcula estoc no funciona bé',
	              10,1 );
	end;
end;

---------------------------------

Insert into estatsComanda
VALUES
('N','Nova'),
('M','Marxant'),
('S','Servida');

Insert into comandes (
num_tarja_fidelitat) 
values 
('11111'),
('22222');

GO
CREATE PROCEDURE afegir_item_a_la_comanda 
    @id_producte INT,
    @id_comanda INT
AS BEGIN
	
   -- Iniciar transacció
   set transaction isolation level serializable;
   BEGIN TRAN T1;
   print 'inicio tx';

   --Comprovo que la comanda està en estat Nova
   DECLARE @estat char;
   set @estat = (select id_estat 
                 from Comandes
                 where id = @id_comanda );
   IF @estat != 'N' BEGIN
	   
	   print 'rollback tx';
	   ROLLBACK TRAN T1; 
	   RAISERROR ('No es pot modificar aquesta comanda',10,1);
       RETURN
   END;

   -- Insertar variacions estoc
   print 'la comanda està en estat N';
   print 'Inserto variacions estoc';
   INSERT into variacionsEstoc 
	(id_component, quantitat,motiu)
	select id_component, -1.0 * quantitat, 'Venta'
	from composicio 
	where id_producte = @id_producte
	
   -- Comprovar que no hi ha rotura d'estoc
   declare @num_ruptures_estoc int;
   set @num_ruptures_estoc = (
          select count(*)
          from components c
          where dbo.getEstoc(c.id) < 0
       );
   if @num_ruptures_estoc>0 BEGIN
	  print 'rollback tx hi ha ruptura d''estoc';
      ROLLBACK  TRAN T1;
      RAISERROR( 'No es pot fer comanda perque no queda estoc', 10, 1);
      RETURN
   END 

   -- Upsert de línia de comanda
   print 'Hi ha prou estoc mirem si cal fer upsert';
   declare @n int;
   set @n = (
        select count(*)
        from liniesDeComandes
        where id_producte = @id_producte AND
              id_comanda = @id_comanda);
   if ( @n > 0 )
   BEGIN
	   print 'El producte apareix a la comanda: Cal fer update';
	   UPDATE liniesDeComandes
	   set quantitat = quantitat +1 
	   where id_producte = @id_producte AND
              id_comanda = @id_comanda;
   END ELSE begin 
	   print 'El producte no apareix a la comanda: fem insert';
	   INSERT into liniesDeComandes 
	        (id_comanda, id_producte, quantitat)
	        VALUES
	        (@id_comanda, @id_producte, 1);
   END;
   print 'commit tx';

   --finalitzem amb commit
   COMMIT TRAN T1; 

END;

--------

EXEC dbo.afegir_item_a_la_comanda 1, 1;
EXEC dbo.afegir_item_a_la_comanda 1, 1;

--Comprovar que només quede 4 llonguets:
--TDD---------------------------
BEGIN
	declare @comprova_funcio_estoc int;
	set @comprova_funcio_estoc = (select dbo.getEstoc( 1 ) );
	if @comprova_funcio_estoc <> 4 begin 
	   raiserror( 'El procediment no ha funcionat bé',
	              10,1 );
	end;
end;
```

---

#FpInfor #Daw #Dam #Asix #AsixMp02 #DawMp02 #DamMp02 #DamMp02Uf03 #DawMp02Uf03 #AsixMp02Uf03

---

###### Autor: daniel herrera 2018.03.31 15:01:08
###### Editat per: daniel herrera 2018.04.13 15:21:56
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
