# Web Scraping amb Java
## DAW-MP03-UF5 - Exercici de POO. Llibreries de classes fonamentals
Introducció
=====================
Per Web Scraping es coneix el procés automàtic de processar una quantitat de dades d'una pàgina web pensada per ser visualitzada per humans per obtenir-ne només la informació que es desitja per poder-la processar-la posteriorment. 

![web scraping](http://imagizer.imageshack.us/v2/800x600q90/707/u89l.png "enter image title here")

A diferència del que es pensa habitualment no només es pot fer de forma senzilla amb els llenguatges dinàmics sinó que amb Java també es pot fer web scraping.

##Web Scraping en Java

A pesar de que tècnicament amb les classes URL i InputStreams es pot fer qualsevol cosa amb l'HTML rebut, a la pràctica sol interessar més no haver d'escriure tant de codi i que tot el procés sigui més “senzill”

[Jsoup](http://www.jsoup.org) és una llibreria de Java que permet recuperar i processar dades de les pàgines web i convertir-les en un objecte que es pot manipular, navegar i indexar (com un array) de forma senzilla. 

    Document doc =  Jsoup.connect("http://ghap.iescendrassos.net/").get();

També permet processar un document HTML que hagi estat carregat en una cadena de text i processar-ho per tractar-ho en una classe Document

    Document doc = Jsoup.parse(html);

Aquesta classe podrà ser navegada en DOM (getElementsById(), getElementsByTag(), ...) o bé se li podrà extreure informació a partir de selectors CSS o JQuery a través del mètode select()

    Elements inputs = doc.select("a"); 

I es podran recuperar els elements amb les classes Node i Element (o en col·leccions Nodes, Elements)

Ofereix funcions per obtenir atributs (attr()), extreure'n el text (text()), o recuperar directament l'HTML d'un objecte (html() o outerHtml())

    System.out.println(doc.body().text());

Es pot trobar la documentació a http://jsoup.org/apidocs/ 

Tasca
-------------

1.Voleu crear una base de dades en MySQL que tingui tots els colors en català que hi ha en la pàgina de la Wikipèdia [http://ca.wikipedia.org/wiki/Llista_de_colors](http://ca.wikipedia.org/wiki/Llista_de_colors). 

Per això heu creat una taula en la Base de dades amb l'estructura següent:

![Taula Colors](http://imagizer.imageshack.us/v2/800x600q90/28/g4b8.png "enter image title here")

Desenvolupeu un programa que us generi un fitxer de comandes SQL que permeti inserir tots els colors en la base de dades.

    INSERT INTO colors (nom, colorhex, red, green, blue) VALUES ("vermell", "#FF0000", 255,0,0);
    INSERT INTO colors (nom, colorhex, red, green, blue) VALUES ("verd", "#00FF00", 0,25,0);
    ...

[Possible solució](https://github.com/utrescu/ColorsEnCatala)

---

#FpInfor #Daw #DawMp03 #DawMp03Uf05

* Resultats d'aprenentatge 2.a 2.b 2.d 4.b 4.c 4.d 4.e
* Continguts 2.1 4.1 4.2 4.3 4.4 4.5
---

###### Autor: Xavier Sala 2014.01.25 00:17:53
###### Editat per: daniel herrera 2015.02.10 20:33:41
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
