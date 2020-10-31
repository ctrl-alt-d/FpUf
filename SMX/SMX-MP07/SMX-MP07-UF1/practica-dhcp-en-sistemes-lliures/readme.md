# Pràctica DHCP en Sistemes Lliures
## SMX-MP07-UF1 - Exercici de configuració de la xarxa (DNS i DHCP).
#### **Pràctica DHCP en Sistemes Lliures**
*Recomanació: 
- Pràctica per tractar el servei DHCP incloent balanceig de càrrega.
- Aquesta pràctica és força llarga i és per això que es aconsellable intercalar explicacions i entregues parcials de la mateixa.
- Fer-la en grups de 2 o 3 alumnes.*

Una empresa té un equip amb Ubuntu Server amb dos adaptadors de xarxa i s'ha comprat 2 més que faran funció de servidors DHCP. A l'empresa hi ha 25 equips de sobretaula (Ubuntu desktop), mes 5 portàtils (Ubuntu desktop). Dels 30 equips, 10 sobretaula i 3 portàtils pertanyen al departament de vendes i els altres 15 sobretaula i 2 portàtils al de producció. Volen que els 2 departaments estiguin en un àmbit diferent corresponent a dues subxarxes classe C.

Volen utilitzar els 2 Ubuntu Server nous com a servidors DHCP per a la xarxa de vendes per tal de tenir balanceig de càrrega i tolerància a fallides. 
Es vol que les configuracions de DNS i pasarel·la es donin automàticament per dhcp als clients. La ip corresponent al servidor DNS serà qualsevol equip de la xarxa de producció (no s'ha d'instal·lar el servei DNS!!!).

Els portàtils rebran una ip associada a la seva MAC. A més aquests portàtils no tindran associat Gateway per part del servidor DHCP.
Expliqueu detalladament (i amb les captures de pantalla) quin és el procediment d'instal·lació i configuració dels servidors DHCP de la xarxa corresponent a vendes. 
Configurar els clients de l'àmbit de vendes en entorn gràfic.
Fer les comprovacions que calgui per veure si funciona tot correctament des d'una màquina viatjant (portàtil) i després des d'una sobretaula.
Realitzar comprovacions al servidors per veure les adreces reservades, donades i els temps en què expiren.

Comprova, amb 3 o més clients, que es produeix el balanceig de càrrega corresponent. Força la “caiguda” del servidor primari DHCP i comprova les accions que es realitzen per part de l'altre servidor. Torna a “engegar” el servidor primari DHCP i comprova de nou les accions que es realizen.
Realitzar el document explicatiu de tot el procés que s'ha realitzat (amb les captures adients).

L'àmbit corresponent a producció no tindrà balanceig. Crea el rang d'assignacions que consideris oportú en un dels 2 servidors DHCP. Tots els clients hauran de tenir servidor DNS i pasarel·la assignada.
Fes tot el necessari per tal que els clients d'aquest nou àmbit rebin ip del servidor DHCP. Per fer-lo utilitza el Ubuntu Server amb 2 adaptadors de xarxa com a encaminador i com agent de retransmisió (dhcp relay agent).
Realitzar noves comprovacions al servidor DHCP per veure les adreces reservades, donades i els temps en què expiren.

Un dels portàtils està al matí en una xarxa i a la tarda en l'altra (en totes dues amb ips fixes). Fes que rebi ips correctament.

El dia que has acabat de configurar i implatar el dhcp arriba el cap de l'empresa amb un portàtil seu (amb Ubuntu Desktop). Aquesta persona té una altra empresa i el portàtil té una ip fixa configurada per a la xarxa d'aquella empresa (xarxa privada classe B). No vol sentir parlar d'haver de canviar configuracions de xarxa cada vegada que es desplaça d'una empresa a una altra. Sabem que a l'altra empresa hi ha un Servidor del qual coneixem les seves IP i MAC. Dona-li solució (i com sempre, documenta'l). Pots seguir aquest enllaç relacionat:  [http://ubuntuforums.org/showthread.php?t=124153](http://ubuntuforums.org/showthread.php?t=124153)


---

#FpInfor #Smx #SmxMp07 #SmxMp07Uf01

---

###### Autor: Juaky 2014.01.10 10:02:30
###### Editat per: Juaky 2014.01.10 10:02:30
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
