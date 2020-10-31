# PHP - Arrays simples
## DAW-MP07-UF1 - Exercici de Desenvolupament web en entorn servidor.
[Un array a PHP és realment un mapa ordenat](http://www.php.net/manual/es/language.types.array.php). Per aquest motiu podem tractar l'array indexant'el numèricament tal i com fem en altres llenguatges. En aquest exercici crearem un array, afegirem valors, en treurem i el pintarem:


```php
<?php
// creo un array amb 3 elements
$a = array( 5,7,11);
print_r( $a );
echo "<br>";

//afegeixo més elements a l'array
$a[] = 13;  
$a[] = 17;
print_r( $a );
echo "<br>";

//encara un altre
array_push ($a, 23);
print_r( $a );
echo "<br>";

//pinto elements de l'array
echo "El valor de del tercer element de l'array és " . $a[2];
echo "<br>";

unset($a[0]); 
unset($a[1]); // el valor 7 seguia a la possició 1
print_r( $a );
echo "<br>";
?>

```
 1. Quina és la instrucció a PHP per a crear un array?
 2. Es pot crear un array buit a PHP ó sempre s'hi han de posar valors a la creació?
 3. Si li prenem el tipus a l'array amb la funció *gettype()*, quin tipus obtenim?
 4. Com puc fer per afegir un element a l'array a partir de la darrera posició coneguda? Esmenta dues maneres diferents.
 5. Com s'accedeix a un element d'un array?
 6. Com s'esborra un element d'un array?
 7. Fixat que el valor 7, emmagatzemat a la posició $a[1], segueix exactament a la mateixa posició després d'esborrar $a[0]. Això no seria així en altres llenguatges de programació, però a PHP els arrays, realment, són mapes ordenats. Farem el següent exercici per comprendre aquest concepte.  

Un cop completat aquest exercici et recomano els següents:

 * [PHP - Recorrer un array simple](/DAW/DAW-MP07/DAW-MP07-UF1/php-recorre-un-array-simple/readme.md)


---

#FpInfor #Daw #DawMp07 #DawMp07Uf01

* Resultats d'aprenentatge 3.c 2.g
* Continguts 3.3 2.4
---

###### Autor: daniel herrera 2013.09.28 19:29:03
###### Editat per: Sergi Coll 2016.10.07 13:27:18
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
