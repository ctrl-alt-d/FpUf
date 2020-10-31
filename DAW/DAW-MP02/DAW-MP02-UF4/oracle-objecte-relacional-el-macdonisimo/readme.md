# Oracle Objecte-Relacional - El macdonísimo
## DAW-MP02-UF4 - Exercici de Bases de dades objectes-relacionals
Treballarem
===========

* Taula d'objectes amb herència.
* Referència a objectes.
* Mètodes no instanciables.
* Sobreescriure mètodes.
* Seleccions sobre subtipus i execució de mètodes.

Enunciat
========

Una hamburgeseria ofereix diferents tipus de productes. Per al nostre exemple ens centrarem en SandWiches, Begudes i Postres. 

El nostre dissenyador ha decidit que existeix la classe 'Producte' ( de la quan no es poden instanciar objectes ) i que d'ella hereten els altres tipus, amb aquestes particularitats:

* Els productes tenen nom i preu.
* Les begudes (subtipus de productes), a més, CC ( centimetres cúbics ). Exemple: CocaCola gran té 250 CC.
* Els sandwidchos (subtipus de productes) tenen 'Comentari Origen Carn', per exemple, la GRAND McEXTREM ORIGINAL és 100% vacuno extremeño.
* I de les postres (subtipus de productes) emmagatzemem les calories. EX: LE PLAISIR CHOCOLATE té 250 calories.

Tot plegat ho emmagatzemem a la taula de productes  (és taula d'objectes)

A banda, tenim una taula d'ofertes. És una taula d'objectes, per això es crea el tipus oferta amb els subtipus oferta producte i oferta menú. 

No tots els productes estan disponibles sempre i hi ha productes que són combinacions d'altres productes ( els menús ). Per això tenim:

Tipus Oferta: No instaciable, data inici oferta i data fi. Mètodes get_nom i get_preu.
Subtipus oferta producte: referència a un producte. Mètodes get_nom i get_preu.
Subtipus oferta menu: conté el nom del menú, el preu del menú, referència a un sandwidch, referència a una beguda i referència a unes postres (total 3 camps de referència) Mètodes get_nom i get_preu. Nota: tot i ser referència a sandwidch, quan ho implementis, declara-ho com a referència a producte per a simplificar el desenvolupament.

Els mètodes get_nom i get_preu a Tipus Oferta són no instanciables. Es sobreescriuen a Subtipus oferta producte on retornen els valors (preu i nom) de la taula de productes i es sobreescriuen a Subtipus oferta menu i prenen el valor nom de la pròpia classe i el preu de la suma de preus del subtipus producte aplicant un 10% de descompte al total.

**Es demana:**

* Totes les sentències DDL utilitzades, ordenades i comentades.
* Captura de pantalla on es vegi el la selecció final.

**Superbonus track:**

Fes que Subtipus oferta menú contingui taula de referència a productes en comptes de taula de productes i que el preu l'obtingui de la suma de tots els productes aplicant un 10% de descompte.

Solució
=======


```SQL
```

    --tipus base producte
    CREATE TYPE producte_typ AS OBJECT (
    
      nom     VARCHAR2(20),
      preu    number(5,2)
      ) not instantiable not final;
    
    --subtipus de producte: beguda, sandwidch, postres
    CREATE TYPE beguda_typ  under producte_typ  (
      CC     integer
      ) final;
      
    CREATE TYPE sandwidch_typ  under producte_typ  (
      origen_carn varchar2(200)
      ) final;
    
    CREATE TYPE postres_typ  under producte_typ  (
      calories int
      ) final;
    
    --taula d'objectes producte
    create table productes_tab of producte_typ;
    
    --inserció de dades a la taula de productes. Polimorfisme.
    insert into productes_tab values (
       new beguda_typ( 'cocacola petita', 1, 125)
    );    
    
    insert into productes_tab values (
       new beguda_typ( 'cocacola grosa', 2, 450)
    ); 
    
    insert into productes_tab values (
       new sandwidch_typ  ( 'mc vedella', 4, 'cantabria')
    );   
    
    insert into productes_tab  values (
       new postres_typ  ( 'danonino', 1.5, 1000)
    ); 
    
    -----------
    
    --Tipus base oferta
    CREATE TYPE oferta_typ AS OBJECT (
    
      inici     date,
      fi    date,
      not instantiable member function get_nom return varchar2,
      not instantiable member function get_preu return number
      ) not instantiable not final;
    
    --Subtipus d'oferta: Oferta d'un producte
    CREATE TYPE oferta_producte_typ under oferta_typ (
       producte ref producte_typ,
       OVERRIDING member function get_nom return varchar2,
       OVERRIDING member function get_preu return number
      )  instantiable  final;
    
    
    CREATE or replace TYPE BODY oferta_producte_typ AS
      OVERRIDING  MEMBER FUNCTION get_nom RETURN varchar2 IS
        producte_v producte_typ;
      BEGIN
        select deref(producte) into producte_v from dual;
        RETURN producte_v.nom;
      END;
      OVERRIDING  MEMBER FUNCTION get_preu RETURN NUMBER IS
        producte_v producte_typ;
      BEGIN
        select deref(producte) into producte_v from dual;
        RETURN producte_v.preu;
      END;
    END;

    --Subtipus d'oferta: Oferta menú    
    CREATE TYPE oferta_menu_typ under oferta_typ (
       nom_menu varchar(100),
       sandwidch ref producte_typ,
       beguda ref producte_typ,
       postres ref producte_typ,
       OVERRIDING member function get_nom return varchar2,
       OVERRIDING member function get_preu return number
      )  instantiable  final;
    
    CREATE or replace TYPE BODY oferta_menu_typ AS
      OVERRIDING  MEMBER FUNCTION get_nom RETURN varchar2 IS
      BEGIN
        RETURN nom_menu;
      END;
      OVERRIDING  MEMBER FUNCTION get_preu RETURN NUMBER IS
        s producte_typ;
        b producte_typ;
        p producte_typ;
      BEGIN
        select deref(sandwidch ) into s from dual;
        select deref(beguda) into b from dual;
        select deref(postres) into p from dual;
        RETURN (s.preu + b.preu + p.preu) * 0.9;
      END;
    END;
    
    --creació de la taula d'ofertes. Polimorfisme.
    create table ofertes_tab of oferta_typ;
    
    --Inserció d'ofertes
    declare
       minicocacola_ref ref producte_typ;
       burger_ref ref producte_typ;
       postres_ref ref producte_typ;
    begin
        select ref(b) into minicocacola_ref
          from productes_tab b
          where nom =  'cocacola petita';
        select ref(b) into burger_ref 
          from productes_tab b
          where nom =  'mc vedella';
        select ref(b) into postres_ref 
          from productes_tab b
          where nom =  'danonino';
        insert into ofertes_tab values ( 
          new oferta_producte_typ( sysdate-100, sysdate+100, minicocacola_ref )
          );
        insert into ofertes_tab values ( 
          new oferta_menu_typ ( sysdate-100, sysdate+100, 'mc menu', burger_ref, minicocacola_ref, postres_ref  )
          );
    end ;

    --selecció d'ofertes, execució de mètodes als subtipus    
    select  value( o).get_nom(),  value( o).get_preu() from ofertes_tab o;
    
    
        
    
    
    
    
    
    







---

#FpInfor #Daw #DawMp02 #DawMp02Uf04

---

###### Autor: daniel herrera 2015.05.05 14:57:00
###### Editat per: daniel herrera 2015.05.05 14:57:00
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
