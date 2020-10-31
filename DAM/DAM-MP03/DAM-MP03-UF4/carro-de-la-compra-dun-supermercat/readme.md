# Carro de la compra d'un supermercat
## DAM-MP03-UF4 - Exercici de Programació orientada a objectes. Fonaments
## Enunciat

Una important empresa de supermercats us demana que li dissenyeu una aplicació revolucionaria! Consisteix en fer que el carro de la compra mostri, en temps real, el preu dels productes que s'hi van introduint.

L'empresa us indica que l'aplicació, de moment, només ha de permetre gestionar les dades d'uns quants dels seus productes: alimentació, tèxtil i electrònica. Aquests productes tenen unes característiques comuns (preu, nom i codi de barres) i un conjunt de característiques específiques de cada tipus de producte:

* **Alimentació**: data de caducitat.

    * El preu d'aquest tipus de producte varia en funció dels dies que falten per caducar, segons la fórmula: `preu - preu*(1/(dataCaducitat-dataActual+1)) +
(preu * 0.1)`

* **Tèxtil**: composició tèxtil (text)

* **Electrònica**: dies de garantia (numèric)

    *  El preu d'aquest tipus de producte varia en funció dels dies que té de garantia segons la fòrmula: `preu + preu*(diesGarantia/365)*0.1`


L'aplicació que heu de fer ha de permetre emmagatzemar tots els productes que s'hi van introduint (màxim 100 productes) i calcular-ne el preu. També ha de permetre que, en passar per caixa, es generi el tiquet de compra i es buidi el carro.

Com que això de la programació orientada a objectes és una metodologia que té molts avantatges decidiu programar-ho en Java.

##Es demana

* 1) Identifica i codifica les classes del sistema. Es demana:

    * Esquema de les classes (notació UML).

* 2) Fer un programa principal que faci ús de les classes dissenyades. La descripció del que ha de fer aquest programa s'explica a continuació. El programa ha de tenir un menú d'opcions com el següent:

    * **1. Introduir producte** En escollir aquesta opció s'ha de mostrar un altre menú d'opcions:*Quin tipus de producte vols afegir?*

        *  **1.1. Alimentació** En escollir aquesta opció s'ha de demanar que s'entri per teclat les dades d'un producte del tipus Alimentació

        * **1.2. Tèxtil** En escollir aquesta opció s'ha de demanar que s'entri per teclat les dades d'un producte del tipus Tèxtil

        * **1.3. Electrònica** En escollir aquesta opció s'ha de demanar que s'entri per teclat les dades d'un producte del tipus Electrònica

        * **1.0. Tornar** En escollir aquesta opció s'ha de tornar al menú principal

    * **2. Passar per caixa** En escollir aquesta opció se simula que es passen tots els productes per caixa i es genera el tiquet. 

        * El tiquet (es mostra per pantalla) ha de mostrar una capçalera amb: data de la compra i nom del supermercat. A continuació es mostra el detall amb: nom del producte, unitats introduïdes al carro, preu unitari i preu total.  Finalment ha de calcular la suma total a pagar. 

        * Si s'han introduït dos productes iguals (tenen el mateix codi de barres i el mateix preu unitari) només es mostrarà una vegada, amb la quantitat total d'aquell producte, és a dir, les unitats. 

        * Aquesta opció també implica buidar el carro de la compra.

    * **3. Mostrar carro de la compra**  En escollir aquesta opció es mostra un llistat amb la descripció i quantitat de cada producte (sense preu) que hi ha dins el carro del a compra. En aquest cas, si hi ha productes repetits ho seran si tenen el mateix codi de barres (no cal mirar el preu unitari).

    * **0. Sortir**  En escollir aquesta opció es tanca l'aplicació.




---

#FpInfor #Dam #DamMp03 #DamMp03Uf04

* Resultats d'aprenentatge 2a 2b 2c 2d 2e 2f 2g 2h 2i 2j 3a 3b 3c 3d 3e 3f 3g 3h 3i 3j
* Continguts 2.1 2.2 2.3 2.4.2.5. 2.6. 2.7 2.8 3.1 3.2 3.3 3.4 3.5 3.6
---

###### Autor: Marc Nicolau 2015.10.30 15:14:29
###### Editat per: daniel herrera 2015.11.04 21:01:35
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
