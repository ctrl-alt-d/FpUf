# Atac a contrasenyes de Windows
## SMX-MP06-UF1 - Exercici de seguretat passiva. 
Introducció
----------
Una de les formes d'accedir a un sistema és conèixer les contrasenyes dels usuaris que conté. Un atacant intentarà emportar-se les contrasenyes al seu equip per evitar ser detectat mentre prova les contrasenyes.

El sistema operatiu Windows les protegeix de dues formes: 

1. Mentre està funcionant protegeix els fitxers de contrasenyes perquè cap usuari no els pugui copiar (ni l'administrador). 
2. Les contrasenyes es guarden en forma de hash i no en text planer

Per saltar-se la protecció anti copia es tenen diverses possibilitats: 

* Iniciar el sistema amb un LiveCD per evitar les proteccions. Les contrasenyes en els fitxers en els sistemes Windows estan en el fitxers de C:\WINDOWS\SYSTEM32\CONFIG: SAM, SYSTEM i SECURITY. 
* Extreure les contrasenyes de les llibreries d'autentificació del sistema amb programes com pwdump7 o fgdump (cal un compte d'administració)

I per descobrir les contrasenyes a partir del hash es poden fer servir programes com Cain & Abel, L0pthcrack, SamInside, etc ... o fins i tot es pot fer des de Linux amb John the ripper

Alguns dels programes permeten a l'administrador recuperar les contrasenyes codificades obtenint-les de processos privilegiats. D'aquesta forma no cal fer el procediment d'arrancar amb un LiveCD perquè es poden obtenir directament

###Obtenir les contrasenyes en planer
Una possibilitat alternativa consisteix en aprofitar-se d'alguna de les llibreries del sistema que mantenen les contrasenyes dels usuaris en planer. D'aquesta forma no s'obtindrà el hash de la contrasenya sinó la contrasenya de l'usuari.

L'únic requeriment sol ser que caldran privilegis d'administració per entrar en el sistema i que caldrà que els usuaris hagin entrat des de que el sistema s'hagi iniciat.

En aquest punt destaquen eines com Mimikatz o WCE (Windows Credentials Editor)

    C:\> wce -w


Tasca
----------

1. En una màquina virtual amb Windows afegiu-hi 10 usuaris

2. Explica detalladament  algun procediment que  pot fer servir un administrador per per recuperar els fitxers de contrasenyes d'un sistema en Windows (feu la prova amb una màquina virtual mostrant els resultats)

3. Un atacant que desconeix la contrasenya de l'administrador. Com ho pot fer per emportar-se els fitxers de contrasenyes?

4. Intenteu descobrir les contrasenyes del sistema amb algun programa d'atac de contrasenyes fent servir un diccionari.Expliqueu com es fa en el programa que hageu triat per atacar els fitxers de contrasenyes, els diccionaris que heu fet servir i el seu resultat

5. Si alguna contrasenya no es troba fes servir l'atac de força bruta durant uns minuts.

6. Entreu en el sistema amb alguns dels usuaris dels que heu trobat la contrasenya i comproveu que funciona

7. Des del compte d'administrador feu servir el programa Windows Credentials Editor (WCE), vigileu que sigui la darrera versió, per veure si podeu recuperar contrasenyes del sistema. Quines troba?

---

#FpInfor #Smx #SmxMp06 #SmxMp06Uf01

* Resultats d'aprenentatge 1.8
* Continguts 1.7
---

###### Autor: Xavier Sala 2013.10.28 11:38:01
###### Editat per: Xavier Sala 2013.10.28 11:59:09
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
