# Afegir certificats SSL a lloc web
## SMX-MP06-UF4 - Exercici de seguretat activa.
#Observacions

Podeu escollir el sistema operatiu del servidor amb el que fareu l'activitat.

També podeu descarregar d'Internet màquines virtuals amb Wordpress instal·lat.

Si la màquina virtual ja incorpora certificats SSL autogenerats, heu de fer l'activitat igualment i substituir el certificat que hi ha pel que generareu vosaltres.

Heu de documentar les passes que heu fet per a realitzar el que us demana l'enunciat.

#Activitat

En una màquina virtual amb Wordpress instal·lat...

1. **Genereu un certificat SSL**. Poseu com a informació del certificat el domini de la vostra màquina (p. ex: petitindi.com), el vostre nom i cognoms i el nom de l'institut com a ubicació.

2. Feu els canvis necessaris per a que **el vostre lloc web utilitzi el certificat SSL que heu generat**.

3. **Connecteu al vostre servidor** des d'un navegador amb https:// i **confirmeu l'excepció de seguretat** que us apareix. Pregunta: per què apareix aquest error? Què implica la vostra acció d'afegir una excepció?

4. **Mostreu la informació del certificat** des del navegador amb una captura de pantalla.

5. Esbrineu com podeu **mostrar l’empremta digital del vostre certificat** (*fingerprint*). Pista: s'utilitza la comanda openssl. Compareu l'empremta digital SHA1 obtinguda amb openssl amb l'empremta digital SHA1 que apareix al mostrar informació de la connexió segura amb el navegador.

6. Feu que el servidor web **redirigeixi les connexions HTTP a HTTPS**

---

#FpInfor #Smx #SmxMp06 #SmxMp06Uf04

* Resultats d'aprenentatge 1.f 1.g
---

###### Autor: Carles Caño 2017.02.02 14:52:04
###### Editat per: Carles Caño 2018.02.09 15:49:40
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
