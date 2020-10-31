# PHP - POST vs GET
## DAW-MP07-UF1 - Exercici de Desenvolupament web en entorn servidor.
Quan un formulari envia dades ho pot fer mitjançant dos mètodes diferents: El POST i el GET. La diferència principal, segons [w3scools](http://www.w3schools.com/tags/ref_httpmethods.asp) eś:

 * GET - Requests data from a specified resource (*"Les dades es prenen des del recurs especificat"*)
 * POST - Submits data to be processed to a specified resource (*"Les dades s'envien per a ser processades al recurs especificat"*)

Això comporta unes consideracions a tenir en compte:

Some other notes on GET requests:

 * GET requests can be cached
 * GET requests remain in the browser history
 * GET requests can be bookmarked
 * GET requests should never be used when dealing with sensitive data
 * GET requests have length restrictions
 * GET requests should be used only to retrieve data

Some other notes on POST requests:

 * POST requests are never cached
 * POST requests do not remain in the browser history
 * POST requests cannot be bookmarked
 * POST requests have no restrictions on data length

Exercici:

 1. A l'exercici [PHP - Treball senzill amb formularis](/DAW/DAW-MP07/DAW-MP07-UF1/php-treball-senzill-amb-formularis/readme.md) substitueix el mètode POST per el GET i investiga que passa.
 2. Un cop fetes varies proves, passa a afinar el codi que processa les dades canviat $_REQUEST per $_GET o $_POST segons el cas.

Solucions:

 * [Solució 1](https://docs.google.com/a/xtec.cat/document/d/1Wi9sCQEaF9QqK25mG0J9Q62q-V80vXuzoIkPbtUlUrw/edit?usp=sharing)


---

#FpInfor #Daw #DawMp07 #DawMp07Uf01

* Resultats d'aprenentatge 3.f
* Continguts 3.6
---

###### Autor: daniel herrera 2013.09.29 13:38:41
###### Editat per: daniel herrera 2015.10.07 15:42:05
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
