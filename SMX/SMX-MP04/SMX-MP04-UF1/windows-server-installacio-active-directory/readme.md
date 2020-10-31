# Windows Server - Instal·lació Active Directory
## SMX-MP04-UF1 - Exercici de sistemes operatius propietaris en xarxa.
#Activitat 3 Instal·lació Active Directory

**Apunts** [Instal·lació d'un controlador de domini Active Directory](https://seicoll.gitbooks.io/sox/UF1/instalacio-AD.html)

![Active Directory](https://seicoll.gitbooks.io/sox/content/assets/ActiveDirectory.png)

## Activitat

Instal·la el **Active Directory** i converteix el servidor en controlador de domini primari.

**Documenta la pràctica **i anota-hi tots els problemes que has trobat durant la instal·lació.

### 1. Instal·lació del Directori Actiu i creació del domini

1. Instal·la el servei de domini (Active Directory) i promou el servidor a controlador de domini.

```
Captura on es vegi el teu domini i que el servidor ara és un controlador d’aquest domini.
```

1.2 Entra com administrador al servidor i crea un usuari del domini que tingui l’identificador usuarixxx (xxx són les teves inicials)   

### 2. Unir equips al domini

2.1 Configuració bàsica: nom de la màquina, IP, màscara, porta d'enllaç i servidors de DNS.
```
Captura on es vegin aquestes dades
```
2.2 Fes pings per a verificar que el client pot comunicar-se amb el servidor.

2.3 Entreu a la màquina client i afegiu-la al domini, canviant el mode de grup de treball al mode de domini. Necessitareu les credencials d'administrador del domini.
```
Captura del missatge on s’indica que la màquina s’ha unit al domini
```

2.4 Comprova que pots entrar a la màquina client validant un usuari del domini (*usuarixxx*).
```
On cop validat l’usuari, captura del resultat de la comanda whoami.
```

2.5 Entra al servidor i busca el nou equip a Eines administratives > Usuaris i equips de l’Active Directory.
```
Captura de la pantalla 
```

### CHALLENGING ACTIVITIES

#### Users validation on the client
Try the different ways to validate a user (indicate what you put in the username):

* Domain user, DNS format (current format)
```
Screenshot	 		
```

* Domain user, NetBIOS format (old format)
```
Screenshot	 		
```

* Local user	
```
Screenshot	 		
```

####Change of domain

* Change the server and client network in Bridged mode.
* Disconnect the client from your domain and connect it to the domain of a classmate.

```
Screenshot indicating that you have joined the machine in a domain of a classmate (indicate with which classmate you have done it)	
```

* Check that you can validate a user of his domain.
* Re-change your machines on the network NAT SOX.
* Disconnect the client from domain and reconnect it to your domain
* Verify that you can validate users in your domain.

---

#FpInfor #Smx #SmxMp04 #SmxMp04Uf01

---

###### Autor: Sergi Coll 2017.06.05 17:03:09
###### Editat per: Sergi Coll 2017.10.20 13:45:14
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
