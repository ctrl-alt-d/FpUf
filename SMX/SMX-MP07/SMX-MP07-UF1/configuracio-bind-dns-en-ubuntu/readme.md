# Configuració Bind DNS en Ubuntu 1
## SMX-MP07-UF1 - Exercici de configuració de la xarxa (DNS i DHCP).
### Exercici pràctic

**Instal·lació del servidor bind DNS**

- Enceneu la màquina virtual Ubuntu Servidor en mode NAT.
- Instaleu el paquet bind9 (apt-get install). 
- Reinicieu la màquina virtual en  mode Xarxa Interna.

**Configuració del servidor bind DNS**

- Configureu la IP estàticament (/etc/network/interfaces). 
- Configureu el fitxer named.conf.local amb una nova zona (/etc/bind).
- Comproveu que el fitxer està ben configurat (named-checkconf).
- Creeu l'arxiu de configuració de la vostra nova zona (db.elvostrenom.com).
- Editeu aquest últim fitxer i configureu els subdominis. 
- Comproveu que el fitxer està ben configurat (named-checkzone).
- Reinicieu el servidor.
- Amb la comanda dig, comproveu que el servidor respon correctament a les peticions. 

**Inicialitzem màquina Ubuntu Client**

- Enceneu la màquina virtual Ubuntu Client en mode Xarxa Interna
- Configureu la IP estàticament. 
- Definiu el seu servidor DNS, que serà el Ubuntu Servidor (/etc/resolv.conf). 
- Fes peticions ping als subdominis per comprovar que funciona el servidor. 



---

#FpInfor #Smx #SmxMp07 #SmxMp07Uf01

* Resultats d'aprenentatge 2.d, 2.f, 2.h
* Continguts 2.4, 2.6, 2.8
---

###### Autor: Isaac Muro 2013.10.29 23:21:13
###### Editat per: Isaac Muro 2013.10.30 10:05:42
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
