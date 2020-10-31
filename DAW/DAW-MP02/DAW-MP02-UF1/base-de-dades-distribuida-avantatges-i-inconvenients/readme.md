# Base de dades distribuida - Avantatges i inconvenients
## DAW-MP02-UF1 - Exercici de Introducció a les bases de dades
Una base de dades distribuida és aquella que s'està executant en diferents màquines independents de manera simultànea i de forma transparent per als usuaris finals.

Optar per una base de dades distribuida té els seus avantatges i inconvenients. Podriem destacar els següents:

Avantatges que es poden assolir:

* Alta disponibilitat. Pot ser que un node caigui però la resta de nodes supleixen la seva absència.
* Alt rendiment. Els diferents nodes cooperen per tal d'executar les consultes en temps més curts.
* Fàcil creixement. Si cal més rendiment afegim nous nodes.

Inconvenients que ens podem trobar:

* Complexitat d'administració: calen més habilitats per tal de manegar una base de dades distribuida: seguretat, configuracions, etc.
* Complexitat de software: en cas que les transaccions estiguin suportades pel SGBDD aquestes són molt més complexes de manegar.
* Seguretat: els nodes han d'estar connectats entre ells, cal fer-ho de forma segura per evitar intrusos.

**Exercici**

1. Familiaritzat amb els avantatges i inconvenients aquí exposats.
2. Consulta altres fonts, per exemple la wikipedia, trobaràs que allà també s'exposen arguments relacionats.
2. Llegix l'article [Difference between scaling horizontally and vertically for databases](http://stackoverflow.com/questions/11707879/difference-between-scaling-horizontally-and-vertically-for-databases) i explica quina diferència hi ha entre escalat vertical i horitzontal.
3. ( Opcional ) El SGBD de Microsoft, anomenat SQL Server, utilitza un servei de Windows anomenat MSDTC ( MicroSoft Distributed Transaction Manager ) per tal de gestionar les transaccions distribuides:
    1. Observa que existeixen incidències relacionades amb aquesta integració.
    2. Busca com configurar el firewall de Windows per tal de permetre que el DTC es pugui comunicar entre els nodes del sistema.
    3. Enllaços que et poden ajudar:
        1. ["How do I enable MSDTC on SQL Server?"](http://stackoverflow.com/questions/7694/how-do-i-enable-msdtc-on-sql-server)  a StackOverflow
        3. ["Configure MSDTC on SQL Server and Adapter Client"](https://msdn.microsoft.com/en-us/library/dd787924.aspx)  a Miscrosoft MSDN
        3. ["Enable Firewall Exceptions for MS DTC"](https://technet.microsoft.com/en-us/library/cc725913.aspx) a Microsoft Technet


>
>######Aquest exercici està extret del llibre [d'exercicis Introducció a les Bases de Dades. UF1 MP2 DAM DAW ASIX](https://www.amazon.es/Introducci%C3%B3-Bases-Dades-asix-MP02-UF1/dp/153735096X) amb permís del seu autor.
>



---

#FpInfor #Daw #Dam #Asix #AsixMp02 #DawMp02 #DamMp02 #DawMp02Uf01 #AsixMp02Uf01 #DamMp02Uf01

---

###### Autor: daniel herrera 2016.06.15 07:48:48
###### Editat per: daniel herrera 2016.08.30 16:51:56
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
