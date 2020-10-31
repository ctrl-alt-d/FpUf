# Exercici: Ús de Parametrització
## DAW-MP03-UF2 - Exercici de Disseny modular
![enter image description here](http://www.lasprovincias.es/las_provincias/noticias/201412/18/media/cortadas/joker-prmitiva-18diciembre--575x323.jpg "enter image title here")

### ** Explicació del joc  **  


La Lotería Primitiva es un juego de azar regulado por Loterías y Apuestas del Estado que consiste en elegir 6 números diferentes entre 1 y 49, con el objetivo de acertar la Combinación Ganadora en el sorteo correspondiente, formada por 6 bolas de las 49 que se extraen del bombo. También se extrae una bola extra como número complementario, y otra bola de un bombo aparte, entre el 0 y el 9, que hace de número de «reintegro».

Existe un escalado de premios dependiendo del número de aciertos con respecto a las bolas principales y la complementaria que coincidan con los 6 números de cada participación, y/o la de reintegro.

En cuanto al número complementario, el apostante no puede marcar ningún número complementario, sino que ese número se contará dentro de los seis que elija como su combinación, y sólo en el caso de que los otros cinco correspondan a la combinación principal; es decir, el complementario sólo se utiliza en la 2ª Categoría de premios (ver a continuación las categorias existentes).

Existen varias categorías de acertantes dependiendo de los números que se aciertan.

*    Categoría Especial: Acertar los seis números de la combinación ganadora y el reintegro.
*    1ª Categoría: Acertar los seis números de la combinación ganadora
*    2ª Categoría: Acertar cinco números de la combinación y el número complementario
*    3ª Categoría: Acertar cinco números de la combinación
*    4ª Categoría: Acertar cuatro números de la combinación
*    5ª Categoría: Acertar tres números de la combinación
*    Reintegro: Acertar el número del reintegro

*(font Wikipedia)*

### **Tasca a realitzar**


Fer una aplicació que simuli el joc de la primitiva utilitzant parametrització als mètodes.
En primer lloc es demanarà a l'usuari que entri els 7 números amb els que vol jugar. A continuació es determinarà si té premi i quin és en aquest cas, a partir de 8 números generats de forma aleatòria (els 6 corresponents a la combinació guanyadora, el complementari i el corresponent al reintegrament).

### **Exemple d'execució:**


>Escriu els 6 números corresponents a la combinació (1-49):

>5 7 37 42 43 8

>Escriu el número corresponent al reintegrament (0-9):

>6

>**La combinació guanyadora és aquesta:**

>**37 43 12 3 1 8      Complementari: 18      Reintegrament: 1**

>Has encertat els números: 37, 43 i 8. No has encertat el reintegrament.

>Enhorabona!! Has aconseguit un premi de 5ª categoria.

Nota: Per generar números aleatoris utilitzar el mètode `nextInt(int n)` de la classe `java.util.Random`
Tenir en compte que els números que es vagin generant de forma aleatòria (corresponents a la combinació guanyadora) no es poden repetir. Si un número s'ha extret del bombo, no pot tornar a sortir!!!
De igual forma en el cas de la combinació entrada per l'usuari, no es poden repetir números!!!!

**Possibles millores:**

- Assignar premis a les diferents categories.

- Crear entorn gràfic utilitzant les [ACM Java Libraries](http://cs.stanford.edu/people/eroberts/jtf/)

- Realitzar més d'una aposta en cada jugada.

- Assignar import a cada aposta realitzada.




---

#FpInfor #Daw #Dam #Asix #AsixMp03 #DamMp03 #DawMp03 #DawMp03Uf02 #AsixMp03Uf02 #DamMp03Uf02

* Resultats d'aprenentatge 1.a 1.b 1.c 1.d 1.e 1.f 1.g 1.h 2.a 2.b 2.c 2.d 2.e 2.f 2.g 2.h 2.i 2.j
* Continguts 1.1  1.2  1.3  1.4  1.5  1.6  1.7  1.8  2.1  2.2  2.3  2.4  2.5  2.6 2.7 2.8 2.9 2.10 2.11 2.12 2.13
---

###### Autor: Juaky 2015.10.01 11:02:29
###### Editat per: daniel herrera 2015.10.05 08:20:43
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
