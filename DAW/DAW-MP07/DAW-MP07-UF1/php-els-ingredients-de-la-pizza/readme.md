# PHP - Els ingredients de la Pizza
## DAW-MP07-UF1 - Exercici de Desenvolupament web en entorn servidor.
Calcula el preu de la pizza:

 1. Fes un formulari PHP que et permeti triar els ingredients d'una pizza.
 2. El preu base de la pizza és 5 euros + 0.5€ per ingredient. 

Amplicació de l'exercici:

 1. Comprova que han inclòs al pizza 'massa', 'orenga'. Si no hi són torna a mostrar el formulari tot renyant a l'usuari: "Una pizza necessita sempre la massa i l'orenga'.
 2. A més de renyar a l'usuari fes que aquests ingredients apareguin marcats juntament amb tots els elements que ja havia triat l'usuari.

Solució
===

>Disclamer: Atenció, aquesta solució és purament acadèmica. No usar aquest patró per a fer aplicacions professionals pels següents motius: el codi html i el codi php estàn altament barrejats, no s'està utilitzant el patró PRG.

**pizza.php**

```php
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title></title>
  </head>
  <body>

<?php
  include_once "dades.php";
  include_once "funcions.php";

  $rebo_dades = ( $_SERVER['REQUEST_METHOD'] == 'POST' );
  $inclou_massa_i_orenga = $rebo_dades &&
                           isset( $_REQUEST['ingredients'] ) &&
                           is_array( $_REQUEST['ingredients'] ) &&
                           in_array( 0, $_REQUEST['ingredients'] ) &&
                           in_array( 1, $_REQUEST['ingredients'] );


  if ($rebo_dades && $inclou_massa_i_orenga )  {
    //he rebut dades i estan ok
    processar_dades( $_REQUEST['ingredients']);
  }
  else {
    //no he rebut dades. O les he rebut i són erronies
    $ingredients_anteriorment_seleccionats = array();
    if ($rebo_dades && !$inclou_massa_i_orenga ) {
      //si les dades són erronies renyar a l'usuari
      renyar_usuari();
      $ingredients_anteriorment_seleccionats = $_REQUEST['ingredients'];
    }
    mostrar_formulari( $ingredients_anteriorment_seleccionats );
  }
?>
  </body>
</html>

```
**funcions.php**

```php
<?php

//funció que processa les dades.
function   processar_dades($ingredients) {

  //variable global amb tots els ingredients que
  //pot portar una pizza amb el seu codi.
  global $possibles_ingredients;

  $preu_total = 5.0;

  //Preparo llista amb tot el que conté la pizza
  $ingredients_solicitats = "";
  foreach ($ingredients as $value) {
    $ingredients_solicitats = $ingredients_solicitats.
                              "<li>".
                              $possibles_ingredients[$value].
                              "</li>";
    $preu_total += 0.5;
  }

  //preparo missatge del processament
  $texte = "<h1>Has demanat una pizza amb els següents ingredients</h1>
            <ul>
               $ingredients_solicitats
            </ul>
            <h3>El preu total de la pizza eś $preu_total</h3>
            ";

  //pinto resultats
  echo $texte;
}

function   mostrar_formulari( $ingredients ) {

  //variable global amb tots els ingredients que
  //pot portar una pizza amb el seu codi.
  global $possibles_ingredients;

  //preparo les opcions de la 'select'
  $ingredients_options = "";
  foreach ($possibles_ingredients as $key => $value) {

    $selected = "";
    //ingredients que l'usuari ja havia seleccionat
    if ( in_array($key, $ingredients) ) {
      $selected = " selected ";
    }
    //alguns ingredients han de quedar seleccionats sempre
    if ( $key==0 || $key==1 ) {
      $selected = " selected ";
    }

    $ingredients_options = $ingredients_options .
                           "<option value='$key' $selected>$value</option>";
  }

  //preparo el formulari
  $formulari = "
    <form method='post' action=''>
       <select  multiple name='ingredients[]'>
            $ingredients_options
       </select>
       <br>
       <input type='submit' value='demanar pizza'>
    </form>
  ";

  //pinto tot
  echo $formulari;

}

function renyar_usuari() {
  echo "<h4>Una bona pizza ha d'incloure massa i orenga</h4>";
}

?>
```

**dades.php**

```php
<?php
  //variable global amb tots els ingredients que
  //pot portar una pizza amb el seu codi.
  $possibles_ingredients = array(
      0 => 'Massa',
      1 => 'Orenga',
      2 => 'Formatge',
      3 => 'Pernil dolç',
      4 => 'Bacon'
  );
?>

```

---

#FpInfor #Daw #DawMp07 #DawMp07Uf01

* Resultats d'aprenentatge 3.b 3.c
* Continguts 3.2 3.3
---

###### Autor: daniel herrera 2013.10.04 13:45:04
###### Editat per: daniel herrera 2016.10.04 14:06:48
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
