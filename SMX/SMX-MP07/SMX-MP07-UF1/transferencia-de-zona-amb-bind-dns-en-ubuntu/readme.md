# Transferencia de zona amb Bind DNS en Ubuntu
## SMX-MP07-UF1 - Exercici de configuració de la xarxa (DNS i DHCP).
### Exercici pràctic

**Instal·lació del servidor bind DNS**

- Enceneu les màquines virtuals Ubuntu Servidor en mode NAT.
- Instaleu el paquet bind9 (apt-get install). 
- Reinicieu les màquines virtuals en  mode Xarxa Interna.

**Configuració del servidor bind DNS**

- Configureu la IP estàticament en els dos servidors. 
- Configureu un servidor DNS per a que faci la funció de DNS primari. 
- Configureu l'altre servidor DNS per a que faci la funció de DNS secundari. 
- Comprovem que el fitxer de configuració de la zona s'ha copiat desde el servidor primari al servidor secundari. 

**Inicialitzem màquina Windows XP**

- Fes peticions ping als subdominis per comprovar que funcionen el servidors, encara que hi hagi un que setigui apagat o desconectat de la xarxa. 

**Per consultar:**

- [Font 1](http://www.josedomingo.org/pledin/2011/11/configuracion-de-un-servidor-dns-esclavo/)
- [Font 2](http://jesusvillaverde.com/external/howtos/bind/x57.html)

---

#FpInfor #Smx #SmxMp07 #SmxMp07Uf01

* Resultats d'aprenentatge 2.d, 2.e, 2.f, 2.h
* Continguts 2.4, 2.5, 2.6, 2.8
---

###### Autor: Isaac Muro 2013.10.30 10:24:56
###### Editat per: Isaac Muro 2013.11.04 16:03:53
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
