# Exercici autenticació usuaris amb patró PRG
## DAW-MP07-UF1 - Exercici de Desenvolupament web en entorn servidor.
Fes en fitxer `dades.php` que contingui un array associatiu. Les claus seran els usernames i els valors les passwords.

Fes la pantalla `login.php` on es demani usuari i contrassenya i que actui segons aquest patró:

```bash
si he_rebut_dades llavors
    si les_dades_estan_be llavors
        redirecció cap a benvinguda.php
    en cas contrari
        pintar formulari
en cas contrari
    pintar formulari de login
```

Comprova que ho pots simplificar i deixar com un esquema de tres vies:

```bash
si he_rebut_dades llavors
    si les_dades_estan_be llavors
        redirecció cap a benvinguda.php ( fi )
pintar formulari de login
```

Solució
=====

Fitxer `login.php`:

```php
<?php
    include_once "dades.php";

    $rebo_dades = ( $_SERVER['REQUEST_METHOD'] == 'POST' );
    $dades_ok =   $rebo_dades &&
                  isset( $_REQUEST['usuari'] ) &&
                  array_key_exists( $_REQUEST['usuari'], $usuaris ) &&
                  isset( $_REQUEST['passwd'] ) &&
                  $usuaris[$_REQUEST['usuari']] == $_REQUEST['passwd'];

    if ($rebo_dades )  {
        if ( $dades_ok ) {
            //redirecció
            $usuari = $_REQUEST['usuari'];
            header("Location: benvinguda.php?usuari=$usuari");
            die();
        } else {
            echo "<h4> usuari o passwd incorrecte </h4>"
        }
    }
    //pintem formulari
    $texte = "
    <!DOCTYPE html>
    <html>
      <head>
        <meta charset='utf-8'>
        <title></title>
      </head>
      <body>
        <form action='' method='post'>
        <input type='text' name='usuari' >
        <input type='passwd' name='passwd'>
        <input type='submit' name='Entrar'>
        </form>
        </body>
      </html>        
    ";

    echo $texte;
?>

```

Fitxer `dades.php`:
   
    <?php
    
    $usuaris = array(
        'dani' => '1234',
        'quim' => '1234'
        );
    
    ?>

---

#FpInfor #Daw #DawMp07 #DawMp07Uf01

---

###### Autor: daniel herrera 2016.10.04 14:55:45
###### Editat per: daniel herrera 2017.10.10 13:48:50
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
