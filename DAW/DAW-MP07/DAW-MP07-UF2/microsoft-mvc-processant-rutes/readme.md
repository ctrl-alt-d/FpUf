# Microsoft MVC Processant rutes
## DAW-MP07-UF2 - Exercici de Generació dinàmica de pagines web.
Processant rutes
================

Crea un controlador anomenat `ElMeuControlador` amb dues accions (`act1` i `act2`), totes dues accions accepten dos paràmetres: `p1` i `p2`. Les accions retornaran un string "Sóc l'acció **act1** i he rebut: 'AAA' i '123'".

A l'acció 1 els paràmetres són alfanumérics, per tant la seva expressió regular serà: `\w+`. A l'acció 2 els paràmetres són numérics, per tant la seva expressió regular serà: `\d+`

La ruta tant per P1 com per P2 ha de ser `"accio/{p1}/{p2}"`

Crea i documenta el routing de les dues accions així com el controler.

Demostra ( tot fent la comprovació ) que l'ordre en declarar les rutes és important.

Per tal de provar les rutes, el controlador i les accions, escriu tu mateix al navegador les urls que disparan aquestes accions.

Recorda que per fer aquest exercici has d'informar el 4t paràmetre del MapRoute. Exemple:

    routes.MapRoute(
        "Product",
        "Product/{productId}",
        new {controller="Product", action="Details"},
        new {productId = @"\d+" }
     );

Nota, si al `MapRoute` poses els noms dels paràmetres (ex: `url:` ) has de saber que el 4t paràmetre es diu `constraints`.

---

#FpInfor #Daw #DawMp07 #DawMp07Uf02

---

###### Autor: daniel herrera 2014.11.24 14:32:01
###### Editat per: daniel herrera 2014.11.25 09:35:33
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
