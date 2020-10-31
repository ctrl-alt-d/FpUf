# SQL Injection challenge
## DAW-MP07-UF3 - Exercici de Tècniques d’accés a dades.
Follow code runs at `https://php-danihp.c9.io/sqlinjection/vaca_mu_en.php` url

```php
<?php

//database connection:
try {
    $hostname = "localhost";
    $dbname = "sqlinjection";
    $username = "reto";
    $pw = "reto";
    $dbh = new PDO ("mysql:host=$hostname;dbname=$dbname","$username","$pw");
    $dbh->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_WARNING);
} catch (PDOException $e) {
    die( "Failed to get DB handle: " . $e->getMessage() . "\n" );
}

//Prepare select and execute
$sql = "SELECT * FROM usuaris WHERE username = '" . $_POST['username'] ."'";
$statement = $dbh->prepare($sql);    
if (!$statement->execute()) {
     die("WTF!");
}

//Take first selected row
$user_row = $statement->fetch();
```

    //Row found?
    if ($user_row)
    {
        //L'usuari és a la taula:
        
        //Passwd stored in MD5 format.
        $password = md5($_POST['password']);
        
        //Password match?
        $password_ok = ( $user_row['password'] === $password ) ;
        if ( $password_ok  ) {
            
            //passwd ok: achieved challenge 
            foreach( $dbh->query( "select * from la_vaca_diu order by idVaca") as $l ) {
               echo $l["diu"] . " <br>";
            }
            
        } else {
            
            //passwd is wrong
            die("User Found, bad password");
            
        }
        
    }  else {
        
        //User not in the list:
        die("user not found"); 
        
    }
    ?>

When user is authenticated a text, that is stored on dabatabase, appears: Who is the author of the text?

Explain the steps to achieve challenge.


---

#FpInfor #Daw #DawMp07 #DawMp07Uf03

---

###### Autor: daniel herrera 2015.11.04 15:15:02
###### Editat per: daniel herrera 2015.11.04 15:21:30
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
