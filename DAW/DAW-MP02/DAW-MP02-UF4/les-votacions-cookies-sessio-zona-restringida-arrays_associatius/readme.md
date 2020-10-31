# Les votacions: cookies, sessió, zona restringida, arrays_associatius
## DAW-MP02-UF4 - Exercici de Bases de dades objectes-relacionals
Es volen realitzar unes votacions a l’institut i cal fer un programa que gestioni tot el procés electoral.
Hi haurà un cens universal que estarà informatitzat.

Només hi haurà una mesa amb un únic ordinador per tal que no es digui que en una mesa hi vota més gent que de la censada.
Per poder accedir a les pàgines de votacions cal autenticar-se amb aquest usuari i passwd:    votacions / democràcia (hardcoded)

Les pantalles per autenticar-se són: **mostra_formulari_login.php** i **processa_login.php**
Un cop autenticat apareix un menú que s’explica més aball, primer expliquem estructures de dades de que disposes:

Tot el cens està en un únic array php que cal importar només des de les pàgines que es necessiti. **cens.php**:

```php
<?php
$cens= array(
"600f6857f966a3ecb5ca3022150669c1",  //md5('10A'); 
"72e2f0c6d08108b42520cc6adffa86ae",  //md5('20B'); 
"e1906c422714eb1385315767c466f30b",  //md5('30C'); 
"d1296d5b86548039214ee1380b44ec16",  //md5('40D'); 
"3bf1be5e1a99d8c8650852f8f4ce54ff",  //md5('50E'); 
)
?>
```

Les opcions a votar també estan en un array que cal importar. **opcions.php**:

```php
<?php
$opcio= array( 
1 => "Volem la truita amb ceba",
2 => "Volem la truita sense ceba",
)
?>

```
Com funciona el programa?

El membra de la mesa s’autentica i li apareix un menú (**menu.php**) amb dues possibilitats:

#### **OP1**: Introduir vot (**introduir_vot.php**):

Apareix una pantalla on demana dues coses:

* DNI (input type text)
* Opció que vota (radio button)

Això s’envia **processa_vot.php** que processa el vot i reenvia cap a menú. Al menú es mostra el resultat de l’acció ( success o l’error que ha hagut ) mitjançant un sistema d’enviament de cookies.

Processar el vot són dues coses:
* Posem en una variable de sesió el hash del dni per tal de que no torni a votar. Per fer el hash: `md5( $_REQUEST['DNI'] );`
* Sumem el seu vot a l’array de votacions que també tenim en una variable de sessió: `$_SESSION[ $_REQUEST['OPCIO'] ]++;`

#### **OP2**: Veure resultats (**veure_resultats.php**):

Ens mostra quants vots porta acumulat cada resultat.

**Important**:

* Només es pot accedir a les pàgines veure_resultats.php, introduir_vot.php, processa_vot.php i menu.php si ens hem autenticat.

**Can entregar:**

Aquest full amb el nom i cognoms.
Un pdf amb:
* el codi del programa 
* el nom a cada full i numerats.
* Un dibuix (en paper) amb un exemple de navegació per la web tal com els fem a la pissarra. Cal que aparegui també el PRG.
* El pdf no estarà comentat perquè el programa es llegirà perfectament bé tot i contenir un mínim de comentaris dins el propi codi.

**Es valorarà**:

* Què s’utilitzen les tècniques de tractament d’arrays associatius (recorrer array només quan sigui necessari, consultar si element és a l’array, consultar valor d’element de l’array, etc )
* Claretat del codi i programació llegible.
* Els errors d’indentació baixen 1 punt per error d’indentació.
* Les variables que enganyin (el nom i el que contenen siguin coses diferents) baixen 1 punt per variable.
* Per superar l’examen cal demostrar l’assoliment i capacitat de posada en pràctica de tot el que s’ha treballat a la UF: arrays associatius, formularis, PRG, sessions, variables de sessió, control d’usuari, zona restringida, instruccions de control de flux del programa, missatgeria cap a usuari mitjançant cookies.

---

#FpInfor #Daw #DawMp02 #DawMp02Uf04

---

###### Autor: daniel herrera 2017.10.19 08:12:59
###### Editat per: daniel herrera 2017.10.19 09:00:40
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
