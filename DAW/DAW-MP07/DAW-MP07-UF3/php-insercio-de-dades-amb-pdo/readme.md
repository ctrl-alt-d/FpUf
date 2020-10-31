# PHP - Inserció de dades amb PDO
## DAW-MP07-UF3 - Exercici de Tècniques d’accés a dades.
En aquest exercici practicarem la inserció de dades amb una base de dades usant PDO.

Primer creem la base de dades i la taula on insertarem dades, això es pot veure a l'exercici [PHP - Accés a dades amb PDO](/DAW/DAW-MP07/DAW-MP07-UF3/php-acces-a-dades-amb-pdo/readme.md)

Mitjançant aquest codi insertem les dades:

```php
<?php 

  try {
    $hostname = "localhost";
    $dbname = "acces_dades";
    $username = "u_acces_dades";
    $pw = "i";
    $dbh = new PDO ("mysql:host=$hostname;dbname=$dbname","$username","$pw");
  } catch (PDOException $e) {
    echo "Failed to get DB handle: " . $e->getMessage() . "\n";
    exit;
  }
  
  try {
  	echo "Comença la inserció<br>";
	//cadascun d'aquests interrogants serà substituit per un paràmetre.
  	$stmt = $dbh->prepare("INSERT INTO prova (i, a) VALUES(?,?)"); 
	//a l'execució de la sentència li passem els paràmetres amb un array 
    $stmt->execute( array('13', 'caco')); 
    echo "Insertat!"; 
  } catch(PDOExecption $e) { 
    print "Error!: " . $e->getMessage() . " Desfem</br>"; 
  } 
   
?> 
```

**Exercici**:

 1. Fixat que és important passar els paràmetres d'aquesta manera per evitar sql injection. Més endavant farem una pràctica sobre això.
 2. Executa aquest codi al teu entorn i amb la teva base de dades. Comprova que els valors realment s'inserten a la taula.
 3. Fés un formulari per a insertar goblins a la base de dades *gringottsDB* de l'exercici [PHP - Accés a dades amb PDO](/DAW/DAW-MP07/DAW-MP07-UF3/php-acces-a-dades-amb-pdo/readme.md). Molt important: Recorda crear la clau primària de la taula. Molt important: les passwd MAI s'emmagatzemen en text pla, cal fer una transformació hash de les mateixes, per exemple amb MD5. Reflexiona perquè fem això amb les passwd.

Nota, codi per emmagatzemar la passwd amb MD5:

```php
<?php
$stmt = $dbh->prepare("INSERT INTO prova (i, a) VALUES(?, MD5(?) )");
```


**Solució**

```php
<?php

$usuari = "";
$msg = "";
if (isset($_COOKIE['msg'])) {
    $msg=$_COOKIE['msg'];
    setcookie("msg", null,-1 );
}

$es_post = ($_SERVER['REQUEST_METHOD'] == 'POST');
if ( $es_post ) {

  try {
    $hostname = "localhost";
    $dbname = "gringottsDB";
    $username = "u_gringottsDB";
    $pw = "i";
    $pdo = new PDO ("mysql:host=$hostname;dbname=$dbname","$username","$pw");
  } catch (PDOException $e) {
    echo "Failed to get DB handle: " . $e->getMessage() . "\n";
    exit;
  }

  $es_ok = isset( $_POST['usuari'] ) &&
           isset( $_POST['passwd'] ) &&
           strlen( $_POST['usuari'] ) >= 5 &&
           strlen( $_POST['usuari'] ) <= 10 &&
           strlen( $_POST['passwd'] ) >= 5 &&
           strlen( $_POST['passwd'] ) <= 15;

  /*
  msg_error = "";
  if (!$es_ok ) {
    if (!isset( $_POST['usuari'] )) msg_error += " Usuari no informat";
    if (!isset( $_POST['password'] )) msg_error += " password no informat";
    if (!(strlen( $_POST['usuari'] ) >= 5)) msg_error += " Usuari massa curt";
    if (!($_POST['usuari'] ) <= 10)) msg_error += " Usuari massa llarg";
    if (!isset( $_POST['usuari'] )) msg_error += " Usuari no informat";
  }
  */

  //comprovo que no estigui repetit aquest usuari.
  if ( $es_ok ) {
      $usuari= $_POST['usuari'];
      $sql="select count(*) as n from goblins where goblin_name = ?";
      $query = $pdo->prepare($sql);
      $query->execute( array( $usuari ) );

      //control d'errors
      $e= $query->errorInfo();
      if ($e[0]!='00000') {
        echo "\nPDO::errorInfo():\n";
        die("Error accedint a dades: " . $e[2]);
      }

      $resultat= $query->fetch();
      $es_ok = ($resultat['n'] == 0 );
  }

  if ($es_ok) {
    //inserció i redirect
    $usuari= $_POST['usuari'];
    $passwd= $_POST['passwd'];
    $sql="insert into goblins values (?,md5(?), null)";
    $query = $pdo->prepare($sql);
    $query->execute( array( $usuari,$passwd ) );

    $e= $query->errorInfo();
    if ($e[0]!='00000') {
      echo "\nPDO::errorInfo():\n";
      die("Error accedint a dades: " . $e[2]);
    }


    setcookie("msg", "Usuari [$usuari] insertat correctament." );
    die( header('Location: ./insert.php'));

  } else {
    //missatge d'error.
    if (isset($_POST['usuari'])) $usuari= $_POST['usuari'];
    $msg="Comprova que has introduit correctament usuari i password i que no està repetit";
  }

}

?>

<!DOCTYPE html>
<html>
<head>
	<meta charset=utf-8 />
	<title>Inserció</title>
</head>
<body>

<div>
    <?php echo $msg ?>
</div>

<form name="login"
      action=""
      method="post"
      accept-charset="utf-8">
  <ul>
    <li><label for="usuari">Usuari:</label>
    <input type="text" value="<?php echo $usuari; ?>"
           name="usuari" placeholder="usuari" required></li>

    <li><label for="passwd">Password:</label>
    <input type="password"
           name="passwd" placeholder="passwd" required></li>

    <input type="submit" value="Calcula"></li>
  </ul>
</form>

</body>
</html>
```

