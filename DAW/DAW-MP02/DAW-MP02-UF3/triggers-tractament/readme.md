# Triggers. Tractament.
## DAW-MP02-UF3 - Exercici de Llenguatges SQL: DCL i extensió procedimental
Un hospital subministra tractament a diferents pacients. 

Exemple: el **pacient** Pere entra a l'hospital per un **cas** de grip cefalopiede i li preescriuen dos **tractaments**: 40grams de fitipilipoides andines (màxim 4 grams diàris) i 20grans de maxilopitifusions meleindrosos (màxim 2 grams diàris ). El primer dia la **dosi** és de 3 grams ( un al matí, un al migdia i un a la tarda ) del primer **medicament**. I dos grams del segon medicament ( que els pren de cop al vespre ). L'endamà l'intenten donar 20 grams de fifipilipodes amb el cafè amb llet, per sort el sistema ho impideix.

L'estructura de dades és aquesta:

* `Pacient`: codi (pk), nom
* `Cas`: codi (pk), pacient (fk), descripció
* `Medicament`: codi (pk), nom, quantitat_max_diaria_a_subministrar
* `Tractament_a_cas_de_pacient`: codi (pk), cas (fk1), medicament (fk2),  quantitat_total_a_subministrar,  quantitat_total_subministrada (default 0).
* `Dosi`: Tractament_a_cas_de_pacient (pk, fk1), dia_i_hora (pk), quantitat.

**Exercici**

* Fes el MCD per entendre millor l'estructura de dades.
* Fes els create tables.
* Fes un trigger que mantingui la quantitat_total_subministrada 
* Fes que el trigger comprovi que a un pacient mai se li subministra medicament per sobre de la quantitat_max_diaria_a_subministrar.
* Fes que el trigger comprovi que a un pacient mai se li subministra medicament per sobre de la quantitat_total_a_subministrar.
* Inserta les dades de l'exemple.


**DDL de les taules**

```sql
create table pacients (
   codi int identity not null,
   nom varchar(200) not null,
   constraint pacient_pk 
   primary key ( codi )
   );

insert into pacients values 
( 'dani' ),
( 'carles');

create table casos (
   codi int identity not null,
   pacient int not null,
   descripcio varchar(200) not null,   
   constraint casos_pk
   primary key ( codi ),
   constraint casos_a_pacients
   foreign key ( pacient )
   references pacients (codi) );

insert into casos values
( 1, 'Té molta gana' ),
( 2, 'Menja molt poc' );

create table medicaments (
   codi int identity not null,
   nom varchar(200) not null, 
   quantitat_max_diaria_a_subministrar int not null,
   constraint medicatments_pk
   primary key (codi )
)

insert into medicaments values
( 'Patates amb xoriço', 2 ),
( 'Bledes bullides', 5 );


create table tractament_a_cas_de_pacient (
     codi int identity not null,
     cas int not null,
	 medicament int not null,
	 qtat_total_a_subministrar int not null,
	 qtat_total_subministrada int not null default (0),
	 constraint tractament_a_cas_de_pacient_pk
	 primary key ( codi ),
	 constraint tractament_a_Cas_de_pacient_a_casc_fk
	 foreign key ( cas )
	 references casos (codi),
	 constraint tractament_a_Cas_de_pacient_a_medicament_fk
	 foreign key ( medicament )
	 references medicaments (codi));

insert into tractament_a_cas_de_pacient  values
( 1, 2, 20, 0 )

insert into tractament_a_cas_de_pacient  values
( 2, 1, 200, 0 )


create table dosis (
     tractament_a_cas_de_pacient int not null,
	 dia_i_hora datetime not null,
	 qtat int not null,
	 constraint dosis_pk
	 primary key ( tractament_a_cas_de_pacient, dia_i_hora),
	 constraint dosis_a_tractament_a_cas_de_pacient_fk
	 foreign key ( tractament_a_cas_de_pacient )
	 references tractament_a_cas_de_pacient (codi ));



/*

Fes un trigger que mantingui la quantitat_total_subministrada

Fes que el trigger comprovi que a un pacient mai se li subministra 
medicament per sobre de la quantitat_max_diaria_a_subministrar.

Fes que el trigger comprovi que a un pacient mai se li subministra
 medicament per sobre de la quantitat_total_a_subministrar.
Inserta les dades de l'exemple.

*/

alter trigger keep_dosi on dosis after insert as
begin
   -- actualitzar dades
   update t
   set qtat_total_subministrada = qtat_total_subministrada + qtat
   from tractament_a_cas_de_pacient t
   inner join (
       select tractament_a_cas_de_pacient codi, sum(qtat) as qtat
	   from inserted 
	   group by tractament_a_cas_de_pacient
   ) i
   on t.codi = i.codi
 
   --comprovació per màxim diari
   if exists( 
       select *
	   from dosis d 
	   group by cast( d.dia_i_hora as date ), d.tractament_a_cas_de_pacient
	   having sum( qtat ) >
	       (  select m.quantitat_max_diaria_a_subministrar
		      from medicaments m
			  inner join tractament_a_cas_de_pacient t
			  on t.medicament = m.codi
			  where t.codi = d.tractament_a_cas_de_pacient )
   ) begin
		raiserror( 'Massa dosi per un sol dia' , 16, 1 );
        rollback
   end

   --comprovació del total
   if exists( 
        select *
		from tractament_a_cas_de_pacient
		where qtat_total_subministrada > qtat_total_a_subministrar
   ) begin
		raiserror( 'Massa dosi total' , 16, 1 );
        rollback
   end
end

insert into dosis values
( 1, '2017-05-08 08:00:00', 1 ),
( 1, '2017-05-08 10:00:00', 2 ),
( 1, '2017-05-08 12:00:00', 1 ),
( 2, '2017-05-08 11:00:00', 1 );
```

---

#FpInfor #Daw #Dam #Asix #AsixMp02 #DawMp02 #DamMp02 #DamMp02Uf03 #DawMp02Uf03 #AsixMp02Uf03

---

###### Autor: daniel herrera 2017.04.25 14:28:51
###### Editat per: daniel herrera 2017.05.08 18:35:02
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
