# "RETO" - Aplicació web farmàcies
## DAW-MP07-UF2 - Exercici de Generació dinàmica de pagines web.
**Objectiu**: Confeccionar aplicació Web comentaris sobre farmàcies.

**Introducció de la pràctica**

* [Introducció arquitectura web](https://youtu.be/q8YBQbiiDWo) YT 19'
* [Reto Farmàcies: Arquitectura MVC](https://youtu.be/BkmcPG6KWsE) YT 24'

**Resolució de la pràctica**

* [Reto Farmàcies: Preparant el projecte](https://youtu.be/wpRIdlxdOdw) YT 28'
* [Reto Farmàcies: Creant models i BD](https://youtu.be/bfem7jKxPfI) YT 52'
* [Reto Farmàcies: Càrrega dades inicials 'seed' 1a part](https://youtu.be/wJ4J4OK-wCU) YT 35'
* [Reto Farmàcies: Càrrega dades inicials 'seed' 2a part](https://youtu.be/feyGjnO42GQ) YT 55'''
* [Reto Farmàcies: Controladors i vistes 1a Part](https://youtu.be/P9c-Ea3GiJw) YT 33'
* [Reto Farmàcies: Controladors i vistes 2a Part](https://youtu.be/2sgdDLmtueU) YT 58'

###Estructura de dades:

>Provincia - Municipi - Farmàcia - Comentari

###Funcionalitat:

* Pantalla principal mostra les 4 províncies i un màxim de 10 localitats a cada província. Fa servir [Panel with heading](http://getbootstrap.com/components/#panels-heading) on la capçalera és el nom de la provincia i al body hi trobem els 10 primers municipis per ordre alfabètic.
* Quan es punxa en una província apareixen en forma de taula totes les poblacions de la província ( clicables )
* Quan es punxa en una població apareixen en forma tabular totes les farmàcies d'aquella població (clicables).
* Quan es punxa en una farmàcia apareix el detall de les dades de la farmàcia.
* A les farmàcies apareix un formulari per poder afegir comentaris sobre aquella farmàcia. Els comentaris es llisten a la pròpia pàgina de detall.

###Desenvolupament de la pràctica:

La pràctica es realitza en grup. Es diferencien una sèrie de rols necessaris per a completar-la. Cada alumne pot prendre un o més rols durant la realització de la pràctica.

####Rol 1: Importador de dades

Les provincies de catalunya a mà ( prepara sentències ORM per crear-les). La PK serà el codi província (ex: '08' Barcelona )

Descarrega les dades de [farmàcies de Catalunya](http://salutweb.gencat.cat/ca/ambits_tematics/per_perfils/empreses_i_establiments/oficines_de_farmacia/farmacies_farmacioles/) i prepara les sentències necessàries per persistir-ho en una base de dades.

Utilitça [get_or_create](https://docs.djangoproject.com/en/1.9/ref/models/querysets/#get-or-create) per a crear els municipis.

####Rol 2: Creador de models

Crea els models necessaris per a persistir les dades. Prepara les migrations i aplicales.

####Rol 3: Disenyador projecte

* Dissenya quines aplicacions, urls i vistes tindrà aquesta web i assigna urls a cadascuna d'elles.
* Crea scaffolding de urls i vistes ( totes retornen 'hello world' ) 
* Crea el template `base.html` amb els blocs necessaris per poder-lo extendre. El deixa preparat per a que el dissenyador hi afegeixi css o js.

####Rol 4: Desenvolupador

* Desenvolupa les vistes per a que tot funcioni correctament.

####Rol 5: Dissenyador:

* Afegeix css i js al `base.html`. Afegeix els components bootstrap necessaris als templates per a que les pàgines segueixin una estètica coherent.

####Rol 6: Organitzador:

* Crea el projecte i el comparteix.
* Organitza el grup i dona suport a les incidències que puguin apareixer.

###S'avaluarà:

* Capacitat del grup per organitzar-se i assumir els diferents rols necessaris per a completar el projecte.
* Aplicació de les tècniques i patrons explicats a l'assignatura.

###Entregables:

* Codi font de la web autocomentat en un únic document format pdf on també s'incloguin les captures de pantalla de la web en funcionament.
* Opcional: Directe de la confecció de la web amb converses i visualització de l'evolució del codi.

---

#FpInfor #Daw #DawMp07 #DawMp07Uf02

---

###### Autor: daniel herrera 2015.12.17 10:58:44
###### Editat per: daniel herrera 2018.01.19 17:55:02
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
