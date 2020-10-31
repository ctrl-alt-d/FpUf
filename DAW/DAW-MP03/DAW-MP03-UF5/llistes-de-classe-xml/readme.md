# LListes de classe XML
## DAW-MP03-UF5 - Exercici de POO. Llibreries de classes fonamentals
StAX
====================
Streaming API for XML (StAX) és una interfície de programació de programes per llegir i escriure documents XML que intenta superar els problemes que tenen els dos sistemes tradicionals de llegir fitxers XML: sistemes basats en events (SAX és el més habitual) i DOM.

StAX intenta aprofitar-se del millor dels dos sistemes:

* No necessita carregar tot el document a memòria com fan els sistemes basats en DOM de manera que consumeix pocs recursos
* Permet que sigui l'usuari i no el parser el que control·la el processat del fitxer XML
* Permet crear documents XML com ho fa DOM

StAX va ser dissenyat pensant en el concepte de cursor (un punt dins del document) que és mogut per l'aplicació a mesura que li fa falta la informació. Funciona amb un sistema conegut com a Pull parsing que es contraposa a la forma de treballar de SAX (Push parsing) on és el parser el que control·la la sortida de la informació i l'aplicació es veu obligada a mantenir l'estat dels events per saber on està en el document.

Funcionament
--------------------
StAX fa servir l'objecte XMLStreamReader per crear un parser a partir d'un fitxer:

    FileReader r = new FileReader("alumnes.xml");
    XMLStreamReader parser = XMLInputFactory.newInstance().createXMLStreamReader(r);
 
I a partir d'aquest es pot control·lar el moviment dins del document amb la funció next(). El document haurà acabat quan no hi hagin més elements ( hasNext() == false )

    while (parser.hasNext())
    {
          int eventCode = parser.next();
          ...
    }
 
El codi de l'event és el que es podrà fer servir per determinar en quin lloc del document estem: inici d'una etiqueta, final, etc... 

    if (eventCode ==  XMLStreamReader.START_ELEMENT)
    {                    	  
        System.out.println(parser.getLocalName());
        System.out.println(parser.getElementText());
    }
 
Activitat
------------------
Se us demana que desenvolupeu un programa amb Java que a partir de les dades del document XML que se us proporciona tregui per pantalla les llistes de classe.

    XML
    ++++++++++++++
    o Federicu Pi

    Xarxes Locals
    ++++++++++++++
    o Federicu Pi
    o Marcelinu Paivinu
    o Filomenu Garcia

    Programació
    ++++++++++++++
    o Filomenu Garcia

El fitxer XML amb les dades té aquesta forma: 

```xml
<persones>
  <alumne>
    <nom>Federicu Pi</nom>
    <any>2010</any>
    <credits>
      <assignatura>XML</assignatura>
      <assignatura>Xarxes Locals</assignatura>
    </credits>
  </alumne>
  <alumne>
    <nom>Marcelinu Paivinu</nom>
    <any>2010</any>
    <credits>
      <assignatura>Xarxes Locals</assignatura>
    </credits>
  </alumne>
  <alumne>
    <nom>Filomeno Garcia</nom>
    <any>2010</any>
    <credits>
      <assignatura>Programació</assignatura>
      <assignatura>Xarxes Locals</assignatura>
    </credits>
  </alumne>
</persones>
```


---

#FpInfor #Daw #DawMp03 #DawMp03Uf05

* Resultats d'aprenentatge 1.h 1.i
* Continguts 1.7
---

###### Autor: Xavier Sala 2014.02.09 22:09:04
###### Editat per: Xavier Sala 2014.02.09 22:09:04
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
