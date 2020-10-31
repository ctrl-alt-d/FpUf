# Pràctica amb procediments, triggers, funcions i vistes.
## DAW-MP02-UF3 - Exercici de Llenguatges SQL: DCL i extensió procedimental
Observa aquestes dues taules:

```sql
create table pelicules  (
  id int identity not null,
  titol varchar(100) not null,
  n_comentaris_positius int default (0),  --valoracions entre 3 i 5
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

* Crea les taules a la base de dades i inserta unes cuantes fileres a cada taula.

* Un programador de SQL vol saber quin és el valor de FETCH_STATUS un cop ja no queden dades al cursor per llegir. Escriu el codi necessari per a saber quin és aquest valor.

* Què és una vista actualitzable? Digues dues condicions que ha de tenir una vista per a ser actualitzable. A partir de les dues taules anteriors escriu dues vistes, una que sigui actualitzable i l'altre que no ho sigui. Comprova-ho.

* Escriu un procediment emmagatzemat que compti el total de valoracions i el desi a la taula `recompte_valoracions` que cal crear-la amb aquesta estructura: `recompte_valoracions ( moment_del_recompte PK, total_valoracions )`

* Escriu una funció que donat un codi de pel·lícula retorni el total de valoracions positives, executa la funció per a cada pel·lícula mitjançant una select. 

* Crea un trigger de manera que quan s'insertin, actualitzin o s'esborrin valoracions ( ja sigui una o un conjunt de valoracions ) s'actualitzi el camp `n_comentaris_positius` .

* Escriu les comandes necessaries per a que només els usuaris del rol 'critics_rol' puguin insertar i llegir valoracions i llegir películes.

* Crea un login i un usuari per a 'Paco' i posa'l dins el rol 'critics_rol'. Comprova que 'Paco' només té els permisos que li hem atorgat.

* Digues a quin dels tres nivells de l'arquitectura ANSI-SPARC (extern, conceptual i intern ) pertanyen les vistes. Argumenta la resposta.

* La LOPD ens diu que els usuaris només han de consultar les dades que necessiten per a fer la seva feina. Però si donem accés de lectura a un usuari a una taula les veurà totes. Com podem fer per a que només vegi les que ha de veure. Posa un exemple.

** Exemple solució trigger complexitat mitjana:

```sql
create function dbo.get_valoracions_positives
 (  @pelicula_id int ) returns int AS
BEGIN
	declare @total_valoracions_positives int;
	select @total_valoracions_positives =
	       count(*)
	  from valoracions v
	 where v.pelicula_id = @pelicula_id
	   and valoracio_del_0_al_5 between 3 and 5;
	return @total_valoracions_positives;
END;

```

    alter trigger actualitza_comptador_comentaris_positius
    on valoracions AFTER INSERT, UPDATE , DELETE 
    as BEGIN
    	
    	update pelicules
    	set n_comentaris_positius = 
    	    dbo.get_valoracions_positives( id )
    	where 
    	    id in 
    	       ( select pelicula_id from inserted 
    	         UNION
    	         select pelicula_id from deleted)
    END

** Exemple solució del trigger 'super quirúrgic':

```sql
crate trigger actualitza_comptador_comentaris_positius
on valoracions AFTER INSERT, UPDATE , DELETE 
as BEGIN
	
	with g_inserted as
	   ( select pelicula_id, count(*) as n
	       from inserted i
	       where i.valoracio_del_0_al_5 >= 3
	       group by i.pelicula_id
	       )
	update p
	set p.n_comentaris_positius = 
	          p.n_comentaris_positius + i.n	
	from pelicules p
	inner join g_inserted i
	on i.pelicula_id = p.id
    ;

	with g_inserted as
	   ( select pelicula_id, count(*) as n
	       from deleted i
	       where i.valoracio_del_0_al_5 >= 3
	       group by i.pelicula_id
	       )
	update p
	set p.n_comentaris_positius = 
	          p.n_comentaris_positius - i.n	
	from pelicules p
	inner join g_inserted i
	on i.pelicula_id = p.id
    ;
	
END;
```

---

#FpInfor #Daw #Dam #Asix #AsixMp02 #DawMp02 #DamMp02 #DamMp02Uf03 #DawMp02Uf03 #AsixMp02Uf03

---

###### Autor: daniel herrera 2017.05.31 08:26:27
###### Editat per: daniel herrera 2018.04.27 14:31:36
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