**Solució 2**

```php
<?php
```

    //Obtenim el missatge de la cookie
    $msg = "";
    if (isset($_COOKIE['msg'])) {
       $msg=$_COOKIE['msg'];
       setcookie("msg", null,-1 );
    }

    $es_post = ($_SERVER['REQUEST_METHOD'] == 'POST');
    if ($es_post) {
     try {
      $hostname = "localhost";
      $dbname = "gringottsDB";
      $username = "u_gringottsDB";
      $pw = "i";
      $pdo = new PDO ("mysql:host=$hostname;dbname=$dbname","$username","$pw");
      
      //Establim els mode d'errors a ERRMODE_EXCEPTION per obtenir els errors 
      //llançats per la BD
      $pdo->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);
    } catch (PDOException $e) {
      echo "Failed to get DB handle: " . $e->getMessage() . "\n";
      exit;
    }
    
    $es_ok = isset( $_POST['usuari'] ) &&
            isset( $_POST['passwd'] ) &&
            strlen( $_POST['usuari'] ) >= 5 &&
            strlen( $_POST['usuari'] ) <= 10 &&
            strlen( $_POST['passwd'] ) >= 5 &&
            strlen( $_POST['passwd'] ) <= 15;
    
    //comprovo que no estigui repetit aquest usuari.
    if ( $es_ok ) {
      try {
        $usuari= $_POST['usuari'];
        $sql="select count(*) as n from goblins where goblin_name = ?";
        $query = $pdo->prepare($sql);
        $query->execute( array( $usuari ) );
        
        $resultat= $query->fetch();
        if ($resultat['n'] == 0 )
        {
          //Si no existeix l'usuari
          $es_ok = true;
        }
        else
        {
          //Si existeix l'usuari
          $es_ok = false;
          $msg = "L'usuari ja existiex";
        }
  
      } catch (PDOException $e) {
        echo "Error consultant goblins: " . $e->getMessage() . "\n";
        exit;
      }
    }
    
    //Si l'usuari no està repetit l'inserim
    if ( $es_ok ) {
      try {
        $usuari= $_POST['usuari'];
        $passwd= $_POST['passwd'];
        $sql="insert into goblins values (:usuari, md5(:passwd), null)";
        $query = $pdo->prepare($sql);
        $query->execute( array( ':usuari'=>$usuari, ':passwd'=>$passwd ) );
        
        $msg = "Usuari [$usuari] insertat correctament.";
  
      } catch (PDOException $e) {
        echo "Error inserint goblin: " . $e->getMessage() . "\n";
        exit;
      }
  
    } else {
      //missatge d'error
      if (!isset( $_POST['usuari'] )) $msg .= "Usuari no informat <br>";
      if (!isset( $_POST['passwd'] )) $msg .= "Password no informat <br>";
      if (strlen( $_POST['usuari'] ) < 5) $msg .= "Usuari massa curt <br>";
      if (strlen( $_POST['usuari'] ) > 10) $msg .= "Usuari massa llarg <br>";
      if (strlen( $_POST['passwd'] ) < 5) $msg .= "Password massa curt <br>";
      if (strlen( $_POST['passwd'] ) > 15) $msg .= "Password massa llarg <br>";
    }
    
    //Guardem el missatge a la cookie i redirigim
    setcookie("msg", $msg);
    die( header('Location: ./Insertar_dades_Goblins.php'));
    }
    ?>

    <!DOCTYPE html>
    <html>
      <head>
      <meta charset="utf-8" />
      <title>Inserció</title>
      </head>
      
      <body>
        <div>
          <?php echo $msg ?>
        </div>
    
        <h1>Formulari per afegir goblins</h1>
        
        <form name="login"
              action="" 
              method="POST"
              accept-charset="utf-8">
            
            <label for="usuari">Usuari:</label>
            <input type="text" value="<?php echo $usuari; ?>" name="usuari" placeholder="usuari" required/>
            <br/>
            <label for="passwd">Password:</label>
            <input type="password" name="passwd" placeholder="passwd" required/>
            <br/>
            <input type="submit" value="Enviar"/>
        </form>
      </body>
    </html>

---

#FpInfor #Daw #DawMp07 #DawMp07Uf03

* Resultats d'aprenentatge 1.b 1.c 1.d 1.e
* Continguts 1.2 1.3 1.4 1.5
---

###### Autor: daniel herrera 2013.10.20 14:35:59
###### Editat per: Sergi Coll 2016.12.05 09:47:26
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
