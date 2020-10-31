# Exercicis XML, DTD i XSD
## DAW-MP04-UF1 - Exercici de Programació amb XML
1) Explica quina és la diferència entre un XML ben format ( *"well formet"* ) i un XML validat.

2) Completa aquesta [pregunta/resposta d'StackOverflow sobre escapar caracters en XML](http://stackoverflow.com/questions/1091945/what-characters-do-i-need-to-escape-in-xml-documents) i explica el motiu pel qual cal escapar-los:

![http://stackoverflow.com/questions/1091945/what-characters-do-i-need-to-escape-in-xml-documents](http://i.imgur.com/7qUGEmU.png)


3) Observa aquestes línia del [DTD configuration de hibernate](http://hibernate.org/dtd/):

    <!ELEMENT class-cache EMPTY>
    <!ATTLIST class-cache class CDATA #REQUIRED>
    <!ATTLIST class-cache region CDATA #IMPLIED>
    <!ATTLIST class-cache usage (read-only|read-write|nonstrict-read-write|transactional) #REQUIRED>
    <!ATTLIST class-cache include (all|non-lazy) "all">

Fes tres propostes diferents de l'element `class-cache` que poguem trobar en un xml de configuració d'hibernate. 

4) Tradueix aquest tall d'XSD a DTD:

![XSD Facturae](http://i.imgur.com/IzkdlzP.png)
 
5) Exercici:

* Escriu un DTD que validi completament aquest XML
* Escriu un XSD que validi completament aquest XML
* Documenta internament el document DTD o XML amb les decissions de validació que prenguis, per exemple, si una composició sempre ha de tenir autor o no.


XML:

```xml
<?xml version="1.0" encoding="utf-8"?>
<obres>
	<!-- Format per entre 0 i n llibre(s) i entre 0 i n composicio(ns)-->
	<llibre isbn="9788493806125">
		<titol>DON QUIJOTE DE LA MANCHA</titol>
		<any-publicacio>2011</any-publicacio>
		<autor>
			<nom-i-cognoms>Miguel de Cervantes Saavedra</nom-i-cognoms>
			<data-neixement>1547-09-29</data-neixement>
		</autor>
	</llibre>
	<llibre isbn="9788466751711">
		<titol>EL LAZARILLO DE TORMES</titol>
		<any-publicacio>2006</any-publicacio>
		<!-- anònim, no es coneix l'autor -->
	</llibre>
	<composicio cataleg="BWV 988">
		<titol>Variacions Goldberg</titol>
		<any-publicacio>1742</any-publicacio>
		<autor>
			<nom-i-cognoms>Johann Sebastian Bach</nom-i-cognoms>
			<data-neixement>1685-03-21</data-neixement>
		</autor>
	</composicio>
</obres>
```

---

#FpInfor #Daw #Dam #Asix #AsixMp04 #DawMp04 #DamMp04 #DawMp04Uf01 #AsixMp04Uf01 #DamMp04Uf01

---

###### Autor: daniel herrera 2016.11.10 14:19:59
###### Editat per: daniel herrera 2016.11.11 16:07:57
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
