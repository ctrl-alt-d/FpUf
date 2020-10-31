# PHP - Concatenar elements d'un array
## DAW-MP07-UF1 - Exercici de Desenvolupament web en entorn servidor.
Donat l'array $a:

    <?php
    $a1 = array( 'A','B','C','D');
    $a2 = array( 1,2,3,4,5,6,7);
    $a3 = array( 'Boli', 'Goma', 'Llapis', 'Escurça');
    $a = array( 'Lletres' => $a1, 'Números' => $a2, 'Materials Oficina' => $a3 );

Fes els bucles necessaris per mostrar pel navegador la següent informació:

* Lletres: A, B, C, D
* Números: 1, 2, 3, 4, 5, 6, 7
* Materials Oficina: Boli, Goma, Llapis, Escurça
    
Aquest exercici té dues complexitats:

 1. Cal un bucle intern (nested loop), això està treballat a l'exercici [PHP - Recorrer array](/DAW/DAW-MP07/DAW-MP07-UF1/php-recorrer-array-mapa/readme.md)
 2. Cal un **separador** entre elements, el separador no ha d'aparèixer davant del primer element i tampoc darrera de l'últim. A sota trobaràs una pista de com fer-ho:

El separador:

    <?php
    $a = array( 1,1,2,3,5,8,13);
    $separador = "";
    foreach( $a as $i ) {
        echo $separador . $i;  //concatenem el separador amb l'element
        $separador = ", ";
    }





---

#FpInfor #Daw #DawMp07 #DawMp07Uf01

* Resultats d'aprenentatge 3.b
* Continguts 3.2
---

###### Autor: daniel herrera 2013.10.01 09:06:27
###### Editat per: Sergi Coll 2016.10.07 13:31:02
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
