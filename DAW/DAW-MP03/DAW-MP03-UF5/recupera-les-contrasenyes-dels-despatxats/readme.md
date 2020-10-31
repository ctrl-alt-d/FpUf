# Recupera les contrasenyes dels despatxats
## DAW-MP03-UF5 - Exercici de POO. Llibreries de classes fonamentals
En la vostra empresa s’ha despatxat massivament a molts treballadors, entre ells l’administrador informàtic, i abans de fer-los marxar se’n van oblidar de demanar-los les contrasenyes. 

![El director té mal caràcter](https://raw.githubusercontent.com/utrescu/utrescu.github.io/master/images/kefe.png)

El problema és que ara no es poden recuperar els fitxers amb els que estaven treballant els treballadors abans que els despatxessin. I com que al director li fa vergonya trucar a la gent que va despatxar per demanar-los la contrasenya, es veu que van acabar malament, us ha demanat que li feu un programa que intenti descobrir les contrasenyes dels fitxers de contrasenyes dels despatxats.

El sistema on treballaven els treballadors despatxats és un Linux. En Linux les contrasenyes estan en el fitxer /etc/shadow i tenen un format estàndard:

![contrasenyes](https://raw.githubusercontent.com/utrescu/utrescu.github.io/master/images/shadow.png)

### Llibreria de suport
Heu trobat una llibreria que us permet comprovar les contrasenyes 

[Descarregar](https://drive.google.com/file/d/0BxakKCNfTojqUU1USmpVRy0tZ2c/view?usp=sharing "llibreria")

La llibreria té tres mètodes que ens interessen:

* **boolean comprova(String usuari, String contrasenya)** : Diu si la contrasenya d’aquest usuari és correcta o no
* **String[] getUsuaris()**: Retorna la llista d’usuaris del sistema
* **void afegirUsuari(String usuari, String hash)**: Permet afegir un usuari a la llista dels que s’han de descobrir. S’hi passa el nom de l’usuari i la codificació de la contrasenya

El funcionament del programa, sembla que l’hagi fet un professor per forçar als alumnes a treballar, consisteix en:

1. Obtenir l'usuari i la contrasenya xifrada dels treballadors i entrar-les amb `afegirUsuari`. 
2. Executar el mètode comprova amb un dels usuaris i una contrasenya per saber si l’hem encertat. Aquest mètode es pot repetir tantes vegades com calgui fins que es trobi la contrasenya

Per exemple entrem l’usuari ‘pere’ i comprovem si la contrasenya és ‘password’ o no:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~java
ComprovaContrasenya prova = new ComprovaContrasenya();

prova.afegirUsuari("Pere", "$6$hJFtcavV$OSEDo7JuAbTuK2Q…";

if  (prova.comprova("Pere", "password")) {
	System.out.println("LA CONTRASENYA ÉS password");
}
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~	    	

Tasca
------------------

Es tracta de fer un programa que vagi provant les contrasenyes que li proporcionarem contra els usuaris del sistema fins que els trobi o bé s'acabin les contrasenyes a provar.

El fitxer amb les contrasenyes a descobrir és aquest 

[Descarregar](https://drive.google.com/file/d/0BxakKCNfTojqbWplU1FfRldDVDA/view?usp=sharing "fitxer amb les contrasenyes")

> Compte que hi ha usuaris que no tenen contrasenya

El programa ha de permetre rebre un fitxer amb un diccionari de contrasenyes per provar: 

    bolet
    sabata
    aaaaaa
    sombrero
    patata
    barretina

Per exemple aquí hi ha exemples de diccionaris (on hi són les contrasenyes a trobar) 

[Descarregar](https://drive.google.com/file/d/0BxakKCNfTojqWkNJQ2luRldTM00/view?usp=sharing "diccionaris")

O sigui que cal fer un programa que li passem un fitxer de contrasenyes, un diccionari i ens diu les contrasenyes que hi ha trobat:

![contrasenyes](https://raw.githubusercontent.com/utrescu/utrescu.github.io/master/images/contrasenyes.gif "atac")

---

#FpInfor #Daw #DawMp03 #DawMp03Uf05

---

###### Autor: Xavier Sala 2017.10.26 09:42:32
###### Editat per: Xavier Sala 2017.11.09 10:06:49
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
