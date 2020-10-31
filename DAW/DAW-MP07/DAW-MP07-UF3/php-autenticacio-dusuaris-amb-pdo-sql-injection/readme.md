# PHP - Autenticació d'usuaris amb PDO - SQL Injection
## DAW-MP07-UF3 - Exercici de Tècniques d’accés a dades.
Un cop completada la tasca [PHP - Inserció de dades amb PDO](/DAW/DAW-MP07/DAW-MP07-UF3/php-insercio-de-dades-amb-pdo/readme.md) farem una pantalla que validi els usuaris a la base de dades.

Aquest és el codi que proposo, però aquest codi està malament perquè és vulnerable a atac per **sql injection**. 

    <?php
    session_start();
    
    require_once("connect.php");
    
    $pass = md5($_POST['psw']); 
    
    $sql = "SELECT * FROM goblins WHERE goblin_name = '" . $_POST['gobliname'] ."'";
    
    $statement = $con->prepare($sql);
    
    if (!$statement->execute()) {
         die("Ha fallat la consulta, comprova usuari, passwd, bd, nom taula i nom columna");
    }

    if ($row = $statement->fetch())
    {
        if ( $row['password'] == $pass )
        {
           //die("perfecte");
        }
        //die("usuari trobat, passwd malament");
    }    
    //die("usuari no trobat"); 
    ?>
    
Exercici:

 1. Crea un formulari per enviar les dades necessaries a aquest script php ( l'usuari i la passwd )
 1. Comprova que els usuaris correctes poden entrar i els que no ho són fallen, bé per passwd o bé per usuari.
 1. Un cop comprovat que tot va bé, prova l'atac per sql injection. És a dir, injectant sql al camp usuari, per exemple `mariano';delete from goblins; select 'mariano`
 1. Refés el codi per a que no sigui vulnerable a aquest atac.

---

#FpInfor #Daw #DawMp07 #DawMp07Uf03

* Resultats d'aprenentatge 1.b 1.c 1.d 1.e
* Continguts 1.2 1.3 1.4 1.5
---

###### Autor: daniel herrera 2013.10.21 13:15:43
###### Editat per: daniel herrera 2017.10.26 13:17:12
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
