# Transaccions - Videos visualitzats
## DAW-MP02-UF2 - Exercici de Llenguatges SQL: DML i DDL
Es vol fer en una transacció dues operacions, primer
mirar els usuaris que han visualitzat menys de 100 minuts de vídeo en el mes en curs
i posar-los en una taula, després fer un tractament amb aquestes dades i finalment
finalitzar la transacció. Quin tipus de nivell d'isolació hem de fer servir si volem
garantir que durant la transacció cap usuari passarà dels 100 minuts de vídeo ? Com
pot afectar això als usuaris que estan mirant vídeos? Argumenta les respostes.


    
    Usuaris ( email (pk), nom, data_alta )
    Videos ( id (pk), titol, minuts )
    Visualitzacions ( usuari_mail (pk, fk1 a Usuaris),
                      video_id (pk, fk2 a Videos, 
                      visualitzat_fins_al_minut )


**SQL d'ajuda**

```sql
create table Usuaris 
( email varchar(200) not null, 
  nom varchar(200) not null, 
  data_alta date not null,
  constraint usuaris_pk
  primary key (email) );

create table Videos 
( id int not null, 
  titol varchar(300) not null, 
  minuts int not null,
  constraint videos_pk
    primary key (id) );

create table Visualitzacions 
( usuari_mail varchar(200) not null,
  video_id int not null, 
  visualitzat_fins_al_minut int not null,
constraint visualitzacions_pk
  primary key (usuari_mail, video_id),
constraint visualitzacions_a_usuari
  foreign key (usuari_mail)
  references usuaris (email),
constraint visualitzacions_a_video
  foreign key (video_id)
  references videos ( id )
);

insert into videos values 
( 1, 'entenent transaccions', 10 ),
( 2, 'Fornite nivell 1', 40 );
insert into usuaris values 
( 'dherrera@macmecmic.cat', 'dani herrera', GETDATE() ),
( 'jrubio@macmecmic.cat', 'juaky rubio', GETDATE() );

insert into visualitzacions values 
(  'dherrera@macmecmic.cat', 2, 15 );
insert into visualitzacions values
( 'jrubio@macmecmic.cat', 1, 1 ),
( 'jrubio@macmecmic.cat', 2, 15 );

create table resum_mensual (
email varchar(200),
nom varchar(200),
minuts_visualitzats int,
mes_De_lestudi int,
constraint resum_mensual_pk
primary key (email, mes_De_lestudi )
)

begin transaction;
set transaction isolation 
level repeatable read;
insert into resum_mensual 
	select u.email, u.nom, 
	       SUM(v.visualitzat_fins_al_minut) as minuts_visualitzats,
		   4 as mes_De_lestudi
	from usuaris u
	inner join visualitzacions v
	  on u.email = v.usuari_mail
	group by u.email, u.nom
	having SUM(v.visualitzat_fins_al_minut) > 15

select SUM(minuts_visualitzats) from resum_mensual;

commit;

begin transaction;

insert into visualitzacions values 
(  'dherrera@macmecmic.cat', 1, 0 );

commit;
```

---

#FpInfor #Daw #Dam #Asix #AsixMp02 #DawMp02 #DamMp02 #DawMp02Uf02 #AsixMp02Uf02 #DamMp02Uf02

---

###### Autor: daniel herrera 2018.03.01 18:47:39
###### Editat per: daniel herrera 2018.03.02 14:34:41
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
