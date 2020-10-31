# Política de contrasenyes en Linux
## SMX-MP06-UF1 - Exercici de seguretat passiva. 
Introducció
---------------
En Linux la definició de polítiques es fa en diferents arxius però la part més important està en els mòduls PAM. Per definir una política senzilla que només necessiti la llargada mínima de contrasenya es pot fer servir el mòdul **pam_unix.so** 

La configuració dels mòduls PAM normalment només consisteix en escriure o modificar línies en el directori /etc/pam.d

> Atenció: Si cal afegir línies en un fitxer PAM el lloc en el que es posen les línies és molt important. Fer-ho malament pot fer que no es pugui entrar més en el sistema o que es pugui entrar sempre...  

S'edita l'arxiu /etc/pam.d/common-password i es busca la línia que defineix el mòdul pam_unix.so. En aquesta línia hi definim la llargada mínima amb “min=”

###Mòduls PAM
Hi ha una gran quantitat de mòduls PAM que es poden fer servir en Linux. Cada mòdul aporta alguns mètodes d'identificació, autentificació o autorització al sistema:

* pam_cracklib, Reforça les contrasenyes dels usuaris impedint-los posar contrasenyes senzilles.  Permet definir històric de contrasenyes
* pam_passwdqc, Permet definir la complexitat de les  contrasenyes del sistema
* pam_limits, Límita el número de recursos que pot fer servir un usuari
* pam_motd, Mostra un missatge a l'usuari que entra al sistema
* pam_time, Permet limitar l'accés dels usuaris a determinades hores
* pam_tally, Permet bloquejar un compte si un usuari ha fallat la contrasenya 

Alguns d'aquests mòduls estan disponibles per defecte mentre que d'altres requereixen que el mòdul sigui instal·lat. Per exemple, el mòdul pam_cracklib no sol venir instal·lat i cal fer-ho manualment.

Es poden trobar tots els mòduls pam d'un sistema en Ubuntu buscant en els paquets els que comencen per “libpam” 

    # apt-cache search ^libpam
    ...  
    libpam-cap - PAM module for implementing capabilities 
    libpam-ck-connector - ConsoleKit PAM module 
    libpam-cracklib - PAM module to enable cracklib support 
    libpam-doc - Documentation of PAM 
    ...

###Pam_cracklib
El mòdul pam_cracklib ofereix la possibilitat de forçar als usuaris a tenir contrasenyes més complexes. Per fer-ho es poden afegir tota una sèrie de paràmetres que indiquen la llargada mínima, la complexitat de la contrasenya (quantes majúscules, minúscules, números i símbols ha de tenir la contrasenya) i com han de diferir les contrasenyes)

Ex. Volem una contrasenya amb almenys 1 caràcter en minúscules, un en majúscules i un número i que no s'assembli a l'anterior:

Només cal buscar el fitxer /etc/pam.d/common-password i localitzar la línia que té pam_cracklib.so i modificar-la d'aquesta forma (el que està entre parèntesi sobra): 

   password    requisite   pam_cracklib.so retry=3 minlen=12 lcredit=1 (minúscules)  ucredit=1 (majúscules)  dcredit=1 (dígits) ocredit=0 (altres) difok=2 (diferència mínima amb l'anterior)

###Pam_tally
El mòdul pam_tally és el responsable de bloquejar els comptes dels usuaris que han fallat un número determinat de vegades les contrasenyes

Generalment està instal·lat per defecte i per configurar-lo només cal “afegir” una línia en un arxiu del /etc/pam.d/

Recordeu que podeu canviar d'un usuari a un altre fent servir la comanda su (no cal sortir i entrar de l'entorn gràfic per fer les proves)

    manolo@Festival$ su federicu
    Password:
    federicu@Festival$ 


###Login.defs
La caducitat per defecte de les contrasenyes es poden definir en l'arxiu /etc/login.defs i se'n pot veure i canviar qualsevol aspecte amb la comanda chage

    $ chage -l federicu
    Last password change					      : Sep 08, 2010
    Password expires					            : Dec 07, 2010
    Password inactive					            : Jan 06, 2011
    Account expires						      : Sep 09, 2010
    Minimum number of days between password change		: 5
    Maximum number of days between password change		: 90
    Number of days of warning before password expires	: 14

Chage també permet modificar-ho: 

    $ sudo chage -E 06/30/2011 -m 5 -M 90 -I 30 -W 14 federicu

Per obtenir ajuda en una comanda de Linux es pot fer servir la comanda man. Per exemple man chage



Activitat
----------------
###Política de contrasenyes en Linux

1. En una màquina virtual en Linux definiu-hi tres usuaris amb contrasenyes simples: “12345”, “1Ab”, “patata”

2. Definiu una política de contrasenyes que defineixi:

* Llargada de la contrasenya: 9 caràcters com a mínim
* Caducitat: Caduquen cada mes
* Complexitat de la contrasenya: Lletres majúscules, minúscules i números
* Bloqueig del compte: 3 fallades

3. Intenteu crear un usuari nou amb una contrasenya senzilla que no compleixi la política i comproveu que el sistema no el deixa crear

4. Intenteu entrar amb un dels usuaris creats anteriorment. Què fa el sistema? 

5. Amb un usuari qualsevol intenteu entrar en el sistema fallant la contrasenya 4 vegades. Què passa?

6. Voleu que a un usuari li caduqui la contrasenya d'aquí dos dies. Com es pot fer?


---

#FpInfor #Smx #SmxMp06 #SmxMp06Uf01

* Resultats d'aprenentatge 1.7
* Continguts 1.6 
---

###### Autor: Xavier Sala 2013.10.28 10:50:13
###### Editat per: Xavier Sala 2013.10.28 10:50:13
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
