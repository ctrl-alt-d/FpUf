# PHP - Els tipus de variables primitius.
## DAW-MP07-UF1 - Exercici de Desenvolupament web en entorn servidor.
PHP és un llenguatge [dinàmicament tipat](http://ca.wikipedia.org/wiki/Llenguatge_de_programaci%C3%B3#Tipus_est.C3.A0tics_versus_din.C3.A0mics). Els tipus que treballarem en aquest exercici són: enters, booleans, coma flotant, cadenes de caracters i objectes.

Observa ara aquest tall de codi:

    <?php
    $i = 12;
    $tipus_de_i = gettype( $i );
    echo "La variable \$i 
          conté el valor $i 
    	  i és del tipus $tipus_de_i";
    ?>

 1. Executa aquest codi.
 2. Observa el comportament de les cometes màgiques de PHP, hem posat *$i* dins la cadena i ens ha mostrat el seu valor.
 3. Explica perquè hem posat la barra invertida davant del símbol $.
 4. Digues de quin tipus és la variable $i.
 5. Digues per a que serveix la funció gettype.
 6. Exten el codi per tal de, a més de la variable *$i*, treballar igual amb variables de tipus: coma flotant, booleana i cadena de caracters. 
 7. Modifica el codi per saber de quin tipus és el valor que retorna gettype.

Aquest exercici continua amb un [exercici amb variables de tipus classe](/DAW/DAW-MP07/DAW-MP07-UF1/php-el-tipus-objecte/readme.md)


---

#FpInfor #Daw #DawMp07 #DawMp07Uf01

* Resultats d'aprenentatge 2.g
* Continguts 2.4
---

###### Autor: daniel herrera 2013.09.28 18:54:53
###### Editat per: daniel herrera 2015.09.25 17:20:38
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
