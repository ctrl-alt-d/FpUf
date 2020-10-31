# Corxets Fibonnachi
## DAW-MP07-UF1 - Exercici de Desenvolupament web en entorn servidor.
Crearem tres pàgines amb el patró PRG.

* **P0.php** demana un número. L'envia via POST a **P1.php**.
* **P1.php** si és número i està comprés entre 5 i 15 redirecció a **P2.php** passant el número via get ( via url ) que anomenaram n. Cas contrari tornem a **P0.php** tot enviant missatge a l'usuari via cookie.
* **P2.php** en un array posem els n primer números de la serie fibonacci. Cal recorre l'array tot pintant un corxet a cada iteració. Davant el corxet pintarem tants espais en blanc com el valor de l'array en aquell element ens indiqui. Després invocarem array_reverse i farem el mateix per tal de tancar els corxets.

Resultat per n = 10:

```java
{
 {
 {
  {
   {
     {
        {
             {
                     {
                                  {
                                  }
                     }
             }
        }
     }
   }
  }
 }
 }
}
```


**Solució P0.php**:

```php
<?php
$msg = "";
if (isset($_COOKIE['msg'])) {
    $msg=$_COOKIE['msg'];
    setcookie("msg", null,-1 );
}
?>

<!DOCTYPE html>
<html>
<head>
	<meta charset=utf-8 />
	<title>Fibonnachi</title>
</head>
<body>

<div>
    <?php echo $msg ?>
</div>

<form name="login" 
      action="p1.php" 
      method="post" 
      accept-charset="utf-8">
  <ul>
    <li><label for="n">Número d'elements de la sèrie:</label>
    <input type="number" value=0 name="n" placeholder="número d'elements" required></li>
    <input type="submit" value="Calcula"></li>
  </ul>
</form>   
 
</body>
</html>
```


**Solució P1.php**:

```php    
<?php

$rebo_dades = isset( $_REQUEST['n']);
$dades_ok = $rebo_dades &&
            is_numeric( $_REQUEST['n'] ) &&
            $_REQUEST['n'] > 5 &&
            $_REQUEST['n'] <= 15;

if ($dades_ok) {
    header('Location: p2.php?n='.$_REQUEST['n']);
} else {
    setcookie("msg", "Has de posar un número entre 5 i 15." );
    header('Location: p0.php');
}

?>    
```


**Solució P2.php**:

```php  
<!DOCTYPE html>
<html>
<head>
	<meta charset=utf-8 />
	<title>Fibonnachi</title>
</head>
<body>

<?php

//tornem a comprovar
$rebo_dades = isset( $_REQUEST['n']);
$dades_ok = $rebo_dades &&
            is_numeric( $_REQUEST['n'] ) &&
            $_REQUEST['n'] > 5 &&
            $_REQUEST['n'] <= 15;

if (!$dades_ok) {
    header('Location: p0.php');
    die();
}


//paràmetres comprovats
$n = $_REQUEST['n'];

$serie = array();
$serie[0] = 0; 
$serie[1] = 1;

for( $i=2; $i < $n; $i++ ) {
    $serie[$i]=$serie[$i-1]+$serie[$i-2];
}

echo "<pre>";

//obrim corxets
foreach ($serie as $value) {
    for ($i=0;$i<$value;$i++) echo " ";
    echo "{<br>";
}

//fem reverse
$serie=array_reverse($serie);

//tanquem corxets
foreach ($serie as $value) {
    for ($i=0;$i<$value;$i++) echo " ";
    echo "}<br>";
}


echo "</pre>";

?>


</body>
</html>
```

---

#FpInfor #Daw #DawMp07 #DawMp07Uf01

---

###### Autor: daniel herrera 2016.10.25 13:32:49
###### Editat per: daniel herrera 2016.10.25 13:38:20
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
