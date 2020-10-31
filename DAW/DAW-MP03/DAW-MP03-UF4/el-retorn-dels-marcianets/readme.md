# El retorn dels marcianets
## DAW-MP03-UF4 - Exercici de Programació orientada a objectes. Fonaments
Aprofitarem el funcionament de l'herència per desenvolupar un programa que ens permeti crear un matamarcians clàssic que podrem expandir fàcilment

> *“Els Shoot'em up, coneguts popularment com a ”marcianets” o “matamarcians” són un tipus de videojoc d'acció consistents a controlar un jugador (guerrer, nau espacial o similar) que ha de sobreviure a l'atac massiu d'enemics mentre els dispara i mata, usualment esquivant obstacles.” Wikipèdia* 

![Marcianets](http://img31.imageshack.us/img31/6623/6dl4.png "Marcianets")

Activitat
----------------------
Desenvolupeu un programa fent servir herència que permeti crear un matamarcians fent servir les llibreries ACM

El jugador control·larà la nau amb el teclat:

* Només es podrà moure lateralment 
* Tindrà un màxim de sis bales però podrà recarregar amb una tecla

Hi hauran diferents tipus de marcians que es comportaran de forma diferent:

* En general els marcians es mouran lateralment d'esquerra a dreta
* Si una bala toca el marcià, aquest es mor i la bala desapareix...
* Les bales desapareixen tant si toquen un marcià com si arriben al límit superior de la pantalla

Tipus de marcians
---------------------------
Podeu definir els tipus de marcians que us semblin però per si algú té poca imaginació hi posarem: 

1. Marcians reclutes: Només es mouen d'esquerra a dreta i disparen molt de tant en tant una bala cap abaix (0,01 per mil)
2. Marcians reforçats: Per matar-los cal que els toquin tres bales. Quan han rebut una bala canvia el seu color
3. Marcians kamikazes: En el moment en que s'activen es llancen cap a baix a tota velocitat! L'activació també serà aleatòria
4. Marcians mare: De tant en tant creen una nau nova  dels tipus anteriors

> No és obligatori quedar-se amb el mínim demanat. Es permet afegir-hi més coses per incrementar les funcionalitats del programa. Qualsevol millora en el programa que faci que l'aspecte final o el funcionament sigui més “professional” contribuirà a que la nota sigui superior.

Exemple a [GitHub](https://github.com/utrescu/Marcianets). L'exemple fa servir Singleton per simplificar però recordeu: *Singletons are evil*

---

#FpInfor #Daw #DawMp03 #DawMp03Uf04

* Resultats d'aprenentatge 1.a 1.b 1.c 1.d 1.e 1.f 2.a 2.b 2.c 2.d 2.e 2.f .2.g 2.h 2.j 3.a 3.e 3.g 3.h 3.i
* Continguts 3.1 3.2 3.3
---

###### Autor: Xavier Sala 2013.11.27 11:22:13
###### Editat per: Xavier Sala 2013.11.27 11:32:28
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
