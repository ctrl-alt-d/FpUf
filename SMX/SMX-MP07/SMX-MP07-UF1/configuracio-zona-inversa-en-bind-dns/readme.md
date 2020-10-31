# Configuració Zona Inversa en Bind DNS 
## SMX-MP07-UF1 - Exercici de configuració de la xarxa (DNS i DHCP).
### Exercici pràctic

**Instal·lació del servidor bind DNS**

- Enceneu la màquina virtual Ubuntu Servidor en mode NAT.
- Instaleu el paquet bind9 (apt-get install). 
- Reinicieu la màquina virtual en  mode Xarxa Interna.

**Configuració del servidor bind DNS**

- Configureu la IP estàticament en el servidor. 
- Configureu el servidor DNS per a que faci la funció de DNS primari. 
- Configureu el servidor DNS per a que respongui a les peticions inverses. 
- Configureu el propi servidor DNS per a que resolgui les seves pròpies consultes DNS (/etc/resolv de la serva pròpia IP).
- Feu consultes host i dig per a comprovar que la zona inversa està ben configurada. El resultat final de l'exercici ha de ser demanar per una IP i que respongui el servidor amb el nom d'aquella IP (**host IP** o **dig -x IP**).

---

#FpInfor #Smx #SmxMp07 #SmxMp07Uf01

* Resultats d'aprenentatge 2.d, 2.e, 2.f, 2.h
* Continguts 2.4, 2.5, 2.6, 2.8
---

###### Autor: Isaac Muro 2013.11.04 16:46:52
###### Editat per: Isaac Muro 2013.11.04 16:52:23
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
