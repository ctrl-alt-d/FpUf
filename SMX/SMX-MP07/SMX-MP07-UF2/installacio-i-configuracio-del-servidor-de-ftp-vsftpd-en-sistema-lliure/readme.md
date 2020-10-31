# Instal·lació i configuració del servidor de FTP VSFTPD en sistema lliure
## SMX-MP07-UF2 - Exercici de correu electrònic i transmissió d’arxius.
**Objectius:**
- Configuració servidor ftp VSFTP (Very Secure File Transfer Protocol) en un sistema GNU/Linux
- Conèixer els arxius i directives de configuració del servidor vsftp

###Respon a les següents preguntes i executa les accions demandes

1. Fes una descripció de les característiques principals del servidor vsftp (Usuaris, límit de connexions, controls, connexions segures etc...). I cerca llocs que utilitzin aquest servidor.
2. Instal·la el servidor vsftp
3. Quin és el fitxer de configuració principal i on es troba?
4. Quin és el fitxer daemon que és el procés principal? On es troba?
5. Quin és el grup principal de l'usuari 'ftp'. A quins grups més pertany?
6. Quin és el directori per defecte dels usuaris anònims? Qui és el seu usuari i grup propietari?
7. Com comproves que el servidor està iniciat i escoltant pel port 21/tcp?
8. Analitza el fitxer de configuració principal i digues quina és la configuració per defecte dels usuaris anònims
9. Quina directiva inhabilita l'accés als usuaris anònims?
10. Com podem fer que el usuaris anònims puguin pujar arxius a una carpeta determinada?
11. Quina és la funció de les directives chroot_list_enable i chroot_list_file
12. Quina és l'adreça del fitxer log del servidor vsftp? Amb quina/es directiva/es ho podem modificar
13. Crea una configuració amb les següents característiques i comprova-ho
    1. Que els usuaris del sistema tinguin accés
    2. Que quan un client inici una comunicació obtingui un missatge de benvinguda al ftp
    3. Que els usuaris anònims tinguin un límit de velocitat de transferència de 7,2 Kb, i que tinguin només 10 minuts d'accés.
    4. Els usuaris locals han de estar engabiats en el seu home de la màquina i poden crear-hi directoris
    5. Per accedir com a anònim hi ha una llista de password disponibles
14. Connectat amb el client ftp del terminal i fes les comprovacions necessàries per demostrar tots els punts de la configuració anterior

---

#FpInfor #Smx #SmxMp07 #SmxMp07Uf02

* Resultats d'aprenentatge 1.b 1.c 1.d
* Continguts 1.2 1.3 1.4
---

###### Autor: Jordi Hernandez 2014.01.13 22:15:00
###### Editat per: daniel herrera 2014.09.13 19:33:04
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
