# Atacs d'home al mig en LAN
## SMX-MP06-UF4 - Exercici de seguretat activa.
Objectius: Descobrir els problemes de seguretat inherents a la capa 2 de les LAN

ARP Spoofing
============================
L'ARP Spoofing es una tècnica de xarxes LAN que aconsegueix fer un atac conegut com de l'“Home al mig” (MITM). Consisteix en enganyar a les màquines implicades en una comunicació per fer passar el trànsit que s’envien entre elles per la de l'atacant.

![Atac](https://raw.githubusercontent.com/utrescu/utrescu.github.io/master/images/mitm.png)

Fer un atac MITM
-----------------------
Hi ha moltes eines que permeten fer aquest atac però entre les més usades hi ha: ettercap, **arpspoof**, **bettercap**, **MITMf** o **Cain & Abel** (en Windows)

### Ettercap

Ettercap permet realitzar l'atac fent servir diferents sistemes (entorn gràfic, consola, etc...). Per enverinar la comunicació entre dos hosts (en l’exemple 192.168.5.3 i 192.168.5.1) en tenim prou amb executar la comanda següent:

    # ettercap -T -M arp /192.168.5.3/ /192.168.5.1/

Amb algunes versions de ettercap cal activar IP forward perquè el trànsit flueixi ...

    # echo 1 > /proc/sys/net/ipv4/ip_forward

Iniciant un sniffer podrem veure tot el trànsit entre les dues màquines

> Pot ser que en funció de la versió que es tingui la comanda anterior doni un error com aquest:
> 
>     Incorrect number of token (///) in TARGET !!		
> Això vol dir que tenim activada la opció de IPv6 i per tant el format és lleugerament diferent (en comptes de fer servir dues barres se n’han de posar tres):
> 	
>     # ettercap -T -M arp /192.168.5.3// /192.168.5.1//
> 

Algunes eines com bettercap o MITMf permeten fer atacs més “moderns” com canviar imatges o contingut, afegir contingut en el trànsit, falsificar connexions SSL,  etc...

Evitar o detectar l'atac
---------------------------

Tenim diferents opcions per intentat detectar aquest tipus d'atacs. 

En sistemes Windows hi ha diferents eines per detectar i bloquejar aquests atacs. Dos programes que es poden usar són Patriot NG o Marmita

![Detectar en Windows](https://raw.githubusercontent.com/utrescu/utrescu.github.io/master/images/mitm-detect.png)

Alguns antivirus també detecten els atacs d'aquest tipus

En Linux en destaquen Arpwatch (per monitoritzar els canvis en les adreces) i ArpON (per evitar aquests atacs)

### ARPWatch

ARPWatch és un dimoni del sistema que es dedica a monitoritzar les màquines que troba en la xarxa de manera que un cop recollides les dades pot detectar qualsevol canvi en la correspondència ARP-IP que s'hi produeixi

D'aquesta forma es poden detectar els atacs al protocol ARP ja que es produiran diferents canvis en la taula ARP

Un cop es produeix una incidència pot enviar un correu electrònic a l'administrador perquè n'estigui assabentat i hi posi remei

### ArpON

ArpON és un servei del sistema que està pensat per evitar els efectes dels atacs al protocol ARP. Per fer-ho porta un control de les adreces IP i MAC de les màquines.

Al rebre un atac ARP, ARPOn no se’n fia de les respostes que arribin sense haver estat demanades (per això les marca com a dubtoses) i quan li fan falta intenta endevinar pels seus mitjans quina és la resposta correcta.

Pot funcionar amb adreces estàtiques (SARPI), dinàmiques (DARPI). Les darreres versions afegeixen un nou sistema híbrid (HARPI).

Tasca
=======================

Atacs d’home al mig
----------------------------

Enverinar el trànsit entre dues màquines

1. Inicieu una màquina virtual amb adaptador pont i feu ping a una altra màquina del sistema (el router per exemple)
2. Comproveu la taula ARP de la màquina virtual
3. Des del vostre host real enverineu el trànsit entre la màquina virtual i l’altra
4. Mentre l’atac s’està fent comproveu que la taula ARP ha canviat

Detecció dels atacs des de Windows
----------------------------------------

5. Inicieu una màquina virtual amb adaptador pont que estigui en Windows 
6. instal·leu-hi algun programa de detecció d’atacs
7. Ataqueu-la i comproveu si l’atac ha estat detectat

Detecció dels atacs des de Linux (part voluntària)
----------------------------------------------------
8. En una màquina virtual amb Linux feu servir ArpWatch o ARPON (un dels dos)
9. Comenceu un atac contra la màquina virtual i comproveu que:
    - Si feu servir ArpWatch comproveu que rebeu el correu electrònic amb l’avís
    - Si feu servir ARPON comproveu que l’adreça MAC es restaura

Si voleu que s’enviin els correus d'ArpWatch a fora recordeu que no podeu fer servir correus de Google o Microsoft perquè els rebutjaran perquè no esteu en cap servidor “real”. Per això van molt bé els d’un sol ús com [mailinator](https://www.mailinator.com/)

---

#FpInfor #Smx #SmxMp06 #SmxMp06Uf04

---

###### Autor: Xavier Sala 2017.03.02 09:17:55
###### Editat per: Xavier Sala 2017.03.02 14:03:38
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
