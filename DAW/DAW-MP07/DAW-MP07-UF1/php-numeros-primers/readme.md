# PHP - Números primers
## DAW-MP07-UF1 - Exercici de Desenvolupament web en entorn servidor.
Fes un formulari que reculli un número, l'anomenarem **n**.

El formulari envia el número (millor a una nova pàgina) i ens informarà si aquell número és primer o no. En cas de no ser primer ens mostrarà tots els seus divisors. 

Exemple per un número primer:

* El número 31 és un número primer.

Exemple resultat per un número no primer:

* El número 24 no és un número primer i els seus divisors són l'1, el 2, el 3, el 4, el 6, el 8, el 12 i ell mateix.

**Ampliació**

Fes que la pàgina php s'envii el número a ella mateixa. Si `'numero'` no apareix a `$_REQUEST` llavors mostra formulari, en cas contrari mostre dades.


**Solució**

```php
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
<meta http-equiv="Content-Type" content="text/html; charset=UTF-8">

<title>Exemple de formulari</title>

</head>

<body>

<div style="margin: 30px 10%;">
<h3>Números primers</h3>
<?php

    /* ----- Controls de paràmetres -----*/
    
    if (!array_key_exists("numero", $_REQUEST) ) {
        die( "No he rebut el número" );
    }
    
    $numero_txt = $_REQUEST["numero"];
    
    if (!is_numeric($numero_txt) ) {
        die( "Cal entrar un número, '$u' no és un número.");
    }
    
    $numero = intval( $numero_txt );
    
    if ($numero <=1 ) {
        die("Cal posar un número superior a 1");
    }
    
    /* ------ Busco els divisors -------- */
    $divisors = array();
    
    for ( $i=1; $i<=$numero; $i++ ) {
        if ($numero % $i == 0) {
            $divisors[]=$i;
        }
    }
    
    $es_primer = (count( $divisors ) == 2);

    /* ------- Mostrar resultats --------- */
    if ($es_primer) {
        echo "El número $numero és primer";
    }else{
        echo "El número $numero no és primer i els seus divisors són: ";
        $separador = "";
        foreach( $divisors as $d ) {
            echo "$separador $d";
            $separador = ",";
        }
    }
?>
</div>
</body>
</html>
```

---

#FpInfor #Daw #DawMp07 #DawMp07Uf01

* Resultats d'aprenentatge 3.a 3.e
* Continguts 3.1 3.5
---

###### Autor: daniel herrera 2013.10.14 13:08:54
###### Editat per: daniel herrera 2017.10.05 14:13:52
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
