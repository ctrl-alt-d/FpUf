# Seguretat física en discs durs: control·lar S.M.A.R.T.
## SMX-MP06-UF2 - Exercici de còpies de seguretat.
SMART
És una tecnologia d'anàlisi dels paràmetres dels dics durs que suporten el protocol SMART. Aquesta tecnologia permet saber si un disc dur té indicadors de possibles fallades en el futur.

L'estàndard SMART controla paràmetres com les hores que ha estat en funcionament, la temperatura, el número d'errors que s'hi han produït, etc... 

Tasca
---------
###Linux
1. En un sistema en Linux instal·la les smartmontools
2. Comprova si el disc dur suporta i té activada la tecnologia SMART amb

    sudo smartctl -i /dev/sda

3. Comprova les dades del disc dur i mira quantes hores ha estat iniciat, la temperatura a la que funciona i les vegades que s'ha engegat.
4. Tots els paràmetres del disc es mantenen prop del recomanat? Quin et sembla que està més malament? Quins són els valors en estat de *pre-fail* o pitjor?
5. Inicia un test ràpid de l'estat del disc dur
6. Comprova quins són els resultats del test. L'ha superat? Quin és el resultat?
7. Apunta el valor dels paràmetres que el sistema avisa que estan en pre-fallada. 
8. Estudia si hi ha la possibilitat de centralitzar en una aplicació les dades SMART de varis discs durs de diferents ordinadors. 

###Windows
1. Aconsegueix una eina per obtenir els valors SMART des de Windows i explica com funciona.
2. Si feu les proves en el mateix disc mireu si dóna el mateix resultat que Windows. Què canvia?


---

#FpInfor #Smx #SmxMp06 #SmxMp06Uf02

* Resultats d'aprenentatge 1.1 1.2
* Continguts 1.2 
---

###### Autor: Xavier Sala 2013.10.28 12:13:10
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
