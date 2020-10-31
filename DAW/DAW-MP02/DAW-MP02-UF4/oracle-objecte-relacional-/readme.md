# Oracle Objecte-Relacional - Reparacions mecàniques - Taula amb columna tipus objecte i mètode
## DAW-MP02-UF4 - Exercici de Bases de dades objectes-relacionals
**Objectiu didàctic**

 * Treballar amb taula amb columna de tipus objecte.
 * Invocar mètodes de l'objecte

**Pràctica**

*UNIVERS DE DISCURS*

Un taller mecanic vol emmagatzemar les reparacions que realitza. Dels cotxes els interesa la matrícula, el propietari, la marca model i la potència. També demanen alguna forma de calcular els cavalls del cotxe perquè alguns clients han demanat si sabrien quan ha de pagar d'impost de circulació ( potReal*1.36 )

De la reparació volen emmagatzemar el numero de factura (o l'id), la data d'entrada del vehicle, el que li passa, la data de sortida si s'escau i el cotxe.

Cotxe serà un objecte a la BDD i s'emagatzema a la taula de reparacions conjuntament amb la resta de dades de la reparació.

```SQL
-- Preparació de l'entorn
--Crear usuari i BDD
CREATE USER mecanic
IDENTIFIED BY ies
DEFAULT TABLESPACE users
TEMPORARY TABLESPACE temp;
GRANT connect, resource TO mecanic;
```

    --Crear el tipus cotxe. Que tindrà una funció que calcularà els cavalls del cotxe
    CREATE or replace TYPE cotxe_typ AS OBJECT(
      matricula varchar2(10),
      propietari varchar2(40),
      marcaModel varchar(60),
      potReal float,
      member function cavalls return float
      );
      /

    CREATE or replace TYPE body cotxe_typ AS
      member function cavalls return float is
      begin
        return potReal*1.36;
      end;
    end;
    
    --Crear la taula amb l'atribut de tipus objecte cotxe_typ
    CREATE TABLE reparacio(
      idReparacio integer PRIMARY KEY,
      dataEntrada date not null,
      incidencia varchar2(200) not null,
      dataSortida date null,
      cotxe cotxe_typ not null)
     
    -- Inserim dades a la taula de reparació
    INSERT INTO reparacio VALUES (
      1,
      '07-04-2014',
      'Explosió del motor, fer el canvi',
      null,
      cotxe_typ('1111-AAA','Pere Pi', 'Ferrari California',338));
    
     INSERT INTO reparacio VALUES (
      2,
      '07-04-2014',
      'Fa un soroll estrany.',
      null,
      cotxe_typ('2222-BBB','Julián Fernández', 'Seat Ibiza',74));

    --Seleccionem la incidencia de cada cotxe amb la seva potència en cavalls cridant al mètode cavalls de l'objecte cotxe
    select r.incidencia, r.cotxe.cavalls() from reparacio r

**Exercicis**

* Executa aquestes sentències al teu entorn Oracle tot comprovant i entenent els resultats.
* Fes una columna de tipus MAP per tal que al comparar dos objectes de tipus cotxe digui que són el mateix si tenen la mateixa matrícula.

*By C.Chaillet & J.Fernández*

---

#FpInfor #Daw #DawMp02 #DawMp02Uf04

* Resultats d'aprenentatge 1.B 1.D 1.F 1.G
* Continguts 1.1 1.3 1.4 1.8 1.9 1.10
---

###### Autor: daniel herrera 2014.04.11 13:53:01
###### Editat per: daniel herrera 2018.04.03 15:00:06
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
