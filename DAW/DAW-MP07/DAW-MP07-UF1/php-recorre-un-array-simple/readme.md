# PHP - Recorrer un array simple
## DAW-MP07-UF1 - Exercici de Desenvolupament web en entorn servidor.
Els següents dos talls de codi fan exactament el mateix:

Tall de codi 1, bucle *foreach*:

    <?php
    $a = array( 1,1,2,3,5,8,13);
    foreach( $a as $v ) {
        echo $v . " ";
    }
    ?>

Tall de codi 2, blucle *for*:    

    <?php
    $a = array( 1,1,2,3,5,8,13);
    for( $i = 0; $i < count( $a ); $i++ ) {
        echo $a[$i] . " ";
    }
    ?>

El primer tall de codi utilitza menys artefactes que el segon:

 * No compta quants elements hi ha a l'array
 * No incrementa cap variable
 * No comprova si encara estem dins de l'array

Exercici:

 1. Això fa que es llegeixi molt millor. Explica per què a l'enginyeria del software és tant important fer que els programes siguin mantenibles.
 2. Acostuma't, a partir d'ara, a fer servir el bucle foreach quan sigui possible.

---

#FpInfor #Daw #DawMp07 #DawMp07Uf01

* Resultats d'aprenentatge 3.b
* Continguts 3.2
---

###### Autor: daniel herrera 2013.09.28 19:56:02
###### Editat per: daniel herrera 2015.09.30 16:28:58
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
