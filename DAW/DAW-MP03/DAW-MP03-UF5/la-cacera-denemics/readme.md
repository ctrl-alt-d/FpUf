# La cacera d'enemics
## DAW-MP03-UF5 - Exercici de POO. Llibreries de classes fonamentals
Objectius: Veure com funciona la serialització a disc d’objectes Java

Serialització d’objectes
-------------------------
Els objectes de Java poden ser convertits a seqüències de bits de manera que podran ser emmagatzemats i recuperats de disc de la mateixa forma que qualsevol altra dada binària fent servir ObjectInputStream i ObjectOutputStream

Per poder ser serialitzats només cal que la seva classe implementi la interfície Serializable:

    class anec implements Serializable {
        String color;
        String crit;		
        String crida() {
            System.out.println(crit);
        }			
    }

Activitat
--------------
Se us demana que feu un programa amb la llibreria ACM que vagi fent que apareguin cada cert temps, soldats amics o enemics per pantalla.

* Els grocs són enemics que s'han d'eliminar fent-hi clic a sobre amb el ratolí
* Els vermells són amics i no s'han de tocar o el programa acabarà

A més el programa ha de portar el compte dels enemics que s'han matat i dels que s'han escapat.

El programa pot acabar al prémer una de les dues tecles següents: 

* **prement la tecla “S”**:  Si es torna a arrancar el programa ha de continuar des d’on estava quan es va aturar.
* **prement la tecla “X”**: Si es torna a iniciar el programa ha de començar de nou.

![exemple](https://raw.githubusercontent.com/XavierSala/M3UF4-2016-09/master/imatges/recorded2.gif)

O bé quan s'hagin escapat "massa" enemics

> Compte! Una de les gràcies de la tasca és que els objectes GImage no són serialitzables ;-)

---

#FpInfor #Daw #DawMp03 #DawMp03Uf05

---

###### Autor: Xavier Sala 2016.11.22 21:56:43
###### Editat per: Xavier Sala 2016.11.23 07:49:27
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
