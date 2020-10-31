# Campionat del món de tres en ratlla
## DAW-MP03-UF5 - Exercici de POO. Llibreries de classes fonamentals
Objectius: Treballar amb taules bidimensionals

Campionat del món de 3 en ratlla
==========================================

Durant els darrers anys la Federació del món de TicTacToe (encarregat dels campionats de 3 en ratlla i del 4 en ratlla) ha vist com els altres esports de taula s’han fet cada vegada més populars ( els escacs, el Go, el backgammon, les dames, …)

![Campionat de Tres en ratlla](https://raw.githubusercontent.com/utrescu/utrescu.github.io/master/images/tictactoe1.png)

Han decidit que això s’ha d’acabar i han organitzat un campionat de TicTacToe en el que hi participaran 80 milions de jugadors. La seva esperança és que això faci que tots els altres jocs de taula quedin enrere!

Activitat
------------------

1. El problema és que no tenen prou arbitres per arbitrar els campionats i per això han decidit fer que l’arbitre sigui un ordinador. 

![Tres en ratlla](https://raw.githubusercontent.com/utrescu/utrescu.github.io/master/images/tictactoe2.png)

S’aniran rebent taulers, tal com estan en un moment determinat i el programa ha d'anar dient: 

* Si la partida no s’ha acabat
* Si ha guanyat el jugador ‘O’ o el ‘X’ 
* Si algú ha fet trampes (perquè hi ha més d’un guanyador)

Per fer la connexió amb el servidor de partides us proporcionen una classe que se n’encarrega de fer la connexió amb el servidor [Descarregar la llibreria](https://drive.google.com/file/d/0BxakKCNfTojqYzJQTXl3RkVOTFk/view?usp=sharing)

S'ha d'afegir la llibreria al projecte i crear l'objecte `TicTacToe`. Després només cal anar cridant `generar()` per rebre els taulers de 3x3 en un array bidimensional d'Strings (cada vegada que cridem generar rebrem un tauler diferent)

    TicTacToe toe = new TicTacToe();    
    String[][] tauler = toe.generar();

També es poden rebre taulers d'altres competicions, com la de 5x6 simplement posant paràmetres a `generar(ample, alt)`

    String[][] tauler = toe.generar(5,6);

El programa ha d'analitzar l'array rebut per saber si ha guanyat algú, la partida encara no ha acabat, etc..

### Ajudes

Es pot veure una representació gràfica del tauler d'aquesta forma: 

    for(int i=0; i < tauler.length; i++) {
        System.out.println(Arrays.toString(tauler[i]));
    }

Que imprimirà una cosa com aquesta:

    [O, O, O]
    [X,  ,  ]
    [X, X, X]

Amb aquest tauler el programa ha de dir: 

    TRAMPES! GUANYEN TOTS DOS

I amb aquest: 

    [O, O, X]
    [X, X,  ]
    [X, O, O]

El programa ha de dir: 

    GUANYA 'X'

---

#FpInfor #Daw #DawMp03 #DawMp03Uf05

---

###### Autor: Xavier Sala 2017.10.02 20:47:33
###### Editat per: Xavier Sala 2017.10.17 09:01:56
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
