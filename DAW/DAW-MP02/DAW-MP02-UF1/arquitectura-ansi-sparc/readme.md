# Arquitectura ANSI-SPARC
## DAW-MP02-UF1 - Exercici de Introducció a les bases de dades
Al 1975 es proposa un estàndard d'arquitectura a seguir pels SGBD. És una proposta abstracte on es diferencien 3 nivells: l'extern, el conceptual i l'intern. El nom de la proposta ve de la pròpia organització estandaritzadora: **American National Standards Institute, Standards Planning And Requirements Committee**.

L'objectiu dels tres nivells és assolir la independència lògica i física de les dades. El nivell extern és el que l'usuari pot veure. El conceptual serien totes les estructures de dades, relacions i dades. El nivell físic és el que amagaria els detalls de com les dades són persistides al sistema.

**Exercici**

Observa aquestes tres sentències SQL amb quin nivell de l'arquitectura ANSI-SPARC estan relacionats i per què:

1) Creació d'una vista sobre dades:

```SQL
CREATE VIEW comandes_zona_A AS
SELECT * FROM comandes WHERE zona = 'A';
```

2) Creació d'un index cluster:

```SQL
CREATE CLUSTERED INDEX idx_comandes_zona
ON comandes (zona); 
```

3) Creació d'una taula:

```SQL
CREATE TABLE comandes ( id_comanda int, data date, zona char );
```

4) En aquests moments a stackoverflow hi ha una sola pregunta amb l'etiqueta ansi-sparc. La pregunta és d'una qualitat espantosa però és una bona oportunitat per a col·laborar en aquesta web de programadors. Posa una resposta a la pregunta [ANSI-SPARC practical explanation](https://stackoverflow.com/questions/9771884/ansi-sparc-practical-explanation) a partir dels coneixements adquirits en aquesta pràctica. No oblidis posar exemples concrets de sentències SQL com les que hi ha en aquest enunciat i de puntuar positivament als companys que hagin fet bona feina allà.
    

>
>######Aquest exercici està extret del llibre [Introducció a les Bases de Dades. UF1 MP2 DAM DAW ASIX](https://www.amazon.es/Introducci%C3%B3-Bases-Dades-asix-MP02-UF1/dp/153735096X) amb permís del seu autor.
>


**First sample logical independence**

Sample of keep logical independence through database dessign changes:

Before the change a single table of customers with email and fax:


```sql
create table customers ( id int, name varchar(200), 
                         email varchar(200), fax varchar(200) );
create view customers_external_view as select * from customers;
```

After the change the customer table is splitted on 2 tables, but external view shows the same fields:
    
```sql
create table customers ( id int, name varchar(200) );
create table customers_adresses ( id int, id_client int, 
                                  adress_type varchar(10), adress varchar(200) );

create view customers_external_view as 
   select c.*,  ca2.adress as email, ca1.adress as fax
     from customers c
       left outer join customers_adresses ca1 
         on ca.adress_type = 'fax' and ca.id_client = c.id
       left outer join customers_adresses ca2 
         on ca.adress_type = 'email' and ca.id_client = c.id ;
```


**Sample 2**

Tenim una taula de passatgers on apareix el número de vol i el seient:

```sql
create table passengers ( nif varchar(200), name varchar(200), 
                         num_flight varchar(200), num_seat varchar(200) );
create view passengers_external_view as select * from passengers;
```

Trenquem la relació en dues taules: passatgers i vols. La vista externa segueix mostrant la mateixa informació.

```sql
create table passengers ( nif varchar(200), name varchar(200) )
create table flight_passengers ( nif varchar(200), num_flight int, 
                                  num_flight varchar(200), num_seat varchar(200) );

create view passengers_external_view as 
   select p.*, fp.num_flight, fp.num_seat
     from passengers p
       left outer join flight_passengers fp 
          on fp.nif = p.nif ;    
```

**Tercer exemple**

Un banc té una taula de clients amb els diners que té dipositats al banc:

```sql
create table customers( nif varchar(200), name varchar(5000), balance numeric(15,2) );
create view customers_external_view as select * from customers;
```

Ara el banc apunta cada operació que fa, però volem que les aplicacions segueixin veient el saldo:


```sql    
create table customers( nif varchar(200), name varchar(5000) );
create table movements( nif varchar(200), moment datetime, import numeric(15,2) );
create view customers_external_view as 
  select c.nif, c.name, sum( m.import ) as balance
    from customers c
    left outer join movements m 
      on c.nif = m.nif
group by c.nif, c.name ;
```


---

#FpInfor #Daw #Dam #Asix #AsixMp02 #DawMp02 #DamMp02 #DawMp02Uf01 #AsixMp02Uf01 #DamMp02Uf01

---

###### Autor: daniel herrera 2016.05.18 14:37:32
###### Editat per: daniel herrera 2016.09.28 17:17:17
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
