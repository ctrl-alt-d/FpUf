# Valoració de películes: trigger, procediment emmagatzemat, cursor i funció.
## DAW-MP02-UF3 - Exercici de Llenguatges SQL: DCL i extensió procedimental
Crea aquestes taules a la teva base de dades:

```sql
create table pelicules  (
  id int identity not null,
  titol varchar(100) not null,
  n_comentaris_positius int default (0),
  constraint pelicula_pk 
  primary key ( id)
);

create table valoracions (
  id int identity not null,
  valoracio_del_0_al_5 int not null,
  pelicula_id int not null,
  constraint comentari_pk primary key ( id),
  constraint comentari_a_peli_fk
  foreign key ( pelicula_id )
  references pelicules ( id )
  );
```

Fes el procediment emmagatzemant `insertar_valoracio`: donat un codi de película i una valoració ha d'insertar la valoració a la taula valoracions. Si la valoració no és un número entre 0 i 5 s'ha de queixar. Si la valoració és un número entre 3 i 5 ha d'incrementar el número de `n_comentaris_positius` de la taula `pelicules`.

Esborra el procediment i programa aquesta funcionaliatat però mitjançant un trigger.

Fes ara un cursor que comprovi si l'agregat a la taula de películes coincideix amb les dades que hi ha a valoracions. Si no coincideix que ho arregli.

Per últim fes una funció que donat un `id_pelicula` retorni el número de valoracions positives.

**Solució procediment emmagatzemat**


    
```sql
alter procedure afegeix_valoracio
    @codi_pelicula int,
	@valoracio int
as begin
    -- control valoracio entre 0 i 5
	if (not @valoracio between 0 and 5)
	begin
	   raiserror( 'valoració erronea', 16,1);
	   rollback;
	end;

	--inserto a la taula de valoracions
	insert into valoracions ( valoracio_del_0_al_5, pelicula_id )
	values ( @valoracio, @codi_pelicula );

	--si valoració entre 3 i 5, incremento comptador
	if ( @valoracio between 3 and 5 ) 
	begin
	   update pelicules
	   set n_comentaris_positius = n_comentaris_positius + 1
	   where id = @codi_pelicula;
	end
end;

declare @i int;
set @i = 10000;
while @i > 0 begin
exec afegeix_valoracio 2, 4;
set @i = @i - 1;
end

select * from pelicules
```


**Solució amb trigger ( només contemplat cas de l'insert )**




```sql
alter trigger valoracio_insert on valoracions
after insert as begin
  --comprovo que no hi ha valors erronis
  if exists (select * 
             from inserted 
			 where valoracio_del_0_al_5 not between 0 and 5) begin
     raiserror( 'valor valoracio erroni', 16,1);
	 rollback
  end

  --incremento comptadors
  update p
  set n_comentaris_positius = n_comentaris_positius + qtat
  from pelicules p
  inner join 
     ( select i.pelicula_id, count(*) as qtat
	   from inserted i
	   where i.valoracio_del_0_al_5 between 3 and 5
	   group by i.pelicula_id ) v
  on p.id = v.pelicula_id

end

insert into valoracions values
( 1, 1),
( 1, 1),
( 1, 1),
( 1, 1),
( 4, 1),
( 5, 1);

select * from pelicules;
```


**Solució cursor**


```sql
begin transaction
set transaction isolation level serializable;


declare cursor_pelicules cursor for
select id, titol,n_comentaris_positius from pelicules ;

declare @pelicula_id int, 
        @titol varchar(200),
		@n_comentaris_positius int;

open cursor_pelicules;

fetch  from cursor_pelicules 
into @pelicula_id, @titol, @n_comentaris_positius;

while @@FETCH_STATUS = 0 begin
   print @titol;

   declare @num_val_pos int;

   /*
   select @num_val_pos = count(*)
   from valoracions v
   where v.pelicula_id = @pelicula_id
         and v.valoracio_del_0_al_5 between 3 and 5;
   */

   set @num_val_pos = 0;
   declare @valoracio_del_0_al_5 int;
   declare cursor_valoracions cursor for
	   select valoracio_del_0_al_5
	   from valoracions v
	   where v.pelicula_id = @pelicula_id;
   open cursor_valoracions;
   fetch from cursor_valoracions into @valoracio_del_0_al_5;
   while @@FETCH_STATUS = 0 begin
       if @valoracio_del_0_al_5 between 3 and 5 begin
	        set @num_val_pos += 1;
	   end;
       fetch from cursor_valoracions into @valoracio_del_0_al_5;
   end
   close cursor_valoracions;
   deallocate cursor_valoracions;

   print 'valoracions positives a pelicules ->' + str( @n_comentaris_positius)
   print 'valoracions positives a taula valoracions ->' + str( @num_val_pos )

   if @n_comentaris_positius != @num_val_pos begin
       update pelicules
       set  n_comentaris_positius = @num_val_pos
	   where id = @pelicula_id;
	   print 'base de dades fixada!';
   end

   fetch next from cursor_pelicules 
   into @pelicula_id, @titol, @n_comentaris_positius;
end;

close cursor_pelicules;
deallocate cursor_pelicules;

commit;
```


**Solució funció**

```sql
alter function num_val_positives( @id_pelicula int ) returns int as
begin
  declare @total int;
  select @total = count(*) from valoracions 
          where pelicula_id = @id_pelicula
		  and valoracio_del_0_al_5 between 3 and 5;
  return @total;
end 

select p.titol, dbo.num_val_positives( p.id )
from pelicules p ;
```

---

#FpInfor #Daw #Dam #Asix #AsixMp02 #DawMp02 #DamMp02 #DamMp02Uf03 #DawMp02Uf03 #AsixMp02Uf03

---

###### Autor: daniel herrera 2017.05.22 17:54:14
###### Editat per: daniel herrera 2017.05.23 17:13:40
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
