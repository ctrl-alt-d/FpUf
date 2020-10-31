# Atacs d'home al mig moderns en xarxes LAN
## SMX-MP06-UF4 - Exercici de seguretat activa.
Fer un atac MITM
==========================
Hi ha moltes eines que permeten fer aquest atac però entre les més usades hi ha: ettercap (en sistemes Unix), arpspoof, bettercap, MITMf o Cain & Abel (en Windows)

Ettercap ha estat el programa més usat durant molts anys però la evolució de les connexions d’Internet cap a SSL, etc… ha fet que cada vegada calguin més eines per poder-lo usar amb connexions a Internet (sslstrip, ferret-ng ....) 

Això ha provocat que hagin aparegut eines que integren els atac que ja feia ettercap amb les altres eines que s’han convertit amb bàsiques i a més disposen de plugins per incrementar-ne les capacitats.

D’entre aquestes eines en destaquen Bettercap i MITMf

Amb MITMf, per exemple, es poden canviar les imatges de les webs, injectar Javascript o HTML a les webs o fins i tot afegir troians als executables que es descarrega la víctima.

![atacs](https://raw.githubusercontent.com/utrescu/utrescu.github.io/master/images/mitmf-atac.png "Girar")

Activitat
--------------------------

### Instal·lar MITMf

1. En una màquina virtual amb Kali amb adaptador pont instal·leu-hi MITMf. Per fer-ho cal seguir les instruccions de la seva web (Enllaç)

2. Preparar la víctima
    . Inicieu una màquina virtual amb adaptador pont que farà de víctima. 
    . Feu ping a una altra màquina del sistema (el router per exemple)
    . Mostreu la taula ARP de la màquina víctima

### Canviar les imatges

3. En la màquina virtual atacant afegiu unes quantes imatges en un directori
4. Inicieu un atac entre el router i la màquina víctima que li canvii les imatges de les pàgines web que visita la víctima
5 .Navegueu en unes quantes màquines i comproveu que les imatges de les webs es canvien per les de l’atacant

### Girar les imatges 180º

6. Com es fa per girar les imatges de les webs del revés?
7. Comproveu que funciona

### Afegir contingut a les pàgines

8. L’atac ‘inject’ permet afegir contingut HTML a totes les pàgines que visita la víctima. Investigueu com es pot fer per fer que en totes les pàgines que visita la víctima aparegui el vostre nom (`<h1>Nom</h1>`) o la imatge que vosaltres vulgueu
9. Feu-ho

---

#FpInfor #Smx #SmxMp06 #SmxMp06Uf04

---

###### Autor: Xavier Sala 2017.03.02 10:10:34
###### Editat per: Xavier Sala 2017.03.02 10:29:45
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
