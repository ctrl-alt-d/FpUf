# Exercici: Quin dia vas néixer?
## DAW-MP03-UF1 - Exercici de Programació estructurada
### Quin dia vas néixer?

Aquesta tasca té per objectiu treballar les estructures condicionals i repetitives.

La "**Congruència de Zeller**" és un algorisme per calcular el dia de la setmana d'una data concreta.

Té un algorisme una mica complex, però hi ha una versió bàsica aplicable que veiem a continuació.

Donada una data: dia/mes/any, l'algorisme és el següent:

     d = (dia + y + y/4 - y/100 + y/400 + (31*m)/12) mod 7

     On:
		a = (14 - mes) / 12
		y = any - a
		m = mes + 12 * a - 2

El resultat (“d”) correspondrà al dia de la setmana: 0 (diumenge), 1 (dilluns) …..... 6 (dissabte).

Fer un programa que demani una data de naixement (de forma separada). Un número pel dia, un mes (en text) i un número per a l'any i que retorni el dia de la setmana que li correspon (dilluns, dimarts, .....).

**Si per exemple l'usuari entra:**

		Dia: 14
		Mes: gener
		Any: 1973
**La sortida serà aquesta:**

		El teu aniversari, dia 14 de gener de 1973 va caure en: Diumenge

Nota: A partir de Java 7, la sentència "switch" permet "Strings". Si la versió del JDK és anterior, recordeu que en Java, “String” és una classe i per tant té mètodes. 
Un d'ells és el mètode “boolean equals(String a)” que retorna true si el String sobre el que s'aplica el mètode és igual a l'String que se li passa com a paràmetre.
A partir de Java 7, la sentència "switch" permet Strings per tant  

Fer modificacions al programa per tal que calculi els anomenats "aniversaris reals".
Un aniversari es diu real si la data coincideix amb el dia de la setmana en què va ser per primera vegada.

**Si per exemple l'aniversari entrat per l'usuari és el 14 de gener de 1973, el programa ha de mostrar:**

		El teu aniversari, dia 14 de gener de 1973 va caure en: Diumenge
		Els anteriors aniversaris reals van ser al:
		1979 1990 1996 2001 2007 , tens 5 anys!!!

Per fer comprovacions pots utilitzar aquest enllaç: [http://www.miverdaderocumpleanos.com/](http://www.miverdaderocumpleanos.com/)

---

#FpInfor #Daw #Dam #Asix #AsixMp03 #DamMp03 #DawMp03 #AsixMp03Uf01 #DamMp03Uf01 #DawMp03Uf01

* Resultats d'aprenentatge 1.a 1.b 1.c 1.d 1.e 1.f 1.g 1.h 2.a 2.b 2.c 2.d 2.e 2.f 2.g 2.h 2.i 2.j
* Continguts 1.1  1.2  1.3  1.4  1.5  1.6  1.7  1.8  2.1  2.2  2.3  2.4  2.5  2.6 2.7 2.8 2.9 2.10 2.11 2.12 2.13
---

###### Autor: Juaky 2015.10.29 11:33:22
###### Editat per: Juaky 2015.11.03 10:13:41
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
