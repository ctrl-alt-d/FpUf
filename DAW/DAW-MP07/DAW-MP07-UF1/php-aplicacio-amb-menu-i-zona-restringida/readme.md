# PHP - Aplicació amb menú i zona restringida
## DAW-MP07-UF1 - Exercici de Desenvolupament web en entorn servidor.
En aquesta pràctica es treballa:

 * Variables de sessió $_SESSION
 * Seguretat: zona restringida i control d'usuaris
 * Formularis: mètode POST (opcionalment GET)
 * Bucles i condicionals

És tracta de fer una aplicació amb menú i zona restringida. El sistema que utilitzarem per emmagatzemar [usuaris i contrasenyes serà un array associatiu](/DAW/DAW-MP07/DAW-MP07-UF1/php-autenticacio-dusuaris/readme.md).

Les pantalles a realitzar són les següents:

 * *formulari_login.php* - Recull usuari i passwd. Llegeix cookie 'errors' si existeix i té valor mostra els errors que allà hi ha llistats per pantalla. Envia usuari i passwd a *processa_login.php*.
 * *processa_login.php* - Comprova usuari i passwd respecte l'array associatiu. Si és ok redirigeix cap a *menu.php* havent posat el nom de l'usuari a la l'array associatiu de sessió. En cas contrari, si usuari i pass no és correcte, informa d'error dins la cookie 'errors' i redirigeix cap a *formulari_login.php*

A partir d'aquí totes les pàgines requereixen haver-se autenticat. Atenció el codi per comprovar que l'usuari ha iniciat sessió ha d'estar dins un include:

 * *menu.php* - Mostra les opcions de menú que són: *comprovar_divisors.php*, *conjetura_collatz.php* )
 * *comprovar_divisors.php* - [comprova els divisors d'un número](/DAW/DAW-MP07/DAW-MP07-UF1/php-numeros-primers/readme.md). Opció per tornar al menú principal.
 * *conjetura_collatz.php* - [comprova la conjetura collatz](/DAW/DAW-MP07/DAW-MP07-UF1/php-algorisme-3n-1-conjetura-collatz/readme.md). Opció per tornar al menú principal.

Per a fer aquest exercici, tots els missatges d'error de formularis o de confirmació de dades s'enviaran via cookie: totes les pantalles comproven si reben cookie 'missatge' si la reben, l'esborren i inclouen el valor de la cookie a la pàgina web. Quan un processament vol enviar missatges a la UI els posa com a valor en aquesta cookie. Com veus la cookie és molt efímera: es fa el Post de les dades del formulari, la pàgina PHP recull les dades, envia cookie de missatge i redirigeix cap a la pàgina que toqui (ex: conjetura_collatz.php?num=17 , a la pàgina final es mostren els possibles missatges de la cookie i el resultat )

---

#FpInfor #Daw #DawMp07 #DawMp07Uf01

* Resultats d'aprenentatge 4.d
* Continguts 4.4
---

###### Autor: daniel herrera 2013.10.14 13:18:39
###### Editat per: Sergi Coll 2016.11.09 11:48:08
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
