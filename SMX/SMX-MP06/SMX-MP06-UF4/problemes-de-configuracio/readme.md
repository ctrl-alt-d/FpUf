# Problemes de configuració
## SMX-MP06-UF4 - Exercici de seguretat activa.
*Objectius: Entendre alguns dels problemes de seguretat pel mal comportament dels usuaris
Problemes de configuració*

### Contrasenyes per defecte

Un dels problemes de configuració relacionats amb la seguretat més habituals en els sistemes informàtics és instal·lar un dispositiu i posar-lo a funcionar sense més. Això fa que el dispositiu estigui a l'abast de qualsevol que en conegui la contrasenya (cosa especialment perillosa si el dispositiu està connectat a Internet)

Però hi poden haver més problemes:

* Molta de la informació que pot quedar exposada per culpa d'aquest error pot ser denunciable 	
* La seguretat per “ocultació” d'IP no sol ser gaire bona (recordeu el cas del nostre centre) 	
* A més sovint ningú se'n recorda més del dispositiu i per tant no se li apliquen les 	actualitzacions de seguretat amb el perill que això comporat 	

### Shodan (https://www.shodan.io )

Shodan és un motor de recerca que busca tots els dispositius que estan connectats a Internet (càmeres de seguretat, punts d'accés, routers, portes de garatge, neveres control·lades per Internet, dispositius SCADA, etc ... ) i n'accedeix als panells de control, etc... 

![Shodan](https://raw.githubusercontent.com/utrescu/utrescu.github.io/master/images/shodan.png "Shodan")

Això implica que qualsevol amb els mínims coneixements del dispositiu pot entrar-hi i aconseguir-ne el control. Sobretot si s'ha deixat la contrasenya per defecte.

### Càmeres web

Per culpa de les contrasenyes per defecte han aparegut pàgines que recopilen dispositius oberts de tot el món. Un dels exemples més clars són les càmeres per defecte: [Insecam](http://www.insecam.org)

![insecam](https://github.com/utrescu/utrescu.github.io/blob/master/images/insecam.png?raw=true "insecam")


Activitat 	 	 	
---------------------

### Dispositius

En la nostra xarxa hi ha dispositus en les adreces del rang 192.168.0.1 a 192.168.0.19

1. Intenteu descobrir de quina marca són. 		
2. Quina és la combinació usuari/contrasenya que s'instal·la per defecte en els dispositius que tenen algun accés d'usuari privilegiat? Funciona?

### Contrasenyes per defecte en dispositius

3. Localitzeu en una botiga d'Internet dos punt d'accés sense fils de marques diferents 		 		i tres càmeres IP de marques diferents 

4. Busqueu per Internet si podeu trobar les contrasenyes per defecte dels 	dispositius que heu trobat

### Shodan

5. Feu servir Shodan per localitzar alguna càmera web que estigui en funcionament 	

6. Localitzeu el manual de la càmera i intenteu entrar amb l'usuari i la contrasenya per defecte. Funciona?

### Recopilació de contrasenyes per defecte

7. Evidentment a Internet han anat proliferant llistes de contrasenyes per defecte. 	Localitza algunes d'aquestes llistes.

---

#FpInfor #Smx #SmxMp06 #SmxMp06Uf04

---

###### Autor: Xavier Sala 2017.02.06 10:22:27
###### Editat per: Xavier Sala 2017.02.22 11:09:59
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
