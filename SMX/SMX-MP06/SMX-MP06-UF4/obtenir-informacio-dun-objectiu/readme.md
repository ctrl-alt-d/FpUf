# Obtenir informació d'un objectiu
## SMX-MP06-UF4 - Exercici de seguretat activa.
Informació a Internet
------------------------
A Internet les organitzacions exposen molta informació que després un atacant pot fer servir per iniciar un atac contra elles.

###WHOIS
Quan algú registra un domini a Internet ha de donar informació que li permeti demostrar que és seu. En aquests registres sovint s'hi pot trobar informació personal.

A Internet hi ha moltes Webs on buscar informació del domini: 

* [whois](http://whois.net)
* [nic.es](http://www.nic.es)
* [domini.cat](http://www.domini.cat)

També es pot obtenir aquesta informació fent servir la comanda de Linux *whois*

    ::bash
    $ whois iescendrassos.net

    Whois Server Version 2.0

    Domain names in the .com and .net domains can now be registered
    with many different competing registrars. Go to http://www.internic.net
    for detailed information.

       Domain Name: IESCENDRASSOS.NET
       Registrar: GODADDY.COM, LLC
       Whois Server: whois.godaddy.com
       Referral URL: http://registrar.godaddy.com
       Name Server: NS1.AFRAID.ORG
       ....

No tots els dominis ofereixen informació, la informació dels dominis pot ser bloquejades. Es pot trobar informació sobre bloqueig de dominis a [aquí](http://info.cdmon.com/index.php?page=buscador-whois&hl=esp)

DNS
----
Un altre lloc del que es pot obtenir informació sobre un domini és a través dels DNS. Els servidors DNS emmagatzemen tota la informació sobre tots els ordinadors accessibles a través del nom d'un domini concret. 

El més evident és fer una **transferència de zona**. Alguns DNS no estan ben configurats i permeten extreure tota la informació que contenen exposant a tothom tots els ordinadors del seu domini 

    ::bash
    $ dig AXFR iescendrassos.net

Però el més habitual és que no ho permetin i per tant cal trobar una nova forma d'atacar-los. 

Una de les característiques del DNS és que si fas una petició correcta dóna resultats, però si el que demanem no existeix no en dóna: 

    ::bash
    # dig www.iescendrassos.net +short
    2.139.163.19
    # dig patata.iescendrassos.net +short
    #

Això el fa un candidat ideal pels atacs de diccionari (amb l'avantatge de que la possible víctima ni se n'adonarà perquè les peticions es fan en el DNS que es tingui configurat i no en el del domini). Podem passar una llista de paraules i provar si són màquines del domini.

Hi ha molts programes que permeten automatitzar aquestes tasques: dnsenum, dnsmap, dnsrecon, dnstracer, dnswalk, fierce, ... 

    ::bash
    $ dnsenum --enum -f -r iescendrassos.net

Activitat
----------------
1. Trieu 5 dominis d'Internet a l'atzar. Tria els dominis diferents, .com, .net, .es , .cat

2. Quina informació podeu trobar d'aquests dominis ? Anoteu si podeu trobar email, noms de treballadors, telèfons, servidors dns, ...

3. Pot ser que us haguéu trobat dominis que no ofereixen informació. Per quin motiu creieu que alguns dominis bloquegen la informació?

4. Feu servir l'eina fierce (http://ha.ckers.org/fierce ) o alguna de les utilitzats vistes a classe (dnsenum, dnsmap, ...) per descobrir tants servidors com pugueu de cada un dels dominis de l'exercici 1

5. Feu el mateix en el domini de l'Institut Cendrassos (iescendrassos.net) i Xtec.cat. 


---

#FpInfor #Smx #SmxMp06 #SmxMp06Uf04

* Resultats d'aprenentatge 1.j
* Continguts 1.10
---

###### Autor: Xavier Sala 2014.01.25 23:00:13
###### Editat per: daniel herrera 2014.01.26 13:21:48
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
