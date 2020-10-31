# Pràctica FTP en Sistemes Lliures
## SMX-MP07-UF2 - Exercici de correu electrònic i transmissió d’arxius.
#### **Pràctica FTP Sistemes Lliures**
*Recomanació: 
- Pràctica per tractar FTP, ftps i sftp utilitzant vsftpd. 
- Aquesta pràctica és força llarga i és per això que es aconsellable intercalar explicacions i entregues parcials de la mateixa.*

En un equip amb Ubuntu Server, instal·lar vsftpd. A continuació configurar el servei ftp amb les següents opcions (realitza la captura de pantalla corresponent explicant les accions realitzades i en el cas de ser possible realitza la comprovació del seu funcionament):

- Permetre pujar fitxers al servidor.
- Mostrar un missatge de benvinguda (el que vulguis)
- Permetre connexió a l'usuari anònim.
- Establir els següents límits de transferència: a l'usuari anonymous 7 Kb/s, a la resta d'usuaris 15 Kb/s
- Permetre a l'usuari anònim crear directoris.
- Que es mostri un missatge en entrar a una carpeta concreta (la que vulguis)
- Permetre a l'usuari anònim pujar fitxers.
- Guardar un log de les pujades i baixades.
- Que el fitxer de log es guardi a /var/log/miftp.log
- Que es tanqui la sessió si no hi ha activitat després de 40 segons.
- Fer que un intent de connexió de l'usuari "anonymous" amb la contrasenya concreta "a@a.com" no pugui conectar-se.
- Crear gàbies per als usuaris. Fer que un usuari concret (el que vulguis) pugui sortir de la gàbia.
- Fer que un usuari pugui fer un llistat ("ls") de forma recursiva.
- Establir un número màxim de 2 usuaris connectats a la vegada.
- Fer que quan un usari cregui una carpeta, tingui tots els permisos per al propietari, els de lectura i execució per al grup i el de escriptura per a la resta.
- Establir un número màxim de 1 usuaris connectats des de la mateixa ip.
- Permetre la connexió a usuaris intrínsecs al servidor Linux.
- Crear un certificat amb openssl i provar una connexió segura mitjançant TLS i mitjançant sftp (port 22). Per fer-lo utilitza un client ftp com ara FireFTP o FileZilla Client. Comprovar amb Wireshark el resultat d'utilitzar ftp, sftp i ftp sobre tls.

---

#FpInfor #Smx #SmxMp07 #SmxMp07Uf02

---

###### Autor: Juaky 2014.01.10 10:47:43
###### Editat per: Juaky 2014.01.10 10:47:43
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
