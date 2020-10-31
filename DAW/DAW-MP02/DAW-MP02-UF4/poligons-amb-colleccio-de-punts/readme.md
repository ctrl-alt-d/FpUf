# Poligons: amb col·lecció de punts
## DAW-MP02-UF4 - Exercici de Bases de dades objectes-relacionals
**Falta enunciat**

```sql
create type punt_typ as object (
   x float,
   y float);
   
create type punts_typ as table of punt_typ;

create type poligon_plus_typ as object(
   id int,
   punts punts_typ,
   member function area return float
)   

create or replace type body poligon_plus_typ as 
   member function area return float is
   area_aux float;
   begin
      area_aux := 0;
      for i in 1 .. self.punts.count - 1 LOOP
         area_aux := area_aux + self.punts(i).x * self.punts(i+1).y;
      end loop;
      area_aux := area_aux + self.punts(self.punts.count).x * self.punts(1).y;

      for i in 1 .. self.punts.count - 1 LOOP
         area_aux := area_aux - self.punts(i+1).x * self.punts(i).y;
      end loop;
      area_aux := area_aux - self.punts(1).x * self.punts(self.punts.count).y;

      return 0.5 * abs( area_aux );
   end;
end;


create table poligons_plus of poligon_plus_typ 
(id primary key)
nested table punts store as poligons_nt;


insert into poligons_plus values
( poligon_plus_typ( 1, 
                    punts_typ( punt_typ( 1,1), 
                               punt_typ( 2,2), 
                               punt_typ( 2,1))))

insert into poligons_plus values
( poligon_plus_typ( 2, 
                    punts_typ( punt_typ( 1,1), 
                               punt_typ( 1,2), 
                               punt_typ( 2,2),
                               punt_typ( 2,1)
                               )))

select p.id, p.area() from poligons_plus p;
```

---

#FpInfor #Daw #DawMp02 #DawMp02Uf04

---

###### Autor: daniel herrera 2017.04.25 18:38:37
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
