# Campionat del món de lluitadors
## DAW-MP03-UF5 - Exercici de POO. Llibreries de classes fonamentals
Objectiu: recuperar dades des d'una aplicació web

Introducció
===========================

### La classe URL

El JDK de Java proporciona una classe anomenada `URL` que es fa servir per representar i manipular adreces en forma de Uniform Resource Identifiers: http://www.iescendrassos.net/index.html

L'objecte `URL` disposa de diferents constructors però en general l'objecte es crea a partir d'alguna forma de representar la URL...
    
```java
URL web = new URL("http://www.iescendrassos.net");
```

Es poden recuperar dades de un objecte URL a partir de dos mètodes:

* openStream()
* openConnection()
* getContent()

Obtenir un stream directament
------------------------------

Un cop tenim una URL es pot obtenir un Stream per recuperar-ne les dades de la mateixa forma que es faria amb qualsevol altra font de dades (com fitxers, etc...). El mètode se n'encarrega de fer tot el necessari entre client i servidor fins que obté el flux de dades.

S'obté un `InputStream` que es pot usar de la mateixa forma que es fa servir en altres fonts de dades

```java
InputStream stream = web.openStream();
```

Amb aquest mètode només s'obté el contingut al que apunta la URL però no hi haurà res relacionat amb el protocol de transmissió (com per exemple les capçaleres HTTP)

Fer servir URLConnection
-------------------------------

El mètode `openConnection` retorna un objecte de tipus `URLConnection` que representa una connexió oberta amb un recurs de xarxa. De la mateixa forma que URL aquest objecte també permet obtenir un flux de dades, en aquest cas fent servir la funció `getInputStream()` 

```java
URL web = new URL("http://www.iescendrassos.net");
```

    URLConnection con = web.openConnection();
    InputStream in = con.getInputStream()
    ...

La diferència està en que a un `URLConnection` permet més control en la connexió amb el servidor: se li poden passar paràmetres extres per la connexió (afegir capçaleres, etc...) es poden obtenir dades del protocol, enviar dades al servidor (POST per exemple)..

Té un descendent molt usat que és `HttpURLConnection` que es fa servir per fer connexions específiques en HTTP

Cookies
-------------
Moltes pàgines fan servir cookies. El sistema se'n pot encarregar automàticament de la gestió de cookies si es crea un objecte `CookieHandler`:

```java
CookieHandler.setDefault(new CookieManager(null, CookiePolicy.ACCEPT_ALL));
```

Només cal que s'executi un cop abans de fer les connexions i el procés de Cookies serà automàtic.

Activitat
======================
L'aplicació web que fa falta per fer aquesta tasca la podeu descarregar [d’aquí](https://drive.google.com/file/d/0B1USLpQ7TipGUFNSSTB3aWRTemc/view?usp=sharing). Podeu executar-la en local amb Java:

    $ java -jar Lluitadors.jar

Després podreu accedir a la web amb [http://localhost:8080](http://localhost:8080) o [http://localhost:8080/Lluitadors](http://localhost:8080/Lluitadors)

> En la web hi podeu descobrir les URL i els mètodes que us faran falta per treballar.

L'aplicació emmagatzema les dades a memòria de manera que cada vegada que l’executeu hi haurà dades diferents.

### Campionat del món de Lluitadors

En el servidor hi ha les dades del campionat de Lluita conegut com el “Campionat del món de lluitadors!”.

En aquests tipus de combats s’enfronten dos lluitadors sense seguir cap norma fins que un dels dos es rendeix.

![Baralla](https://raw.githubusercontent.com/XavierSala/M3UF4-2016-10/master/imatges/baralla.png)

Com que volen que els combats siguin el màxim de justos, des del dia en que s'inscriuen,  als lluitadors ja no els deixen entrenar més i només els donen bledes per menjar per evitar que se’ls hi incrementi la força (haurien d’haver entrenat abans d’apuntar-se!)

Un apostador us ha contractat perquè li feu un programa que li permeti fer apostes segures:

* El programa ha de calcular quin dels lluitadors és el més fort (el que guanya a tots els altres)

---

#FpInfor #Daw #DawMp03 #DawMp03Uf05

---

###### Autor: Xavier Sala 2016.12.15 14:23:22
###### Editat per: Xavier Sala 2016.12.16 07:38:53
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
