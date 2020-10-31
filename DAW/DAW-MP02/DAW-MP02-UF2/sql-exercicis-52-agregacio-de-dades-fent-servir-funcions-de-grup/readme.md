# SQL Exercicis 5.2: Agregació de dades fent servir funcions de grup
## DAW-MP02-UF2 - Exercici de Llenguatges SQL: DML i DDL
La Web StackOverflow permet fer consultas sobre la base de dades que hi ha darrera de la web.

Per fer-ho cal anar a [data.stackexchange.com](http://data.stackexchange.com/)  i punxar a 'Compose new query'.

A la pantalla, a la dreta apareixeran les taules i camps disponibles i a l'esquerra l'àrea per escriure una consulta.

Cal que consultis:

1) El número total de preguntes per cada tag. Quedat amb els 10 tags amb més preguntes ( usant un `select top 10` ). Cal mostrar tant el valor `count` de la taula tag com el recompte que facis tu agregant les preguntes. 

2) El número total de preguntes per cada tag. Quedat amb els tags amb més d'1 milió de preguntes. Cal mostrar tant el valor `count` de la taula tag com el recompte que facis tu agregant les preguntes. Ordena els resultats descendents per número de preguntes.

3) Els 10 usuaris amb més vots possitius aquest mes.

4) Escriu una consulta que ens doni una matriu. Tag x Numero de preguntes. Pels tags 'sql', 'java', 'xml'. Com aquesta:


    Tag     2016  2016
    java     100   232
    xml       12  1232 
    sql     1232   324

Els valors serien el total de posts per cada tag.

---

#FpInfor #Daw #Dam #Asix #AsixMp02 #DawMp02 #DamMp02 #DawMp02Uf02 #AsixMp02Uf02 #DamMp02Uf02

---

###### Autor: daniel herrera 2016.12.14 18:07:52
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
