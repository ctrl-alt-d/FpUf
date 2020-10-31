# PHP - Funcions i procediments
## DAW-MP07-UF1 - Exercici de Desenvolupament web en entorn servidor.
PHP suporta el model orientat a objecte, però també un model modular basat en funcions. 

Podem declarar les funcions a la pròpia pàgina PHP o bé en una altre pàgina PHP i incloure-la a la nostre pàgina.

 1. Fes una funció que, passat un número, ens retorni si aquest número és parell o senar.
 2. Posa la funció en una pàgina PHP a banda anomenada *funcions.php*, fes un include d'aquesta segona pàgina a la principal.

Exemple de funció:

```php
<?php
function es_multiple_de_3( $numero ) {
    return ($numero % 3 == 0);
}
?>
... codi html ...
<?php
   ...
   if ( es_multiple_de_3($i) ) {
      echo "$i és multiple de 3";
   } else {
      echo "$i NO és multiple de 3";
   }
   ...
```
Bibliografia:

 * [Funcions, documentació oficial PHP](http://php.net/manual/es/language.functions.php)
 * [Include, documentació ficial PHP](http://php.net/manual/es/function.include.php)
 
 

---

#FpInfor #Daw #DawMp07 #DawMp07Uf01

* Resultats d'aprenentatge 3.d
* Continguts 3.4
---

###### Autor: daniel herrera 2013.09.29 13:17:44
###### Editat per: daniel herrera 2013.11.01 16:48:59
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
