# Política de contrasenyes en Windows
## SMX-MP06-UF1 - Exercici de seguretat passiva. 
Introducció
--------------
L'accés als sistemes operatius sol estar control·lat a través d'algun sistema d'usuari i contrasenya. Generalment si es deixa a un usuari que triï la contrasenya que vulgui el resultat serà una contrasenya dèbil o fàcil d'endevinar i això no es pot permetre en un sistema professional.

> El nivell de seguretat d'una organització depèn de la política de contrasenyes que es faci servir ja que unes contrasenyes dèbils poden facilitar la intrusió en el sistema d'atacants.

Però s'ha d'anar amb compte a l'hora de definir una política de contrasenyes ja que si és molt complexa els usuaris normalment solen ignorar-la i fer coses poc segures com escriure-les en Post-It, etc... 

Els sistemes operatius ofereixen alguna forma d'obligar als usuaris a tenir contrasenyes que segueixin alguna política determinada. En Windows la definició de polítiques de contrasenyes es fa en un punt centralitzat anomenat “Directiva de seguridad local” que permet controlar detalladament tot el que fa referència a les contrasenyes i bloqueigs de comptes d'usuari

Activitat
-----------------------

###Definir una Política de contrasenyes en Windows

1. En una màquina virtual en Windows definiu-hi tres usuaris amb contrasenyes simples: “12345”, “1Ab”, “patata”

2. Definiu una política de contrasenyes que obligui als usuaris a:

    * Tenir contrasenyes de 9 o més caràcters amb complexitat (números, lletres i símbols)
    * Que caduquin cada setmana
    * Que guardi les darreres tres contrasenyes
    * Que bloquegi el compte si l'usuari falla la contrasenya tres vegades seguides i que només pugui restablir-la l'administrador

3. Reinicieu el sistema

4. Intenteu crear un usuari nou amb una contrasenya senzilla que no compleixi la política i comproveu que el sistema no el deixa crear

5. Intenteu entrar amb un dels usuaris creats anteriorment. Què fa el sistema?

6. Amb un usuari qualsevol intenteu entrar en el sistema fallant la contrasenya 4 vegades. Què passa?

7. Entreu amb un dels usuaris del sistema i canvieu la contrasenya 5 vegades. Comproveu que no podeu posar una de les anteriors.


---

#FpInfor #Smx #SmxMp06 #SmxMp06Uf01

* Resultats d'aprenentatge 1.7
* Continguts 1.6
---

###### Autor: Xavier Sala 2013.10.28 10:42:00
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
