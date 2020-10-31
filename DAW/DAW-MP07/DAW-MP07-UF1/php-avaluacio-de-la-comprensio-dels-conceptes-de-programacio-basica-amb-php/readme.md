# PHP. Avaluació de la comprensió dels conceptes de programació bàsica amb PHP.
## DAW-MP07-UF1 - Exercici de Desenvolupament web en entorn servidor.
2. Digues si és millor fer servir GET o POST per cadascuna d'aquestes accions i explica perquè:
    1. Formulari d'entrada amb usuari i password. `Ex: http://maquina/processa_login.php?usuari=guillermo&password=patata`
    2. Mostrar el detall d'un producte. `Ex: http://maquina/mostra_producte.php?id=1`
    3. Esborrar un producte. `Ex: http://maquina/esborra_producte.php?id=1`

3. Sessió: Digues si es veritat o fals les següents afirmacions i argumenta-les o explica-les amb il·lusttracions o corregeixe-les:
    1. El protocol http és un protocol sense sessió.
    2. El PHP injecta codi al servidor web per tal convertir el http en un protocol amb sessió.
    3. El PHP utilitza cookies per gestionar/simular un mateniment de sessió a nivell d'aplicació sobre un protocol que no és orientat a sessió.
    4. Quan treballem amb PHP sense cap framework el codi PHP i el codi html ens queden barrejats. No ens hem de preocupar per això, és així com es programa via web i el que cal és acostumar-nos.
    5. Les variables de sessió es creen utilitzant la funció `$_SESSION`. Exemple: `$v=3; $_SESSION( $v ); //ja tenim la variable a la sessió, disponible per fer-la servir més endavant`.
    6. Podem restringir parts de la web feta amb PHP mitjançant les variables de sessió.

4. Tipus de dades:  Digues si és correcta o no:
    1. PHP és un llenguatge fortament tipat, però es pot canviar el tipus de la variable dinàmicament amb `type()` i `class()`.
    2. PHP allibera al programador de concatenar strings. Podem fer: `echo "Hola $usuari el teu llenguatge de navegació és $_SERVER['HTTP_ACCEPT_LANGUAGE']";`

1. Arrays associatius: Argumenta si aquest codi i els seus comentaris són correctes o no:

Codi:

```php
<?php
$a = array();
$a[0] = 'a';
$a[1] = 'b';
//eliminem el primer element de l'array:
unset( $a[0]);
//l'element 1 passa a la possició 0, el pintem
echo $a[0];
//el resultat és 'b'
```


---

#FpInfor #Daw #DawMp07 #DawMp07Uf01

---

###### Autor: daniel herrera 2015.10.15 09:09:49
###### Editat per: daniel herrera 2015.10.16 15:40:48
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
