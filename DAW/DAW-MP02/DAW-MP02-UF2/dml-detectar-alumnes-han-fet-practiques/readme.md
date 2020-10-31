# DML: Detectar alumnes han fet pràctiques
## DAW-MP02-UF2 - Exercici de Llenguatges SQL: DML i DDL
###Col·leció de minipreguntes per comprovar que els alumnes han fet les pràctiques:

####Pregunta 1: Columna ambigua:
>ORA-00918
>Error: ORA-00918: column ambiguously defined
>Causa: A column name used in a join exists in more than one table and is thus referenced
>ambiguously. In a join, any column name that occurs in more than one of the tables must be >prefixed by its table name when referenced.

Posa una consulta exemple que produeixi aquest error amb aquestes taules.

```sql
Paisos ( codiPais (PK), nomPais)
Provincies ( codiPais (FK a Paisos), codiProvincia (PK), nomProvincia)

```
####Pregunta 2: Agregació en mal lloc?
Observa aquesta consulta estreta d'una [pregunta d'stackoverflow](http://stackoverflow.com/questions/15410802/error-in-using-aggregate-function-max-oracle)

```sql
select * 
from OS_Historystep 
where step_name = '011' and 
      finish_date = max(finish_date) ;
```

Explica perquè produeix l'error:

    ORA-00934: group function is not allowed here
    00934. 00000 -  "group function is not allowed here"
    *Cause:    
    *Action:
    Error at Line: 12 Column: 72
    
Reescriu-la per a que a que s'executi segons les expectatives de l'usuari.

####Pregunta 3: Aquesta sentència provoca error en Oracle i en SQL Server (no dona error en MySQL) Explica quin és l'error.

```sql
SELECT ssn, fname, minit, lname, AVG(hours)
FROM EMPLOYEE, WORKS_ON
WHERE EMPLOYEE.ssn = WORKS_ON.essn
GROUP BY hours
ORDER BY AVG(hours) DESC
```

Error a l'oracle: 

>ORA-00979: not a GROUP BY expression
>You tried to execute an SQL SELECT statement that included a GROUP BY function (ie: SQL MIN Function, SQL MAX Function, SQL SUM Function, SQL COUNT Function) and an expression in the SELECT list that was not in the SQL GROUP BY clause.

####Pregunta 4: Quan hi ha dependència en identificació, la clau forana pot prendre valors nulls? Per què?

####Pregunta 5: Quan no hi ha dependència en identificació, la clau forana pot prendre valors nulls. En aquest cas, la clau primària de la taula referenciada pot prendre valors nulls? Per què? En cas que hagis contestat no, com es fa per insertar tuples amb la clau forana a null?

---

#FpInfor #Daw #Dam #Asix #AsixMp02 #DawMp02 #DamMp02 #DawMp02Uf02 #AsixMp02Uf02 #DamMp02Uf02

---

###### Autor: daniel herrera 2013.09.07 14:42:02
###### Editat per: daniel herrera 2017.02.21 17:51:57
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
