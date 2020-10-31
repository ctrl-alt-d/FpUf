# PHP - El bucle for i la instrucció if
## DAW-MP07-UF1 - Exercici de Desenvolupament web en entorn servidor.
Exercici:

Primera part:

Fes un formulari que demani una frase ('laMevaFrase') i un número ('elMeuNumero').
El formulari enviarà les dades a una nova pàgina php que farà el següent:

 1. Informi com ha rebut les dades: via POST o via GET
 2. Pinti 'elMeuNumero' de vegades la frase 'laMevaFrase'

Segona part:

 1. Modifica el programa per tal que sigui una única pàgina la que demani les dades i pinti el resultat.
 4. Modifica el programa per tal que, tot i rebre dades (via POST o GET) si el número rebut és senar ó [no és un número](http://php.net/manual/es/function.is-numeric.php), mostri un missatge dient que el programa només funciona amb números parells. I torni a demanar el número i **conservi la frase** (has de posar el seu valor dins *value* del tag *input* ) 


**Solució**



```php
<html>
    <head>
        <meta charset="UTF-8"/>
        <title>Pràctica escriu frase n vegades</title>
    </head>
    <body>
<?php

$rebo_dades= array_key_exists("laMevaFrase",$_REQUEST) &&
             array_key_exists("elMeuNumero",$_REQUEST);
             
$numero_es_valid = $rebo_dades &&
                   is_numeric( $_REQUEST['elMeuNumero'] ) && 
                   ( $_REQUEST['elMeuNumero'] % 2 == 0 )
                   ;
$cal_pintar_formulari = ( ! $rebo_dades || ( $rebo_dades && ! $numero_es_valid ) );
if ($cal_pintar_formulari) {

   $frase = "";
   if ( $rebo_dades && ! $numero_es_valid ) {
       $frase = $_REQUEST["laMevaFrase"];
       echo "Noi!! Aquest programa només funciona amb números parells";
   }    
    
?>
    <form method="get" action="">
        Frase: <input type="text" name="laMevaFrase" 
               value="<?php echo $frase ?>" />
        Número: <input type="text" name="elMeuNumero"/>
        <input type="submit" value="Submit"/>
    </form>    
<?php 
} else {
    $metode = $_SERVER['REQUEST_METHOD'];
    echo "He rebut les dades via $metode<br>";
    for ($i = 0; $i < $_REQUEST['elMeuNumero']; ++$i ) {
        $frase  = $_REQUEST['laMevaFrase'];
        echo "$frase<br>";
    }    
}
?>
    </body>
</html>
```

---

#FpInfor #Daw #DawMp07 #DawMp07Uf01

* Resultats d'aprenentatge 3.a
* Continguts 3.1
---

###### Autor: daniel herrera 2013.10.04 13:35:59
###### Editat per: daniel herrera 2017.10.09 13:12:54
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
