# Verificar l'autenticitat i la integritat de les aplicacions a instal·lar
## SMX-MP06-UF4 - Exercici de seguretat activa.
#Activitat

1. Des d'una màquina GNU/Linux amb gpg instal·lada, descarrega els següents fitxers:

    (a) [turnkey-wordpress-14.2-jessie-amd64.ova](https://www.turnkeylinux.org/download?file=turnkey-wordpress-14.2-jessie-amd64.ova) (304MB)
    
    (b) [turnkey-wordpress-14.2-jessie-amd64.ova.hash](https://releases.turnkeylinux.org/turnkey-wordpress/14.2-jessie-amd64/turnkey-wordpress-14.2-jessie-amd64.ova.hash) (2,2 KB)
    
    Desa el fitxer (b) al teu disc dur i obre'l amb un editor de text. Llegeix-ne el contingut i segueix les instruccions que dona per a comprovar la firma del mateix fitxer (b) i per a comprovar el hash SHA256 del fitxer (a).
   
2. Repeteix l'apartat anterior però buscant tu mateix un programa per a GNU/Linux per descarregar. Recorda que has de comprovar que el hash del fitxer descarregat sigui el mateix que el hash indicat a la pàgina de descàrrega (idealment hauria d'anar signat). Indica el programa i la URL amb el que has fet l'apartat.
 
3. Instal·la amb apt-get algun programa que requereixi tenir la clau pública del desenvolupador per a poder fer-ho. Per exemple, [com instal·lar Docker en Ubuntu](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-on-ubuntu-16-04). 

    ATENCIÓ! Si tens una màquina Debian (per exemple de la Wordpress Turnkey Linux) segueix les instruccions de [Get Docker CE for Debian](https://docs.docker.com/install/linux/docker-ce/debian/)
    
    Resumeix el procés realitzat amb les teves paraules. Es valorarà que ho repeteixis amb un altre aplicació.

4. Amb una màquina Windows, descarrega des del navegador algun programa que el fabricant aparegui identificat (fes-ne una captura) i mostra la seva firma digital (també amb captura). Respon les següents preguntes: **Què implica que hi hagi aquesta firma al descarregar un fitxer? Hi ha algun risc al descarregar Skype de la web original si apareix com a fabricant "Desconegut"?** Raona la resposta.

---

#FpInfor #Smx #SmxMp06 #SmxMp06Uf04

* Resultats d'aprenentatge 1.c 1.g 1.h
---

###### Autor: Carles Caño 2017.02.17 14:53:19
###### Editat per: Carles Caño 2018.02.16 16:01:21
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
