# Integritat referencial. Treballant amb claus foranes.
## DAW-MP02-UF2 - Exercici de Llenguatges SQL: DML i DDL
Observa el post [Getting complicated about foreign key](http://stackoverflow.com/q/23718559/842935) de l'stackoverflow.

**[user3248713](http://stackoverflow.com/users/3248713/user3248713) question**:

I am a beginner in innoDB and not very good in database. I m getting confused about foreign keys. I just want to know is:

 - If I delete a PK( fk on another table)
   - is the FK on child table also deleted?
   - So how about if I delete FK on child table?
   - Record in parent table also deleted?
 - Also, if I ADD a new record to parent table
    - child table also added?
    - How about i add to child table?
    - How about if i update data?

Please help me, I am very confused about foreign key reference in innoDB database . Guide me to the easiest way. Thanks.

**[spencer7593](http://stackoverflow.com/users/107744/spencer7593) answer**:

Assuming that the foreign key constraints are defined, supported by the storage engine and are enabled, (MySQL vrforeign_key_checks = 1)


Q: If I delete a PK( fk on another table) , is the FK on child table also deleted ?

A: If the DELETE rule is specified as CASCADE, then a delete on the parent table will also perform delete operation on the child table. If the DELETE rule is specified as RESTRICT, and there's rows in the child table that reference the parent key, then the DELETE operation will raise an error.


Q: If I delete FK on child table? Record in parent table also deleted ?

A: No. Deleting rows in the child table will have no affect on the parent table.

Q: If I INSERT a new row to parent table, child table also added ? 

A: No. Rows are *not* automatically inserted to child tables. It's valid (relational database-wise) to have a parent row that does not have any child rows referencing it.

Q: If I INSERT a row to the child table ?

A: No, and insert to the child table does not automatically insert a row to the parent table. (Any non-null value of the foreign key column being inserted to the child table will be validated; the database will verify that there already exists a row in the parent table with a matching value. If there's not, then the INSERT will fail with an error.)

Q: What if I UPDATE values of the foreign key column in the child table.

A: Same as with an insert, the new value will be validated before the update operation proceeds.

Q: What if I UPDATE the value of the primary key in the parent table?

A: If the UPDATE rule on the foreign key is specified as CASCADE, then the related rows in the child table will also be updated, to preserve the relationship between the rows. If the UPDATE rule is RESTRICT, and there are related rows in the child table, the update operation will raise an error.

---

Foreign keys are designed for enforcing referential integrity. They basically disallow inserts/updates in the child table when the new non-null values of the foreign key column doesn't reference a row in the parent.

The UPDATE and CASCADE rules defined on the foreign key constraint determine the behavior of UPDATE and DELETE operations on the parent table.

(by [spencer7593](http://stackoverflow.com/users/107744/spencer7593) )

**Exercici**:

* Crea un disseny de base de dades on puguis provar totes i cadascuna de les explicacions que ofereix *spencer7593* a la seva resposta.
* Escriu les taules amb les restriccions d'integritat del disseny elaborat.
* Fes les provatures per comprovar que el que contesta *spencer7593* és cert. Documenta tota i cadascuna de les proves que realitzis.






---

#FpInfor #Daw #Dam #Asix #AsixMp02 #DawMp02 #DamMp02 #DawMp02Uf02 #AsixMp02Uf02 #DamMp02Uf02

* Resultats d'aprenentatge 2.g
* Continguts 2.1.1
---

###### Autor: daniel herrera 2014.05.18 11:08:15
###### Editat per: daniel herrera 2014.05.18 11:08:15
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
