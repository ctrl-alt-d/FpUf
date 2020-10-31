# PHP - Treball amb POST
## DAW-MP07-UF1 - Exercici de Desenvolupament web en entorn servidor.
En aquest exercici modificarem el comportament del programa de l'exercici [/DAW/DAW-MP07/DAW-MP07-UF1/php-treball-senzill-amb-formularis/readme.md](/DAW/DAW-MP07/DAW-MP07-UF1/php-treball-senzill-amb-formularis/readme.md). Es tracta d'unificar les dues pàgines: **pinta_formulari.php** i **processa_dades.php** en una única pàgina **formulari.php**. 

Desenvolupament de l'exercici:

La pàgina **formulari.php** detectarà si li estan fent un POST, si és el cas processarà les dades que li arriben. Si no és el cas, no és un POST, llavors, simplement, mostrarà el formulari:

    <?php
    if($_SERVER['REQUEST_METHOD'] == 'POST') {
       //Processar les dades
    } else {
       //Pintar el formulari
    }
    
    





---

#FpInfor #Daw #DawMp07 #DawMp07Uf01

* Resultats d'aprenentatge 3.f
* Continguts 3.6
---

###### Autor: daniel herrera 2013.09.30 13:28:17
###### Editat per: daniel herrera 2013.10.29 13:32:26
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
