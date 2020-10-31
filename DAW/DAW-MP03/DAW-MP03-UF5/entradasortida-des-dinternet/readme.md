# Entrada/sortida des d'Internet
## DAW-MP03-UF5 - Exercici de POO. Llibreries de classes fonamentals
La classe URL
----------------------
El JDK de Java proporciona una classe anomenada URL que es fa servir per representar  i manipular adreces en forma de Uniform Resource Identifiers: 

    http://www.iescendrassos.net/index.html

URL disposa de diferents constructors però bàsicament consisteix en que l'objecte es crea a partir d'alguna forma de representar la URL...

    URL web = new URL(“http://www.iescendrassos.net”);

Es poden recuperar dades de un objecte URL a partir de tres mètodes:

* openStream()
* openConnection()
* getContent()

Per simplificar ens concentrarem en els dos primers.

### Obtenir un stream directament
Un cop tenim una URL es pot obtenir un Stream per recuperar-ne les dades de la mateixa forma que es faria amb qualsevol altra font de dades. El mètode se n'encarrega de fer tot el necessari entre client i servidor fins que obté el flux de dades.

S'obté un InputStream que es pot usar de la mateixa forma que es fa servir en altres fonts de dades

    InputStream stream = web.openStream();
    ...

Amb aquest mètode només s'obté el contingut de la URL però no hi haurà res relacionat amb el protocol de transmissió (com per exemple les capçaleres HTTP)

###Fer servir URLConnection
El mètode openConnection retorna un objecte de tipus **URLConnection**. Els objectes URLConnection representen una connexió oberta amb una URL. Aquest objecte permet obtenir un flux de dades d'entrada fent servir la funció getInputStream() que després podrem llegir de la forma habitual

    URL web = new URL(“http://www.iescendrassos.net”);
    URLConnection con = web.openConnection();
    InputStream in = con.getInputStream()
    ...

La diferència està en que a un URLConnection permet molt més control en la connexió que URL: permet passar paràmetres en l'establiment de la connexió (afegir capçaleres, etc...) es poden obtenir dades del protocol, permet enviar-hi dades (el POST de HTTP, per exemple) etc ...

Té un descendent molt usat que és HttpURLConnection que es fa servir per fer connexions específiques en HTTP

Activitat
-----------------

1. Desenvolupeu un programa en Java que us permeti descarregar qualsevol imatge de tipus PNG, GIF, JPG a partir de la seva URL. 

Condicions: 

* Si la URL no porta a una imatge el programa ha de donar un error
* Voleu que el nom del recurs descarregat conservi el nom que tenia a Internet. Si el nom del recurs ja el tenim i ve d'una URL diferent s'ha d'afegir un número d'ordre al darrere

Per exemple:

    http://www.iescendrassos.net/imatge.jpg ha de crear imatge.jpg
    http://moodle.iescendrassos.net/imatge.jpg ha de crear imatge-01.jpg

* Si la imatge ja s'havia descarregat anteriorment (de la mateixa URL) ha d'oferir la possibilitat de descarregar-la de nou o deixar-ho estar


---

#FpInfor #Daw #DawMp03 #DawMp03Uf05

* Resultats d'aprenentatge 2.a 2.b 2.d 4.b 4.c 4.d 4.e
* Continguts 2.1 4.1 4.2 4.3 4.4 4.5
---

###### Autor: Xavier Sala 2014.01.25 22:09:24
###### Editat per: Xavier Sala 2014.01.25 22:09:24
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
