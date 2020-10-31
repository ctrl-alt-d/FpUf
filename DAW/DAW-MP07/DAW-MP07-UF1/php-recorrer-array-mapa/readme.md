# PHP - Recorrer array ( mapa )
## DAW-MP07-UF1 - Exercici de Desenvolupament web en entorn servidor.
Tal com hem aprés a l'exercici [PHP - Arrays (mapes)](/DAW/DAW-MP07/DAW-MP07-UF1/php-arrays-mapes/readme.md) [un array en realitat és un mapa ordenat per les claus](http://www.php.net/manual/es/language.types.array.php).

Com podem fer per recorrer un array obtenint tant les claus com els valors? Doncs de la següent manera:


```php
<?php
$m = array( "Alibaba" => "y los quarenta ladrones",
            "Harry Potter" => "y el cáliz de fuego");

//afegim un element més
$m["Aníbal"] = "El caníbal";

//pitem el contingut de l'array
foreach( $m as $clau=>$valor) {
	echo "El valor de [$clau] és [$valor] <br>";
}
```

Aquest exercici és complicat!! Fes un array on les claus siguin noms d'esports i els valors siguin, a la seva vegada, un array de jugadors d'aquell esport. Després fes que es apareguin al navegador. T'ajudo amb dos esports i el amb el bucle extern per a pintar-los:

```php
<?php
$jugadors_de_lacrosse = array( "Billy Bitter", "Chris Bocklet", "Jeremy Boltus" );
$jugadors_de_pilota_vasca = array( "Iñaki" );
$esports = array();
$esports["Lacrosse"] = $jugadors_de_lacrosse;
$esports["Pilota Vasca"] = $jugadors_de_pilota_vasca;

foreach( $esports as $esport => $jugadors ) {
	echo "Els meu jugadors preferits de $esport són ";
	//aquí va un altre foreach que et deixo per a tu!!
    //foreach( $jugadors as ...
    echo "<br>";
}
```

---

#FpInfor #Daw #DawMp07 #DawMp07Uf01

* Resultats d'aprenentatge 3.b
* Continguts 2.3
---

###### Autor: daniel herrera 2013.09.28 20:11:20
###### Editat per: daniel herrera 2017.09.25 13:05:19
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
