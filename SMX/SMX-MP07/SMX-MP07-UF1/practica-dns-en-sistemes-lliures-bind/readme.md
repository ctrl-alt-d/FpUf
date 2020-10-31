# Pràctica DNS en Sistemes Lliures (Bind)
## SMX-MP07-UF1 - Exercici de configuració de la xarxa (DNS i DHCP).
#### **Pràctica DNS en Sistemes Lliures (Bind)**

*Recomanació: 
- Pràctica per tractar el servei DNS utilitzant Bind, dig i nslookup.
- Aquesta pràctica és força llarga i és per això que es aconsellable intercalar explicacions i entregues parcials de la mateixa.*

- Instal·lar i configurar un servidor DNS en un Ubuntu Server (utilitzar Bind). Utilitzar com a nom de subdomini "smx.cfgm.com". Crear la zona directa i també la zona inversa. 

- Introduir un Ubuntu Desktop (amb ip fixa) com a màquina al DNS (registre A). Indicar un alias (el que vulguis). Indicar dos servidors de correu pel subdomini (només indicar-los, no cal tenir les màquines). 

- Comprovar (amb dig) que l'Ubuntu Desktop està utilitzant correctament el servei. Per fer-lo, preguntar per la ip que té l'àlies, preguntar pels noms servidors de correu i realitzar una pregunta inversa per un dels servidors de correu. 

- Imagina que un intrús vol realitzar una transferència de zona del teu subdomini. Quins són els passos que seguiria?  Fes-lo.

- Introduir un altre equip al DNS (un Windows). Comprobar (amb nslookup) que està utilitzant correctament el servei realitzant les mateixes accions que has fet amb dig. 

- Utilitza NameBench des de l'Ubuntu Desktop, per fer un test dels servidors DNS recomanats. 
- Què és DNSSEC i com funciona?

Com sempre captures i documentació de tots els passos

---

#FpInfor #Smx #SmxMp07 #SmxMp07Uf01

---

###### Autor: Juaky 2014.01.10 10:15:56
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
