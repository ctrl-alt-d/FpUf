# Generar el mapa de xarxa
## SMX-MP06-UF4 - Exercici de seguretat activa.
Obtenir informació tècnica
----------------------------------
Al cercar informació sobre un determinat objectiu una de les parts més importants és determinar quins serveis, programes i sistemes esta utilitzant la víctima. Els atacants fan servir aquesta informació per generar el mapa de la xarxa

En xarxes locals una de les formes de detectar equips és fer servir netdiscover

![NetDiscover](https://github.com/utrescu/utrescu.github.io/blob/master/images/netdiscover.png?raw=true "netdiscover")

Una vegada s’han trobat els diferents hosts interessa obtenir informació detallada sobre ells que posteriorment es podrà usar per cercar-hi vulnerabilitats:

* Sistemes operatius
* Versions dels servidors i programes

Molta d’aquesta informació es pot aconseguir fent servir un escànner de ports. Possiblement l’escànner de ports més popular del món és nmap

![nmap](https://raw.githubusercontent.com/utrescu/utrescu.github.io/master/images/nmap.png "nmap")

Nmap es distribueix amb un entorn gràfic anomenat ZenMap que li permet  mostrar la informació d’una forma més “tractable”

Activitat
-------------------

### netdiscover

Netdiscover és una eina de Linux que permet detectar les màquines que estan connectades o de les que arriba informació en la màquina que l’executa

1. Feu servir netdiscover per detectar les màquines que hi ha en la vostra xarxa local (si ho feu amb una màquina virtual poseu l’adaptador de xarxa en ‘bridget’)

### Nmap

1. Nmap permet veure els serveis que estan actius en un host determinat

2. Feu servir nmap per detectar els serveis que estan actius en la vostra xarxa. 
Localitzeu les versions i els sistemes operatius dels serveis

3. Feu la mateixa recerca amb ZenMap per veure les capacitats gràfiques que ofereix a nmap
    - Quin és el servei més usat en la vostra xarxa? 
    - Quins servidors web hi ha? Intenteu connectar-hi per veure que hi descobriu
    - Detecció dels punts de sortida de la xarxa

4. Descobriu per quines xarxes passeu per sortir a Internet
    - Quines xarxes privades heu descobert que hi ha en el centre? Com ho podeu fer per trobar-ne més?

---

#FpInfor #Smx #SmxMp06 #SmxMp06Uf04

---

###### Autor: Xavier Sala 2017.02.06 10:12:06
###### Editat per: Xavier Sala 2017.02.06 10:12:06
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
