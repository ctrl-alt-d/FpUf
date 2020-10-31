# PHP - El tipus objecte.
## DAW-MP07-UF1 - Exercici de Desenvolupament web en entorn servidor.
[Exercici previ a realitzar](/DAW/DAW-MP07/DAW-MP07-UF1/php-els-tipus-de-variables-primitius/readme.md)

PHP és un llenguatge orientat a objectes. Un dels tipus de variables són les [variables de tipus objecte](http://php.net/manual/es/language.types.php)

En aquest exercici declararem una variable de tipus objecte. En concret instànciarem un objecte de la classe *DateTime*. Després invocarem un métode de la classe datetime. PHP utilitza la notació fletxa ( -> ) per a invocar mètodes:

    <?php
    $d = new DateTime();
    $tipus_de_d = gettype( $d );
    echo "La variable \$d 
          conté el valor " . $d->format( "d/m/Y") .
    	  " i és del tipus $tipus_de_d";
    ?>

 1. Executa el codi anterior.
 2. De quin tipus és la variable $d?
 3. Observa que l'operador de concatenació de cadenes en php és el punt ( . )
 4. Que retorna la invocació del mètode format de la classe datetime?
 5. Prova a modificar el codi per a intentar mostrar $d tal com ho feiem a [l'exercici anterior](/DAW/DAW-MP07/DAW-MP07-UF1/php-els-tipus-de-variables-primitius/readme.md). És a dir *echo "el valor de \$d és $d";* Ha funcionat? 
 6. Seria interessant, ara que sabem que la variable és de tipus objecte, conèixer de quina classe és aquell objecte. Això ho podem fer amb la funció *get_class()*. Una pista: *$classe_de_d = get_class( $d );*




---

#FpInfor #Daw #DawMp07 #DawMp07Uf01

* Resultats d'aprenentatge 2.g
* Continguts 2.4
---

###### Autor: daniel herrera 2013.09.28 19:11:01
###### Editat per: daniel herrera 2016.09.20 14:37:50
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
