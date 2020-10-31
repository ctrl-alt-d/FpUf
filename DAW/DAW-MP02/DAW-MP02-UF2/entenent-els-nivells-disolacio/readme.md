# Entenent els nivells d'isolació
## DAW-MP02-UF2 - Exercici de Llenguatges SQL: DML i DDL
En el video [nivells de isolació](https://youtu.be/6Wfu9ueOJ6g) trobareu una explicació de les possibles anomalies de lectura i com se solucionen amb els nivells d'isolació.

[![nivells d'isolació](http://i.imgur.com/t04maAW.png)](https://youtu.be/6Wfu9ueOJ6g)

**Exercici.** 

A continuació es plantegen dos programets que modifiquen dades a la base de dades. Observa el codi i digues quin seria el nivell d'isolació mínim ideal per a cadascun d'ells.

**Cas 1** Una empresa de taxis assigna els viatges a un taxi a l'atzar. Fixat en el codi SQL, digues quin problema poden tenir segons el nivell d'isolació en que s'executi la transacció:

```sql
begin transaction;
insert into viatges ( id, numPassatgers, origen )  --insertem viatge num 1000
values ( 1000, 3, 'Cruilla Balmes-Muntaner' );  
commit;

begin transaction;

set @ID = ( select top 1 idTaxi      --seleccionem un taxi
            from taxis
            where idViatgeActual is Null
            order by newid() );

Update taxis                   --li assignem el viatge
set idViatgeActual = 1000;
commit;
```

**Cas 2** Una companya d'avions utilitza el següent algoritme per tal de canviar els viatgers de seient quan aquests ho demanen. Amb quins nievells d'isolació el viatger es pot quedar a terra? Per què?

```sql
SET @seient_desitjat = 100;
SET @seient_actual = 210;
BEGIN TRANSACTION;
--comprovo que està lliure:
SET @num_ocupants = ( select coalesce( count(*), 0 )
                     from seients
                     where id =  @seient_desitjat );
--si no està lliure sortir
IF @nun_ocupants > 0 THEN BEGIN
   RAISERROR (50005, 10, 1, N'El seient desitjat no està lliure');
   ROLLBACK;
END ELSE
   --si està lliure el desitjat allibero l'actual i agafo el nou.
   DELETE FROM seients WHERE id = @seient_actual;
   INSERT INTO seients (id, passatger) VALUES( @seient_desitjat, @numPassatger);
   COMMIT;
END;
```


**Solucions**

Cas 1: El nivell d'isoliació `read commited` no és suficient, potser assignen un viatge al taxi just abans del nostre `update`. Cal un nivell d'isolació `repeatable read`.

Cas 2: Per reservar els seients es fan inserts a la base de dades, el nivell d'isolació  `serialitzable` és l'únic que ens garanteix que no s'insertaran dades dins del conjunt de dades llegits en la comprovació del seient lliure.

---

#FpInfor #Daw #Dam #Asix #AsixMp02 #DawMp02 #DamMp02 #DawMp02Uf02 #AsixMp02Uf02 #DamMp02Uf02

---

###### Autor: daniel herrera 2017.01.18 17:59:25
###### Editat per: daniel herrera 2017.01.18 18:57:58
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
