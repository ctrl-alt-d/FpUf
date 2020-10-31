# Poligons: triange, quadrilàter i pentàgon
## DAW-MP02-UF4 - Exercici de Bases de dades objectes-relacionals
** Falta l'enunciat **



```sql
create type poligon_typ as object (
   id int,
   not instantiable member function area return float
) not final not instantiable;

create type triangle_typ under poligon_typ (
  x1 float,
  y1 float,
  x2 float,
  y2 float,
  x3 float,
  y3 float,
  OVERRIDING member function area return float
);

create or replace type body triangle_typ as
  OVERRIDING member function area return float is
  begin
    return 0.5 * abs(x1 * y2 + x2 * y3 + x3 * y1 - x2 * y1 - X3 * y2 - X1 * Y3 ) ;
  end;
end;


create type quadrilater_typ under poligon_typ (
  x1 float,
  y1 float,
  x2 float,
  y2 float,
  x3 float,
  y3 float,
  x4 float,
  y4 float,
  OVERRIDING member function area return float
);

create or replace type body quadrilater_typ as
  OVERRIDING member function area return float is
  begin
    return 0.5 * abs(x1 * y2 + x2 * y3 + x3 * y4 + x4 * y1 
                  - x2 * y1 - X3 * y2 - x4 * y3 - x1 * y4 ) ;
  end;
end;

create type pentagon_typ under poligon_typ (
  x1 float,
  y1 float,
  x2 float,
  y2 float,
  x3 float,
  y3 float,
  x4 float,
  y4 float,
  x5 float,
  y5 float,
  OVERRIDING member function area return float
);

create or replace type body pentagon_typ as
  OVERRIDING member function area return float is
  begin
    return 0.5 * abs(x1 * y2 + x2 * y3 + x3 * y4 + x4 * y5 + x5 * y1
                  - x2 * y1 - X3 * y2 - x4 * y3 - x5 * y4 - x1 * y5) ;
  end;
end;

create table poligons of poligon_typ ( id primary key );

insert into poligons values
  ( triangle_typ (1,  1,1,2,2,7,7 ) );
  
insert into poligons values
  ( triangle_typ (3,  1,1,2,2,3,1 ) );

  
insert into poligons values
  ( pentagon_typ(2,  1,1,1,2,2,2,4,2,18,1) )


-------------------------
```

---

#FpInfor #Daw #DawMp02 #DawMp02Uf04

---

###### Autor: daniel herrera 2017.04.25 18:18:43
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
