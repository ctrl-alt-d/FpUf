# T-SQL Jugant una mica amb els permisos
## DAW-MP02-UF3 - Exercici de Llenguatges SQL: DCL i extensió procedimental
###Primera Part###

* Mitjançant l'assistent de l'SQL Server crea un Login 'l_alumne'.
* Mitjançant l'assistent fes una connexió amb 'l_alumne' i comprova que pots connectar-te al SGBD però no pots 'entrar' a veure cap base de dades.
* Mitjançant l'assistent, des del compte d'administrador, tria una base de dades i crea un usuari 'u_alumne' amb el login 'l_alumne'.
* Mitjançant l'assistent, des del compte 'l_alumne, comprova que pots 'entrar' en la base de dades triada però no pots veure les taules.
* Fes una consulta a la base de dades amb l'usuari administrador i otorga permisos de select a l'usuari 'u_alumne': `grant select on XXX to u_alumne'.
* Mitjançant l'assistent, des del compte 'l_alumne', comprova que pots veure i fer seleccions sobre aquella taula.
* Otorga permisos d'insert, update i delete. Prova els permisos des del login 'l_alumne'.
* Revoca tots els permisos, comprova que estan revocats.
* Mitjançant l'assistent, des del compte d'administrador, afegeix l'usuari 'u_alumne' al rol 'db_datawriter' i comprova que ara pot modificar les dades. Després tornar-li a des-assignar el permís.


### Segona part###

* Crea un rol i otorga-li permisos de CRUD sobre alguna taula. Utilitza SQL [CREATE ROLE](https://msdn.microsoft.com/en-us/library/ms187936.aspx)
* Afegeix un usuari com a membre d'aquell rol i comprova que pot realitzar les operacions. Utilitza SQL.

###Tercera part###

* Crea 10 logins mitjançant sql. [CREATE LOGIN](https://msdn.microsoft.com/en-us/library/ms189751.aspx)
* Crea un usuari per a cada login en una base de dades. Utilitza [CREATE USER](https://msdn.microsoft.com/en-us/library/ms173463.aspx)
* Crea dos rols, un que tingui permisos de lectura i un permisos d'escriptura. Afegeix a un rol la meitat d'usuaris i a tots dos rols la resta.


###ajuda

**creant logins de manera massiva**


```sql
declare @i int;
declare @p nvarchar(400);
set @i = 1000;
while @i > 14 begin
   set @p = 'CREATE LOGIN login_' + rtrim(ltrim( str(@i))) + ' WITH  PASSWORD = ''1'' ';    
   exec sp_executesql @p;
   set @i = @i - 1;
end;
```

**creant usuaris de manera massiva**


```sql
declare @i int;
declare @p nvarchar(400);
declare @n nvarchar(5);
set @i = 1000;
while @i > 14 begin
   set @n = rtrim(ltrim( str(@i)));
   set @p = 'CREATE USER user_' + @n + ' FOR LOGIN login_' + @n;    
   exec sp_executesql @p;
   set @i = @i - 1;
end;
```

**Crear roles**

```sql
create role escriu;
create role llegeix;

grant select on paraules to llegeix;
grant insert, delete, update on paraules to escriu;

alter role llegeix add member user_20;
alter role llegeix add member user_21;
alter role escriu add member user_21;
```

---

#FpInfor #Daw #Dam #Asix #AsixMp02 #DawMp02 #DamMp02 #DamMp02Uf03 #DawMp02Uf03 #AsixMp02Uf03

---

###### Autor: daniel herrera 2017.03.13 19:11:51
###### Editat per: daniel herrera 2017.03.14 18:55:17
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
