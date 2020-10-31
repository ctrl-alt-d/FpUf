# Gestió d'entrades per al teatre
## DAW-MP02-UF2 - Exercici de Llenguatges SQL: DML i DDL
###Univers de discurs###

Un teatre organitza `representacions`. Cada representació és d'una `obra`. Les obres d'identifiquen pel títol de l'obra més l'autor i les representacions a través de l'obra més la data i hora de representació.

Per a cada representació es decideix quantes `entrades` es posen a la venda i s'anota a la base de dades. Les entrades són nominals, de manera que cada entrada s'identifica pel nom de la persona que la compra més la representació a la que dona accés aquesta entrada.

###Primera part###

Fes el MCD de dades d'aquest univers de discurs més els create tables.

**Les claus surrogades**

Treballar amb [claus naturals](https://en.wikipedia.org/wiki/Natural_key) té l'inconvenient que la propagació de claus es fa molt feixuga. És una pràctica comú desnormalitzar el model i usar [claus surrugades](https://en.wikipedia.org/wiki/Surrogate_key). 

Esborra les taules i torna a fer els create tables ara amb claus surrogades. 

**Inserció de dades**

Inserta les següents obres:

* `Seny i amor, amo i senyor` d' `Avel·lí Artís i Balaguer,`
* `La Senyora Florentina i el seu amor Homer` de `Mercè Rodoreda`
* `Sogra i nora` de `Josep Pin i Soler`

Inserta les següents representacions:

* `Seny i amor, amo i senyor` el dia 30 de novembre de 2017 a les 18:00 i a les 20:00. 5 entrades disponibles per a cada representació.
* `La Senyora Florentina i el seu amor Homer` el dia 3 de desembre de 2017 a les 18:00 i a les 20:00. 2 entrades disponibles per a cada representació.

### Segona part###

**Transaccions**

La transacció per a vendre una entrada és la següent:

1. Iniciar la transacció
2. Comprovar el número d'entrades venudes per aquella representació ( fent un recompte de les entrades venudes )
3. Si el número d'entrades venudes és inferior a l'aforament per aquella representació es fa la inserció a la taula d' `entrades` amb el nom del comprador.

Ven una entrada de la primera representació de `Seny i amor, amo i senyor` a la `Maria`.

**Isolació**

Es pot donar el cas que dues transaccions s'iniciin a la vegades, totes dues llegeixin que hi ha 4 entrades venudes i que l'aforament és 5. Llavors totes dues transaccions intentaran vendre l'entrada que queda. Quin nivell d'Isolació ens cal en aquest escenari? Per què? Comprova-ho.

###Tercera part###

**Modificació sobre l'enunciat**

Ara, a més d'emmagatzemar l'aforament de la representació, també emmagatzemarem quantes entrades portem venudes.

Modifica les taules per tal d'afegir aquest camp:

`alter table representacions add entrades_venudes int default 0`

Actualitza com puguis la taula representacions per posar cuantes entrades hi ha venudes de cada representació.

**La nova transacció**

1. Iniciar la transacció
2. Comprovar el número d'entrades venudes per aquella representació ( consultant el nou camp )
3. Si el número d'entrades venudes és inferior a l'aforament per aquella representació es fa la inserció a la taula d' `entrades` amb el nom del comprador.
4. Incrementem el número d'entrades venudes.

**Isolació**

Explica quin nivell d'isolació necessitem per traballar en aquest escenari tot argumentant la teva resposta.



## Solucions##

* [Part 2](https://youtu.be/15d8BV7_lGo)
* [Part 3](https://youtu.be/kRRRTqCN8T4)

Part 1 i codi:

```sql
create table obres (
   titol varchar(200) not null,
   autor varchar(200) not null,
   constraint obres_pk
   primary key ( titol, autor )
);


--drop table representacions;
create table representacions (
    data date not null,
	hora int not null,
	minut int not null,
    titol varchar(200) not null,
    autor varchar(200) not null,
	numero_de_entrades_a_la_venda int not null,
	constraint representacions_pk
	primary key ( data, hora, minut,
	              titol, autor ),

    constraint representacions_a_obra_fk
	foreign key (titol, autor )
	references obres ( titol, autor )
);


create table entrades (
    nom_espectador varchar(300) not null,
    data date not null,
	hora int not null,
	minut int not null,
    titol varchar(200) not null,
    autor varchar(200) not null,
	constraint entrades_pk
	primary key ( nom_espectador, data,
	              hora, minut, titol, autor ),

    constraint entrades_a_respresentacio_fk
	foreign key ( data, hora, minut,
	              titol, autor )
	references representacions (data, hora, minut,
	              titol, autor )

)
```


**Solució amb claus surrogades**

```sql
drop table entrades;
drop table representacions;
drop table obres;

create table obres (
   id int identity not null,
   titol varchar(200) not null,
   autor varchar(200) not null,
   constraint obres_pk
   primary key ( id )
);

create table representacions (
    id int identity not null,
    data date not null,
	hora int not null,
	minut int not null,
    id_obra int not null,
	numero_de_entrades_a_la_venda int not null,
	constraint representacions_pk
	primary key ( id ),

    constraint representacions_a_obra_fk
	foreign key (id_obra )
	references obres ( id )
);

create table entrades (
    id int identity not null,
    nom_espectador varchar(300) not null,
	id_representacio int not null,
	constraint entrades_pk
	primary key ( id ),

    constraint entrades_a_respresentacio_fk
	foreign key ( id_representacio )
	references representacions ( id )
);
```


*Solució inserció de dades*

```sql
insert into obres
values ('Seny i amor, amo i senyor',
'Avel·lí Artís i Balaguer');

insert into obres
values ('La Senyora Florentina i el seu amor Homer',
'Mercè Rodoreda');



INSERT INTO [dbo].[representacions]
           ([data]
           ,[hora]
           ,[minut]
           ,[id_obra]
           ,[numero_de_entrades_a_la_venda])
     VALUES
           ('2017-11-30',18,0,1,5);

INSERT INTO [dbo].[representacions]
           ([data]
           ,[hora]
           ,[minut]
           ,[id_obra]
           ,[numero_de_entrades_a_la_venda])
     VALUES
           ('2017-11-30',20,0,1,5);

INSERT INTO [dbo].[representacions]
           ([data]
           ,[hora]
           ,[minut]
           ,[id_obra]
           ,[numero_de_entrades_a_la_venda])
     VALUES
           ('2017-12-03',18,0,2,2);

INSERT INTO [dbo].[representacions]
           ([data]
           ,[hora]
           ,[minut]
           ,[id_obra]
           ,[numero_de_entrades_a_la_venda])
     VALUES
           ('2017-12-03',20,0,2,2);

```


*Solució transaccions*

Aquest és el codi que hem fet servir per a provar la isolació. Cal obrir dues sessions diferents ( 2 MSSQLServerManagementStudio ) per tal d'emular la concurrència.

```sql
declare @representacio int 
set @representacio = 3;

declare @payo varchar(100);
set @payo = 'Gerard';

begin transaction;
set transaction isolation level serializable;

declare @num_entrades_venudes int;
select @num_entrades_venudes = count(*)
from entrades 
where id_representacio = @representacio

WAITFOR DELAY '00:00:05'   --donem temps a que l'altre
                           --transacció també faci el
                           --recompte d'entrades

declare @aforament int;
select @aforament = r.numero_de_entrades_a_la_venda
from representacions r 
where id=@representacio;

if (@aforament > @num_entrades_venudes) 
begin
  insert into entrades values ( @payo, @representacio); 
  commit;
end else begin
  --està tot ple:
  print 'està ple!'
  rollback;
end
```

---

#FpInfor #Daw #Dam #Asix #AsixMp02 #DawMp02 #DamMp02 #DawMp02Uf02 #AsixMp02Uf02 #DamMp02Uf02

---

###### Autor: daniel herrera 2017.01.24 17:16:21
###### Editat per: daniel herrera 2018.02.23 16:07:09
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
