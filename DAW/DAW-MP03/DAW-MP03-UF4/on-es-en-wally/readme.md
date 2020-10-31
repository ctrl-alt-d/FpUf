# On és en Wally?
## DAW-MP03-UF4 - Exercici de Programació orientada a objectes. Fonaments
On és en Wally?
=========================
Tothom ha sentit a parlar del passatemps conegut com “On és en Wally?” que consisteix en localitzar en Wally en un dibuix

![Wally](https://raw.githubusercontent.com/XavierSala/M3UF4-2016-08/master/imatges/wally.png)

Però el que la gent no sap és que aquest passatemps també es pot fer en ASCII! Donat un fitxer qualsevol s’hi ha de localitzar la cadena *“Wally”* 


    Lorem ipsum dolor sit amet, consectetur adipiscing elit.
    Curabitur consectetur, eros ut auctor interdum, turpis diam
    rutrum nulla, in cursus erat mauris nec tellus. In ut luctus
    massa, et sodales lectus. Proin leo enim, eleifend vitae
    malesuada nec, pulvinar at nisi. Nunc in mi nec libero
    porttitor convallis. Curabitur dignissim urna ut nulla mattis
    sagittis. Vivamus efficitur felis tristique enim tempor 
    eleifend. Vestibulum a massa consectetur, malesuada tortor sit 
    amet, consectetur dolor.Wally Praesent posuere lectus vel odio 
    luctus, a eleifend lacus vestibulum. Nam malesuada aliquam erat 
    nec condimentum. Proin id augue eget est pellentesque viverra 
    sit amet et odio. Interdum.


S’ha de trobar la paraula que pot estar envoltada amb algun dels separadors estàndards: punt, coma o espais:

* “ Wally.”, “.Wally “, “.Wally,” → OK
* “ Wallypop”, “-Wally “, “WallyWally” → NO

Activitat
----------------
Se us demana que feu un programa que agafi un fitxer de text i ens digui en quina fila i columna es troba en “Wally” (començant per zero). En cas de que surti més d’una vegada ha de donar “FITXER INCORRECTE”


Exemple:

Amb aquest fitxer: 

    Patata Bicicleta
    Festa Wally tinta
    Mono Bolets, vi

Donarà:

   En Wally és a la fila 1 columna 7


Fitxers de proves: [Descarregar](https://drive.google.com/file/d/0B1USLpQ7TipGS0VxQWRuSTVrSms/view?usp=sharing)

Els resultats són: 

    Fitxer: wally.txt --> En Wally és a la línia 1 columna 3
    Fitxer: wallyno.txt --> En Wally no hi és
    Fitxer: fitxerinexistent.txt --> No existeix el fitxer
    Fitxer: doswallys.txt --> FITXER INCORRECTE
    Fitxer: wallyprincipi.txt --> En Wally és a la línia 0 columna 0
    Fitxer: wallyfinal.txt --> En Wally és a la línia 4 columna 9
    Fitxer: treswallys.txt --> FITXER INCORRECTE
    Fitxer: fitxerbuit.txt --> En Wally no hi és
    Fitxer: wallysaltdelinia.txt --> En Wally és a la línia 2 columna 9

---

#FpInfor #Daw #DawMp03 #DawMp03Uf04

---

###### Autor: Xavier Sala 2016.11.14 23:23:40
###### Editat per: Xavier Sala 2016.11.15 13:25:55
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
