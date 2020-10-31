# PHP - Accés a dades amb PDO
## DAW-MP07-UF3 - Exercici de Tècniques d’accés a dades.
Repassem que és PDO:

*The PHP Data Objects (PDO) extension defines a lightweight, consistent interface for accessing databases in PHP. Each database driver that implements the PDO interface can expose database-specific features as regular extension functions. Note that you cannot perform any database functions using the PDO extension by itself; you must use a database-specific PDO driver to access a database server.*

*PDO provides a data-access abstraction layer, which means that, regardless of which database you're using, you use the same functions to issue queries and fetch data. PDO does not provide a database abstraction; it doesn't rewrite SQL or emulate missing features. You should use a full-blown abstraction layer if you need that facility.*

Anem a fer la primera aplicació que s'hi connecti a una base de dades. Utilitzarem *MySQL* per aquesta pràctica.

Primer creem la base de dades:

```console
dani@teacher:~/projectes/fpuf$ mysql -u root -p

```
Creem la base de dades i un usuari que tingui tos els permisos sobre la base de dades creada:

```sql
mysql> create database acces_dades;
mysql> create user u_acces_dades@localhost identified by "i";
mysql> grant all privileges on acces_dades.* to u_acces_dades@localhost ;
```

Ara ens hi desconnectem de root i ens connectem amb l'usuari que hem creat, creem una taula i hi posem valors:

```sql
mysql> exit;
$mysql -u u_acces_dades -p
mysql> use acces_dades;
mysql> create table prova ( i int, a varchar(10) );
mysql> insert into prova values ( 1,'a'), (2,'b');
```


Això crearà la taula:

 i  | a
------------- | -------------
 1  | 'a'
 2  | 'b'


Per últim llegim tots els valors des de PHP:

```php
<?php
  //connexió dins block try-catch:
  //  prova d'executar el contingut del try
  //  si falla executa el catch
  try {
    $hostname = "localhost";
    $dbname = "acces_dades";
    $username = "u_acces_dades";
    $pw = "i";
    $pdo = new PDO ("mysql:host=$hostname;dbname=$dbname","$username","$pw");
  } catch (PDOException $e) {
    echo "Failed to get DB handle: " . $e->getMessage() . "\n";
    exit;
  }
  
  //preparem i executem la consulta
  $query = $pdo->prepare("select i, a FROM prova");
  $query->execute();
  
  //anem agafant les fileres d'amb una amb una
  $row = $query->fetch();
  while ( $row ) {
    echo $row['i']." - " . $row['a']. "<br/>";
	$row = $query->fetch();
  }

  //eliminem els objectes per alliberar memòria 
  unset($pdo); 
  unset($query)
 
?>
```

**Exercici**: 

 1. Fes la teva base de dades *acces_dades* i prova aquest codi php.
 2. Simplifica el codi usant [foreach + query](http://www.php.net/manual/en/pdo.query.php)
 3. Fes una nova base de dades anomenada *gringottsDB* i crea un usuari amb permisos sobre aquesta base de dades. Crea una taula anomenada *goblins* amb estructura: *goblin_name*, *password*, *last_login*. Inserta uns quants goblins (fent servir SQL). Per últim fes un programet amb PDO que llisti tots els goblins de la taula.

**Lectura recomanada** [Explendit resum de com fer servir PDO](http://stackoverflow.com/questions/12859942/why-shouldnt-i-use-mysql-functions-in-php)



**Solució exercici 2**


```php
<?php
```

       ...
      
      //preparem la consulta i l'executem
      $query = $pdo->prepare("select i, a FROM prova");
      $query->execute();
    
      //comprovo errors:
      $e= $query->errorInfo();
      if ($e[0]!='00000') {
        echo "\nPDO::errorInfo():\n";
        die("Error accedint a dades: " . $e[2]);
      }  
      
      //itero
      foreach ($query as $row) {
        echo $row['i']." - " . $row['a']. "<br/>";
      }
    
      ...
    ?>

---

#FpInfor #Daw #DawMp07 #DawMp07Uf03

* Resultats d'aprenentatge 1.b
* Continguts 1.2
---

###### Autor: daniel herrera 2013.10.20 14:04:59
###### Editat per: daniel herrera 2017.10.24 13:34:14
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
