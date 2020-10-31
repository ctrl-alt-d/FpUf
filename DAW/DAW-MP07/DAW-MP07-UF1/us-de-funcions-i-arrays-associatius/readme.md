# Us de funcions i arrays associatius
## DAW-MP07-UF1 - Exercici de Desenvolupament web en entorn servidor.
Es tracta de fer un programa php que anoti les connexions remotes que rep, tant la IP remota com el navegador que utilitza, i que mostri tot l'històric de connexions.

Com que encara no sabem fer servir una base de dades, anotarem les connexions en un array com aquest:

```php
Array
(
    [0] => A connection from 10.240.208.91 using Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/45.0.2454.101 Safari/537.36
    [1] => A connection from 10.240.115.169 using Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/45.0.2454.101 Safari/537.36
    [2] => A connection from 10.240.86.62 using Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/45.0.2454.101 Safari/537.36
)

```
I persistirem l'array a disc amb aquestes funcions que inclourem al nostre projecte al fitxer `funcions.php`:

```php
<?php

//retrieving
function llegeix_de_disc() {
    $file = 'my_array.php';
    $var = null;
    if ( file_exists($file) ) {
        $var = json_decode(file_get_contents($file), true);
    } else {
        $var = array();
    }
    
    return $var;
}

// storing
function persisteix_a_disc($var) {

    $file = 'my_array.php';
    file_put_contents($file,json_encode($var));

}

?>
```

**Aquesta no és una manera professional de persistir dades dinàmiques, cal usar base de dades però encara no ho hem treballat**

El nostre programa ha de tenir aquesta estructura:

```php
<?php

//incloure altres fitxers
//todo: incloure funcions.php

//retrieving
$var = //todo: cridar la funció que llegeix l'array de disc

//afegir dades darrera connexió
$ip_remota = //todo: obtenir l'adreça remota del navegador
$navegador = //todo: obtenir el tipus de navegador que s'hi connecta
$txt = "Connexió des de $ip_remota using $navegador";
$var[] = $txt;

//mostrar totes les connexions al navegador
//todo: fer un bucle per recorrer l'array i mostrar-lo com una taula

//storing
//todo: invocar la funció que persisteix a disc amb els paràmetres que calgui.

?>
```

Es demana:

* Implementar el programa i que funcioni correctament. Indentant el codi i documentant dins el propi codi de programa les parts que calgui.
* Executar el programa en alguna plataforma pública, ex: c9.io i aconseguir que ens arribin connexions remotes ( ex: publicant la url al pastebin )

Entregables:

* Fitxer pdf amb el codi del programa ( amb visualització de codi de programa, no amb visualització de processador de textos )
* Explicació de com hem aconseguit tràfic cap a la nostra web.
* Captura del programa en funcionament i identificar quines connexions ens han arribat des de l'exterior.

**Segona part de l'exercici:**

* Modifica el codi per tal que envii una cookie als clients que s'hi connectin de manera que:
    * Si és el primer cop que es connecten el valor de la cookie valgui 1
    * Si s'han connectat anteriorment s'incrementi el valor de la cookie i li tornem a enviar.
    * Dins l'array associatiu emmagatzemarem quantes vegades s'ha connectat aquell usuari:
        * [7] => Connection number 4 from 10.240.208.91 using Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/45.0.2454.101 Safari/537.36

Entrebables:

* Fitxer pdf ampliat amb la captura del codi modificat.
* Captura de pantalla mostrant el valor de la cookie al navegador.








---

#FpInfor #Daw #DawMp07 #DawMp07Uf01

---

###### Autor: daniel herrera 2015.10.15 08:59:57
###### Editat per: daniel herrera 2015.10.15 09:36:38
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
