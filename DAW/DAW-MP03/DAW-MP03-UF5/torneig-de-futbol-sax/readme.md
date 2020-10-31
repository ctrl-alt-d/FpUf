# Torneig de futbol XML
## DAW-MP03-UF5 - Exercici de POO. Llibreries de classes fonamentals
SAX
----------------
Simple API for XML (SAX) és una forma de processar els documents XML basada en **events**. Amb SAX s'obté una forma alternativa a l'estàndard DOM (Document Object Model) de llegir dades d'un document XML. Originalment es va pensar per Java però es pot trobar en molts altres llenguatges: C, Perl, Python, ... 

SAX no està en cap especificació “formal” sinó que s'ha agafat l'especificació de Java com a normativa de referència.

El funcionament és senzill, es crea un parser SAX a partir d'un objecte de fàbrica d'events i se li passa el fitxer i la classe que rebrà els events (Processar):

    SAXParserFactory spf = SAXParserFactory.newInstance();
    SAXParser parser = spf.newSAXParser();
    parser.parse(new File("test.xml"), new Processar());

Després el parser va llegint el fitxer i va generant events cada vegada que es troba alguna cosa rellevant: Començament o final d'un document, inici o final d'una etiqueta, contingut, etc... L'objecte que captura els events només ha de capturar les funcions que li són necessàries:

    public class Procesar extends DefaultHandler {
        int numelements=0;
        public void endDocument() throws SAXException{
            System.out.println("Total etiquetes: " + numelements);	
        }	
 
        public void startElement(String uri, String localName, 
                             String qName, Attributes attributes) {
           numelements++;	
        }
    }

Tasca
---------
En el torneig de futbol "La lliga dels colors" han generat els resultats en format XML 

[Descarregar](http://s000.tinyupload.com/index.php?file_id=19124590905519164977)

Necessiten un programa que els permeti mostrar la classificació de cada lliga per pantalla d'una forma semblant a aquesta:

    Vermells .... 10 punts
    Blaus .......  8 punts
    Grocs .......  5 punts
    Blancs ......  2 punts


1. Desenvolupeu un programa en Java que fent servir el parser SAX a partir d'un dels fitxers XML amb els resultats de la lliga mostri per pantalla la classificació final

---

#FpInfor #Daw #DawMp03 #DawMp03Uf05

* Resultats d'aprenentatge 1.h 1.i
* Continguts 1.7
---

###### Autor: Xavier Sala 2014.02.04 08:30:06
###### Editat per: Xavier Sala 2014.02.04 08:42:51
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
