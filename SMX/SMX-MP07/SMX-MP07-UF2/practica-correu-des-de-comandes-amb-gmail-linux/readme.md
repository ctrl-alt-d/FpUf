# Pràctica Correu des de comandes amb gmail - Linux
## SMX-MP07-UF2 - Exercici de correu electrònic i transmissió d’arxius.
#### **Pràctica Correu des de Comandes amb Gmail - Linux**
*Recomanació: 
- Pràctica per tractar els comandos del servei de correu.*

 Enviar un correu des de línia de comandes amb compte de gmail.

- No podem utilitzar el port 25 ja que gmail utilitza ssl. Per connectar-nos al port 465 (SSL) necesitarem crear un túnel des d'un port de la nostra màquina (el 25) a un altre de la remota (el 465). L'establiment de túnels es veurà a la quarta unitat formativa. Una de les eines per poder realitzar un túnel és el paquet "tunnel" que haurem d'instal·lar a la nostra máquina: apt-get install stunnel

- En acabar la instal·lació ens avisa que està desactivat i que s'ha de mirar el fitxer /etc/default/stunnel4. Allà indica que per activar-lo cal posar ENABLED=1.

- Per realitzar el túnel, la comanda és: stunnel -d 25 -cr smtp.gmail.com:465 No dóna cap resposta, però el túnel estarà establert.

- Connectem amb el port 25 del nostre equip (localhost), el túnel farà que realment es connecti al port 465 del servidor smtp de gmail:
telnet localhost 25

- Ja estem connectats al servidor remot, ara iniciem la connexió amb la comanda del smtp: helo nommaquina

- L'usuari i contrasenya utilitzats estan encriptats en base64, per tant hem de dir-li que utilitzarem aquest mode d'autenticació:: auth login
Respondrá: 334 VXNlcm5hbWU6

- Des d'un altre terminal obtindrem el nom d'usuari pero en base64, per fer-lo Ubuntu ja incorpora el paquet "base64" el qual realitza la conversió de text:
echo "nom usuari en gmail" | base64      
El nom d'usuari s'ha de possar complet: usuario@gmail.com

- Copiem l'obtingut i li pasem a la connexió oberta amb smtp.

- Respondrá: 334 UGFzc3dvcmQ6

- Fem el mateix per pasar-li la contrsenya, primer la pasem a base64:
echo "la contraseña" | base64

- Copiem l'obtingut i li pasem a la connexió oberta amb smtp.

- Respondrà: 235 2.7.0 Accepted

- A partir d'aquí podem començar amb els comandos del smtp que ja coneixem:

mail from: <"Dirección de correo"> (s'ha d'escriure exactament així, amb símbols de menor i major i amb cometes dobles)

rcpt to: <"Dirección de correo">    (també s'ha d'escriure exactament així)

data

quit

El correu ja s'ha enviat correctament. 

---

#FpInfor #Smx #SmxMp07 #SmxMp07Uf02

---

###### Autor: Juaky 2014.01.10 10:55:01
###### Editat per: Juaky 2014.01.10 10:55:01
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
