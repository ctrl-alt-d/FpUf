# Exercici de selecció, restriccions, funcions d'una sola fila i join.
## DAW-MP02-UF2 - Exercici de Llenguatges SQL: DML i DDL
La Web StackOverflow permet fer consultas sobre la base de dades que hi ha darrera de la web.

Per fer-ho cal anar a [data.stackexchange.com](http://data.stackexchange.com/)  i punxar a 'Compose new query'.

A la pantalla, a la dreta apareixeran les taules i camps disponibles i a l'esquerra l'àrea per escriure una consulta.

Cal que consultis:

1) Tots els tipus de Post. Taula `postTypes`.

2) El títol ( `Title`) dels 10 primers ( `select top 10 ...`) posts de tipus 'Question' per ordre cronològic ( `CreationDate` ).

3) Els anys i mesos que han passat des de les 10 primeres preguntes. Cal concatenar i ha de quedar una única columna: *La pregunta "blah blah blah" es va plantejar fa 4 anys i 2 mesos*.



```sql
select top 10 
  concat(
      'La pregunta "',
      P.title,
      '" es va plantejar fa ',
      datediff( year, CreationDate, getdate() ),
      ' anys ',
      datediff( month, CreationDate, getdate() ) % 12,
      ' mesos ' )
from postTypes T
inner join posts P
   on P.PostTypeId = T.Id
where T.Name = 'Question'
order by CreationDate
```


4) Els 10 primers comentaris ( `comments` ) que al seu `text` comenci per la paraula `potato`. Cal mostrar el `text` del comentari i també qui l'ha escrit ( `DisplayName`  de la taula `Users`). Ull aquesta consulta pot trigar una mica.

```sql
select top 10 [Text], u.DisplayName
from comments c
inner join Users u
   on c.UserId = u.id
where [Text] like 'potato%'
order by c.CreationDate
```

 
5) Els títols de les preguntes dels tags *'iphone-sdk-documentation', 'large-fonts', 'balloons'* ordenat alfabèticament per tag i per títol.

```sql
select ta.TagName, p.title 
from       
     postTypes T
inner join 
     posts P
        on P.PostTypeId = T.Id
inner join 
     PostTags pt
        on pt.PostId = P.id
inner join 
     Tags Ta
        on Ta.id = pt.TagId
where T.Name = 'Question'  AND
      Ta.TagName in ('iphone-sdk-documentation', 
                     'large-fonts', 
                     'balloons' )
order by ta.TagName, p.title
```

---

#FpInfor #Daw #Dam #Asix #AsixMp02 #DawMp02 #DamMp02 #DawMp02Uf02 #AsixMp02Uf02 #DamMp02Uf02

---

###### Autor: daniel herrera 2016.12.13 17:36:14
###### Editat per: daniel herrera 2016.12.14 18:00:23
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
