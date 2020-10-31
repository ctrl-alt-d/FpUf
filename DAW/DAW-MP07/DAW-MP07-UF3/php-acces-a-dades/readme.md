# PHP - Accés a dades
## DAW-MP07-UF3 - Exercici de Tècniques d’accés a dades.
PHP disposa d'un gran número de funcions per operar amb diferents sistemes gestors de bases de dades: [Vendor Specific Database Extensions](http://www.php.net/manual/en/refs.database.vendors.php).

Per exemple, per MySQL trobem la instruccion [mysqli::real_connect](http://www.php.net/manual/en/mysqli.real-connect.php) per realitzar la connexió: 

    <?php
    
    $mysqli = mysqli_init();
    ...   
    if (!$mysqli->real_connect('localhost', 'my_user', 'my_password', 'my_db')) {
        die('Connect Error (' . mysqli_connect_errno() . ') '
                . mysqli_connect_error());
    }
    ...    
    ?>

I per a connectar-nos a Oracle disposem de [oci_connect](http://php.net/manual/en/function.oci-connect.php):

    <?php
    
    // Connects to the XE service (i.e. database) on the "localhost" machine
    $conn = oci_connect('hr', 'welcome', 'localhost/XE');
    ...

Investiga que són les Database Extensions Abstraction Layer i reflexiona que aporten respecte utilitzar les instruccions específiques de cada base de dades.

  



---

#FpInfor #Daw #DawMp07 #DawMp07Uf03

* Resultats d'aprenentatge 1.a
* Continguts 1.1
---

###### Autor: daniel herrera 2013.10.19 20:01:02
###### Editat per: daniel herrera 2013.10.19 20:01:02
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
