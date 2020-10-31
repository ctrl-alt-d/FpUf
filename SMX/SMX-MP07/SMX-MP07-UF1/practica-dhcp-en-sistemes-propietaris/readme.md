# Pràctica DHCP en Sistemes Propietaris
## SMX-MP07-UF1 - Exercici de configuració de la xarxa (DNS i DHCP).
#### **Pràctica DHCP en Sistemes Propietaris**

*Recomanació: 
- Aquesta pràctica és força llarga i és per això que es aconsellable intercalar explicacions i entregues parcials de la mateixa.
- Fer-la en grups de 2 o 3 alumnes.*

Una empresa té un Windows Server 2003 amb dos adaptadors de xarxa i s'ha comprat un servidor amb Windows Server 2008. A l'empresa hi ha 25 equips de sobretaula (amb Windows), mes 5 portàtils (Ubuntu). Dels 30 equips, 10 amb Windows i 3 portàtils pertanyen al departament de vendes i els altres 15 i 2 portàtils al de producció. 
Volen que els 2 departaments estiguin en un àmbit diferent corresponent a dues subxarxes classe C i que hi hagi comunicació entre ambdues fent servir el 2003 com a router (es necessitarà que faci funció de DHCP Relay Agent).

Volen utilitzar el servidor 2008 com a DHCP per donar ip's a les dues subxarxes. Hi ha un servidor DNS en l'àmbit en el qual no està el servidor DHCP. Es vol que aquestes dues configuracions (DNS i pasarel·la) es donin automàticament per dhcp als clients. Nota: No cal instal·lar cap DNS, només necessitem la seva ip per donar al clients dhcp.
Els 5 portàtils tindran una ip associada a la seva MAC. A més, aquests portàtils no tindran associat Servidor de DNS ni Gateway per part del servidor DHCP (això significa que no s'enviarà cap gateway ni adreça DNS a aquestes màquines).

Expliqueu detalladament (i amb les captures de pantalla) quin és el procediment d'instal·lació i configuració del servidor DHCP de l'àmbit corresponent a vendes.
Configurar els clients de l'àmbit de vendes en entorn gràfic. Arribat a aquest punt, decideixen afegir un equip amb Windows en aquest àmbit. Fes-lo des de l'entorn de comandes amb "netsh".
Fer les comprovacions que calgui per veure si funciona tot correctament des d'una màquina portàtil i després des d'una altra de sobretaula.
Realitzar comprovacions al servidor per veure les adreces reservades, donades i els temps en què expiren.
Realitzar el document explicatiu de tot el procés que s'ha realitzat (amb les captures adients).

Des de línia de comandes (amb "netsh") crea l'àmbit corresponent a producció al servidor DHCP. Crea el rang d'assignacions i reserves que consideris oportú. Crea també un rang d'exclusions (el que vulguis). Tots els clients hauran de tenir servidor DNS i pasarel·la assignada.
Fes tot el necessari per tal que els clients d'aquest nou àmbit rebin ip del servidor DHCP.
Realitzar noves comprovacions al servidor per veure les adreces reservades, donades i els temps en què expiren.
Comprova també els logs del servidor DHCP.

Monitoreu el trànsit que genera el servidor DHCP utilitzant Wireshark (paquets DHCPDISCOVER, DHCPOFFER, DHCPREQUEST, DHCPACK).
Ara que està tot funcionant realitza un esquema (com a mena de mapa lògic) de com queda configurat.
El dia que has acabat de configurar i implantar el dhcp arriba el cap de l'empresa amb un portàtil seu (amb Windows). Aquesta persona té una altra empresa i el portàtil té una ip fixa configurada per a la xarxa d'aquella empresa. No vol sentir parlar d'haver de canviar configuracions de xarxa cada vegada que es desplaça d'una empresa a una altra. Dona-li solució (amb ip alternativa).

Al DHCP també apareix el concepte de “Superàmbit”. Cerca informació al respecte i afegeix un resum de per a què pot servir.

---

#FpInfor #Smx #SmxMp07 #SmxMp07Uf01

---

###### Autor: Juaky 2013.10.09 16:54:28
###### Editat per: Juaky 2013.10.14 08:17:28
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
