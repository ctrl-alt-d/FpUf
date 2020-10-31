# El Zoo. Funcions i procediments emmagatzemants
## DAW-MP02-UF3 - Exercici de Llenguatges SQL: DCL i extensió procedimental
Un zoo té catalogats els seus exemplars per espècies. Cada espècie té una dieta. Aquestes serien les relacions a la base de dades:

* `Espècies` ( codi (pk), nom (unique), continent_origen )
* `Animals` ( espècie (fk1), num_xip (pk), nom, dia_neixement, data_baixa (null) )
* `Aliments` ( nom (pk), preu )
* `Dietes` ( aliment (pk, fk1), espècie (pk, fk2), qtat_en_grams )

**Primera part**

Fes la funció `mitjana_edat` la qual, donada un codi d'espècie, retorna l'edat mitjana dels animals del zoo vius d'aquella espècie.

Fes el procediment emmagamatzemat `alta_animal` el qual, passant per paràmetre l'espècie, número de xip, el nom i la data de neixement dona d'alta un animal.

Crea un usuari anomenat `cuidador` amb un login anomenat `l_cuidador` i que sigui membership del rol db_datareader i a més d'un altre rol pugui executar el procediment emmagatzemat que has escrit.

**Segona part**

Afegim dues noves taules a la base de dades:

* `Ordre de compra` ( id (pk de tipus identity), data (unique) )
* `LíniaOrdreDeComra` ( aliment (pk, fk1), ordre (pk, fk2), qtat_en_grams )

Les ordres de compra són mensuals.

Cal una línia a l'ordre de compre per a cada aliment que cal comprar.

Es calcula la quantitat a comprar segons la dieta dels animals vius del zoo.

Cal calcular quants dies té el més perquè la dieta és diària i l'ordre de compre és mensual.

Crea un procediment emmagatzemat que donat un any i un mes creii l'ordre de compra per aquell mes.

==============================

**Solució 1ra part**


    
```sql
drop table animals;
drop table especies;

create table especies 
( codi int identity not null,
nom varchar(200) not null,
continent_origen varchar(200) not null,
constraint especies_pk primary key ( codi ),
constraint especies_uq1 unique ( nom ));

create table animals (
especie int not null,
num_xip int not null,
nom varchar(300) not null,
dia_neixement date not null,
data_baixa date null,
constraint animals_pk primary key ( num_xip ),
constraint animals_a_especie_fk foreign key (especie) references especies (codi));

insert into especies (nom, continent_origen) values
('impala','Africa' ),
('koala', 'Oceania'),
('canguro', 'Oceania'),
('cebra', 'Africa'),
('Tarantula', 'Africa' );

insert into animals values
(1, 1, '150cc', '2001-05-01', null),
(1, 2, '250cc', '2002-07-21', null),
(5, 3, 'Pelacuaia', '2012-07-2', null),
(5, 4, 'Pelacuaia', '2012-07-23', '2015-07-23');

create table aliments (
nom varchar(300) not null,
preu money not null,
constraint aliment_pk primary key (nom) ) ;
```

    insert into aliments values
    ( 'eucalipto', 0.20 ),
    ( 'mosquitos desidratados', 0.10 ),
    ( 'menta', 0.2 );
    
    insert into dietes values
    ( 'eucalipto', 2, 1200),
    ( 'menta', 2, 50),
    ( 'mosquitos desidratados', 5, 53 );
    
    create table dietes (
       aliment varchar(300) not null,
       especie int not null,
       qtat_en_grams float not null,
       constraint dietes_pk primary key (aliment, especie),
       constraint dietes_a_especie_fk foreign key (especie) references especies (codi),
       constraint dietes_a_aliments_fk foreign key (aliment) references aliments (nom)
    )

    create function mitjana_edat ( 
       @codi_especie int )
       returns float
    as begin
    
       declare @mitjana float;
       select @mitjana = avg( datediff(month,dia_neixement,getdate())/12.0 )
       from animals a
       where a.especie = @codi_especie
         and data_baixa is null;
       return @mitjana;
    end;

    --creem el procediment
    create procedure inserta_animal 
    @especie int,
    @xip int,
    @nom varchar(100),
    @dia_naixement date
    
    as begin
    
        insert into animals
        values(@especie,@xip,@nom,@dia_naixement,null)
    
    end
    
    --provem el procediment
    exec dbo.inserta_animal
    @especie = 4,
    @xip = 5,
    @nom = 'delfin',
    @dia_naixement ='2002-02-02';
    
    
    CREATE LOGIN l_cuidador WITH PASSWORD = '1234';
    
    CREATE USER cuidador FOR LOGIN l_cuidador;
    
    ALTER ROLE db_datareader ADD MEMBER cuidador;
    
    CREATE ROLE Rol_procedure;
    
    ALTER ROLE Rol_procedure ADD MEMBER cuidador;
    
    grant execute on [dbo].[inserta_animal] to Rol_procedure;


**Solució part 2**


    
```sql
create table ordre_de_compra (
   numero_de_ordre int identity not null,
   data date,
   constraint ordre_de_compra_pk
   primary key ( numero_de_ordre ),
   constraint ordre_de_comora_ak1
   unique ( data ) 
);

create table linia_ordre_de_compra (
   numero_de_ordre int not null,
   aliment varchar(300) not null,
   qtat_en_grams float  not null,
   constraint linia_ordre_de_compra_pk
   primary key ( numero_de_ordre, aliment),
   constraint linia_ordre_de_compra_a_alimnent_fk
   foreign key (aliment) 
   references aliments ( nom ),
   constraint linia_ordre_de_compra_a_odre_de_compra_fk
   foreign key (numero_de_ordre) 
   references ordre_de_compra ( numero_de_ordre )
   );
```

    select d.qtat_en_grams, d.aliment, e.codi
    from especies e 
    inner join animals a
       on e.codi = a.especie
    inner join dietes d
       on e.codi = d.especie
    where a.data_Baixa is null

---

#FpInfor #Daw #Dam #Asix #AsixMp02 #DawMp02 #DamMp02 #DamMp02Uf03 #DawMp02Uf03 #AsixMp02Uf03

---

###### Autor: daniel herrera 2017.03.29 13:47:03
###### Editat per: daniel herrera 2017.04.04 17:52:33
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
