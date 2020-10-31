# PHP - El manteniment de sessió i les variables de sessió
## DAW-MP07-UF1 - Exercici de Desenvolupament web en entorn servidor.
El PHP ens proporciona un mecanisme per, tot i estar treballant sobre un protocol sense estat, mantenir una sessió de treball amb l'usuari.

Com pot PHP mantenir una sessió sobre un protocol que no és orientat a sessió? Bé, no hi ha màgia, php utilitza una cookie que identifica la sessió, cada cop que el navegador és connecta li envia la cookie i d'aquesta manera PHP és capaç d'associar aquella petició a una sessió.

Pràctica:

 1. **P0.php** - [Inicia una sessió amb PHP](http://php.net/manual/es/function.session-start.php). Té un enllaça a P1.php
 2. **P1.php** - Instància algunes [variables de sessió](http://www.php.net/manual/es/reserved.variables.session.php). Fixat que en realitat les variables de sessión són entrades a l'array associatiu *$_SESSION*. Ex: *$_SESSION['laMevaVariableDeSessio']="oculus reparum"*; .Enllaça a **P2.php**
 3. **P2.php** - Pinta les variables de sessió (les que haguem instanciat al punt 2). Enllaça a **P3.php**
 4. **P3.php** - [Destrueix la sessió](http://php.net/manual/en/function.session-destroy.php). Enllaça a **P2.php**.

Comprova que el segon cop que passis per **P2.php** no tens les variables de sessió disponibles.



---

#FpInfor #Daw #DawMp07 #DawMp07Uf01

* Resultats d'aprenentatge 4.c
* Continguts 4.3
---

###### Autor: daniel herrera 2013.10.07 14:40:22
###### Editat per: daniel herrera 2014.10.03 14:34:14
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
