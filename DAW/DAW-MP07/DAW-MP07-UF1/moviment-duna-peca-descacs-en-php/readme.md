# Moviment d'una peça d'escacs en PHP
## DAW-MP07-UF1 - Exercici de Desenvolupament web en entorn servidor.
Realitzarem un taulell d'escacs amb certa funcionalitat del joc. No el farem complert ja que és un projecte força més complex, però sí que podrem posar una figura al taulell, moure-la, i comprovar que el moviment és correcte.

Guia:

1. Crea el taulell (amb bucles, res de predefinits) i amb les cel·les blanques i negres adequadament.
2. Numera les files amb lletres (A-H) i les columnes amb nombres.
3. Introduirem una peça a la variable de sessió, per exemple ```$_SESSION["rei_n"]``` (rei negre), i assigna-la a alguna cel·la de sortida. NOTA: inicialment és més fàcil fer-ho amb les files i columnes com a números (passant de les files amb lletres).
4. Mostra la cel·la al taulell.
4. Fes un formulari amb un input on introduirem la casella de destí de la peça a moure. A l'enviar el formulari la peça ha de desplaçar-se al nou lloc (modificant la variable ```$_SESSION```).
5. Mou la peça a la posició que l'usuari indiqui.
6. Comprova que la cel·la destí introduïda no surt del taulell.
7. Comprova que la cel·la de destí compleix amb les regles del joc dels escacs (dependrà de la peça que hagis triat).
8. Canvia els índex de fila a lletres. Per indicar la cel·la destí hauria de ser A1, B5, F7, per exemple.


---

#FpInfor #Daw #DawMp07 #DawMp07Uf01

* Resultats d'aprenentatge 2.x 3.x 4.x
---

###### Autor: Enric Mieza 2016.10.20 13:41:57
###### Editat per: Enric Mieza 2016.10.20 13:41:57
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
