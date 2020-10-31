# Base de dades. El camí de la consulta.
## DAW-MP02-UF1 - Exercici de Introducció a les bases de dades
El sistema gestor de base de dades processa les consultes que li arriben. Entenem consulta en un sentit ampli, una consulta pot ser també una ordre per modificar el valor d'un conjunt de dades, crear-ne de noves o esborrar-ne. 

El sistema gestor de base de dades ha de traduir la consulta que li arriba al seu llenguatge intern, comprovar que l'usuari té permisos per a realitzar-la, buscar la manera óptima d'accedir a les dades, mantenir la integritat de les dades segons les regles establertes, mantenir estructures en memòria i disc per tal que les consultes siguin ràpides i retornar els resultats. 

La programació interna del SGBD distribueix totes aquestes responsabilitats en mòduls que anomenem **components**. Així doncs tenim el *parser* que comprova la sintaxi de la consulta i la tradueix al llenguatge intern del SGBD, l'*optimitzador* que busca la manera més eficient de realitzar la consulta mitjançant els indexos, el *gestor de buffers* que decideix quines estructures estan en memòria i quan es passen a disc, el *controlador d'integritat* que garantitza que les dades seguirant complint amb les regles establertes, el *gestor de transaccions* que permet la concurrència a les dades de manera endreçada i el *controlador d'autoritzacions* que comprova si l'usuari pot realitzar les operacions. 

A banda hi ha altres components que també tenen les seves tasques com el *planificador de tasques* que executa tasques a determinades hores o el *gestor de recuperació* que s'encarrega de poder fer còpies de seguretat sense aturar la base de dades. 

**Exercici**

Un usuari fa una consulta a la base de dades. Es contemplen dues vies, mitjançant aplicació web o amb aplicació client/servicor. Completa la següent il·lustració tot posant noms als components que manquen. 

![diagrama components de una base de dades](http://i.imgur.com/nGb9Di8.png)




>
>######Aquest exercici està extret del llibre [Introducció a les Bases de Dades. UF1 MP2 DAM DAW ASIX](https://www.amazon.es/Introducci%C3%B3-Bases-Dades-asix-MP02-UF1/dp/153735096X) amb permís del seu autor.
>




---

#FpInfor #Daw #Dam #Asix #AsixMp02 #DawMp02 #DamMp02 #DawMp02Uf01 #AsixMp02Uf01 #DamMp02Uf01

---

###### Autor: daniel herrera 2016.05.17 07:59:31
###### Editat per: daniel herrera 2016.08.30 16:50:09
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
