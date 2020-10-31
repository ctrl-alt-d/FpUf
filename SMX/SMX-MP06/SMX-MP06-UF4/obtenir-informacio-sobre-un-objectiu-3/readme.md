# Obtenir informació sobre un objectiu 3
## SMX-MP06-UF4 - Exercici de seguretat activa.
Objectius: Veure que es pot obtenir informació remota dels sistemes

Obtenir informació
===========================

Un dels problemes que ha portat Internet és que es pot aconseguir informació sobre una possible víctima des de qualsevol cosa. Fins i tot de les coses que d’entrada poden semblar menys útils com les adreces IP, els navegadors o els documents que han penjat

Informació de les IP
--------------------------
Quan algú es connecta a Internet rep una adreça IP única. De les adreces IP se’n pot obtenir molta informació … 

Localització de la IP en el món

- [http://aruljohn.com/ip/](http://aruljohn.com/ip/)
- [https://iplookup.flagfox.net/](https://iplookup.flagfox.net/)
- [http://www.ip2location.com/demo](http://www.ip2location.com/demo)  *

Saber quins hostings hi ha en el mateix lloc web

- [http://www.yougetsignal.com/tools/web-sites-on-web-server/](http://www.yougetsignal.com/tools/web-sites-on-web-server/)
- [http://www.ip-address.org/reverse-lookup/reverse-ip.php](http://www.ip-address.org/reverse-lookup/reverse-ip.php)
- [http://www.ip2hosts.com/](http://www.ip2hosts.com/)

fingerprint  dels navegadors
-------------------------------
No sempre els atacs van dirigits als serveis, actualment s’estan produint atacs contra programes. En aquest sentit una de les formes d’obtenir informació és fer que un client visiti una pàgina web tunejada per obtenir-ne tot el que els navegadors diuen de l'usuari i el seu sistema ...

- [http://www.uniquemachine.org/](http://www.uniquemachine.org/) 
- [https://amiunique.org/](https://amiunique.org/) 
- [https://panopticlick.eff.org/](https://panopticlick.eff.org/) 

Informació dels documents
-----------------------------
FOCA (Fingerprinting Organizations with Collected Archives) és una eina de Windows que es fa servir entre altres coses per trobar metadades que està emmagatzemada en documents que les empreses publiquen a la web. 

Pot analitzar documents de diferents tipus que van des de Office, OpenOffice, PDF, o fins i tot imatges. 

Pot cercar els documents en diferents cercadors, Google, Bing, Exalead, de forma més o menys automàtica.  Dels documents n’extreu tota una sèrie de dades que permet identificar informació de la xarxa.

![FOCA](https://raw.githubusercontent.com/utrescu/utrescu.github.io/master/images/foca.png)

Es pot trobar a [https://www.elevenpaths.com/labstools/foca/index.html#](https://www.elevenpaths.com/labstools/foca/index.html#) 

Activitat
=====================

Informació de l’adreça IP
-------------------------------

1. Localitzeu en quin lloc hi ha el servei de www.cendrassos.net
    1. Proveu-ho en diferents llocs per veure si la informació és diferent
    2. Quin dels serveis us sembla més detallat?
2. Feu el mateix en tres dominis diferents (L’objectiu és aconseguir trobar llocs compartits)

3. Localitzeu la IP de 10 llocs web que conegueu i després localitzeu en quin lloc del món estan situats

Informació del navegador
-------------------------
4. Aneu amb un navegador a les webs de fingerprinting. 
    1. Quina informació tenen?
5. Feu el mateix amb un altre navegador i comproveu si detecta el mateix.

Informació dels documents
-------------------------------------

6. A partir del domini d’una empresa de la comarca i el del nostre centre, iescendrassos.net, feu servir FOCA per comprovar si els documents que tenen penjats en les seves webs tenen "metadades"
7. Quina informació hi heu descobert sobre els usuaris?
8. N'heu pogut deduir alguna cosa més? (Sistema operatiu, hosting, etc ... )

---

#FpInfor #Smx #SmxMp06 #SmxMp06Uf04

---

###### Autor: Xavier Sala 2017.02.15 15:23:00
###### Editat per: Xavier Sala 2018.01.07 19:20:56
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
