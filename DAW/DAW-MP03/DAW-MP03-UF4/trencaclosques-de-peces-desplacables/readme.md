# Trencaclosques de peces desplaçables
## DAW-MP03-UF4 - Exercici de Programació orientada a objectes. Fonaments
Trencaclosques
============================
La idea és agafar una fotografia i trencar-la en parts diferents que seran les peces del trencaclosques.

![Trencaclosques](http://imageshack.us/a/img824/3632/0et6.png "Trencaclosques")

El programa permetrà carregar qualsevol imatge (de la mida que sigui) per fer el trencaclosques:

1. Al començar durant uns segons s'ha de veure la imatge tal com ha de quedar un cop estigui resolt el trencaclosques i després barrejar-se automàticament
2. Per moure una peça es farà clic amb el ratolí sobre la peça que es vol moure que es mourà, si és possible, a l'espai buit
3. S'ha de portar el compte dels moviments que ha fet l'usuari, una opció de “reset”
4. S'ha de mostrar la imatge que es vol fer perquè el jugador tingui una referència
5. Un cop es posin les imatges al seu lloc es mostrarà la imatge acabada sencera.

![Trencaclosques en marxa](http://imageshack.us/a/img40/3898/nmxl.png "trencaclosques en marxa!")

Com que la llibreria ACM JTF no té cap opció per partir les imatges he implementat el codi necessari per fer-ho: 

    /**
    * Funció que rep com a paràmetre un GImage que té la imatge sencera i 
    * retorna una subimatge definida per les coordenades x, y, w i h
    * @param src Imatge que es vol tallar
    * @param x coordenada x del tall
    * @param y coordenada y del tall
    * @param w amplada del tall
    * @param h altura del tall
    * @return Imatge escapçada
    * 
    *  .--------------------------------.
    *  |   x,y                          |
    *  |     *--------------*           |
    *  |     |               |          |
    *  |     *--------------*           |
    *  |                                |
    *  ---------------------------------.
    */ 	 
    public static GImage tallaImatge(GImage src, int x, int y, int w, int h) {
       Image imatge = src.getImage();
       imatge = Toolkit.getDefaultToolkit().createImage(new          
                     FilteredImageSource(imatge.getSource(),
                     new CropImageFilter(x, y, w, h)));
       return new GImage(imatge);
    }

Activitat
---------------
 1. Desenvolupeu el programa especificat en Java fent servir la llibreria "[acm jtf](http://www-cs-faculty.stanford.edu/~eroberts/jtf/)"

** Solució de la part central a [GitHub](https://github.com/utrescu/Puzzle)... *

---

#FpInfor #Daw #DawMp03 #DawMp03Uf04

* Resultats d'aprenentatge  1.a 1.b 1.c 1.d 1.e 1.f 2.a 2.b 2.c 2.d 2.e 2.f .2.g 2.h 2.j 3.a 3.e 3.g 3.h 3.i
* Continguts 3.1 3.2 3.3
---

###### Autor: Xavier Sala 2013.12.11 08:36:57
###### Editat per: Xavier Sala 2013.12.11 08:42:34
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
