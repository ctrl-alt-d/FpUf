# Atac a contrasenyes de xarxa
## SMX-MP06-UF1 - Exercici de seguretat passiva. 
Introducció
---------------
Una de les activitats que l'increment de les velocitats de connexió a Internet ha provocat ha estat que es poden fer servir sistemes semblants per atacar contrasenyes de xarxa que els que s'han fet servir normalment en local. 

Aquesta “universalització” dels sistemes d'atac fan que sigui molt important comprovar que els usuaris de la xarxa tenen contrasenyes segures. Moltes webs basen la seva seguretat en http forms per rebre les contrasenyes d'usuaris i per això aquestes eines són molt importants per fer prou proves. 

### [THC-HYDRA](http://thc.org/thc-hydra/)
Sol estar en els repositoris de totes les distribucions però també es distribueix amb codi font. Per tant es pot descarregar el codi i compilar-lo.

Hydra permet fer atacs a molts dels protocols de xarxa que demanen usuari i contrasenya: ssh, smb, ftp, etc.. Però un aspecte interessant és que permet atacar les contrasenyes dels formularis de les pàgines web:

    $ ./hydra -l usuari -P fitxer_passwords 127.0.0.1 http-post-form "check.php:user=^USER^&contrasenya=^PASS^:Error"

A part de formularis web pot atacar una gran quantitat de protocols: SSH, SMB, HTTP, FTP, etc...

### [Medusa Parallel Network Login Auditor](http://www.foofus.net/~jmk/medusa/medusa.html) 
Medusa és un programa per fer atacs de força bruta de contrasenyes de xarxa pensat per ser ràpid i modular. Suporta una gran quantitat de serveis de xarxa

### [Bruter](http://sourceforge.net/projects/worawita/)
Bruter és un programa per Windows pensat per comprovar la força de les contrasenyes de xarxa. Permet definir atacs fent servir diccionaris o força bruta

### [Brutus AET](http://www.hoobie.net/brutus/brutus-download.html)
Brutus és una eina per Windows que ens permet fer proves de recuperació de contrasenyes dels serveis HTTP (basic), HTTP (Form), FTP, POP3, Telnet, SMB, Netbus o algun servei personalitzat. 

Es tracta d'un programa molt vell però encara funciona

### [Patator](https://github.com/lanjelot/patator)

Patator és un programa multifils fet en Python i que és de més recent creació que els anteriors. Intenta ser més flexible que els altres programes d’atac per xarxa. També és modular i cada un dels seus mòduls sol tenir moltes opcions diferents.

La llista de protocols i programes que pot atacar és bastant extensa: FTP, SSH, Telnet, SMTP, FINGER, HTTP, AJP, POP, IMAP, SMB, LDAP, RLOGIN, VMAUTH, MSSQL, ORACLE, MYSQL, RDP, PGSQL, RDP, DNS, SNMP, IKE, ZIP, JAVA KEYSTORE,  ...


Tasca
----------
Navegant per Internet us heu trobat unes adreces del domini del centre que us semblen prou atractives.... Rere una pantalla que demana usuari i contrasenya sempre hi deu haver alguna cosa interessant

* [http://192.168.4.1/projectes](http://192.168.4.1/projectes) (només des de la xarxa del centre)
* [http://projectes.cendrassos.net/seguretat/](http://projectes.cendrassos.net/seguretat/) (accessible des d'Internet)

Us proposeu investigar si aconseguiu descobrir què és el que estan emmagatzemant els professors en les seves zones privades

1. Investigació prèvia.
    * Quins són els usuaris d'aquestes pàgines? 
    * Quin usuari tenen per accedir al sistema?
2. Atac
    * Expliqueu detalladament quins són els mètodes i els atacs que heu intentat (encara que no hagin tingut èxit)
    * Quina és la contrasenya i la informació secreta dels usuaris que heu pogut descobrir

Podeu fer servir l'aplicació que vulgueu per fer l'atac. Si ho feu amb més de una se us tindrà en compte

---

#FpInfor #Smx #SmxMp06 #SmxMp06Uf01

* Resultats d'aprenentatge 1.8
* Continguts 1.7
---

###### Autor: Xavier Sala 2013.10.28 11:56:33
###### Editat per: Xavier Sala 2017.10.09 21:41:09
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
