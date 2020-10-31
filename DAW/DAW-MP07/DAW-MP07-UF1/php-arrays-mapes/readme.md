# PHP - Arrays (mapes)
## DAW-MP07-UF1 - Exercici de Desenvolupament web en entorn servidor.
Recomenat realitzar abans [exercici arrays simples](/DAW/DAW-MP07/DAW-MP07-UF1/php-arrays-simples/readme.md).

[Un array a PHP és realment un mapa ordenat](http://www.php.net/manual/es/language.types.array.php) i això és el que ara treballarem. Observa i executa aquest tall de codi:

```php
<?php
$m = array( "Alibaba" => "y los quarenta ladrones",
	        "Harry Potter" => "y el cáliz de fuego");

//afegim un element més
$m["Aníbal"] = "El caníbal";

//mostrem *tot* el contingut de l'array
print_r($m);
print( "<br>");

//Accedim a un element (mostrem només un element)
print( $m["Alibaba"]);
print( "<br>");

//Esborrem un element
unset( $m["Harry Potter"]);

//mostrem *tot* el contingut de l'array
print_r($m);
print( "<br>");

?>
```

 1. Després de l'execució d'aquest codi, quines claus conté l'array?
 2. Quin valor li correspon a cada clau?
 3. Com es fa per afegir un nou parell clau-valor a l'array?
 4. Com es fa per accedir a un valor mitjançant la seva clau?
 5. Com s'esborra una entrada clau-valor?

Exercici a realitzar després d'aquest:

 * [Recorrer array (mapa)](/DAW/DAW-MP07/DAW-MP07-UF1/php-recorrer-array-mapa/readme.md)

---

#FpInfor #Daw #DawMp07 #DawMp07Uf01

* Resultats d'aprenentatge 3.c 2.g
* Continguts 3.3 2.4
---

###### Autor: daniel herrera 2013.09.28 19:50:18
###### Editat per: daniel herrera 2016.09.26 15:05:13
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
