# Programar còpies de seguretat amb cron (GNU/Linux)
## SMX-MP06-UF2 - Exercici de còpies de seguretat.
#Recursos

[LPI 107.2. Automatitzar tasques d'administració del sistema amb treballs programats](http://acacha.org/mediawiki/LPI_107.2._Automatitzar_tasques_d%27administraci%C3%B3_del_sistema_amb_treballs_programats#.Whbd13XWwb1)

#Activitat

En aquesta activitat programaràs diverses còpies de seguretat del teu sistema GNU/Linux.

1. Per saber quins dies faràs còpia, prem [aquí](https://www.random.org/integers/?num=3&min=1&max=7&col=1&base=10&format=plain&rnd=new). Si surten nombres repetits, recarrega la pàgina fins que siguin tots diferents. Ara ja saps els dies de la setmana (p. ex: 4, 7, 2 serien dijous, diumenge i dimarts). **Apunta els dies de la setmana que t'han sortit**

2. Per saber quines hores faràs còpia, prem [aquí](https://www.random.org/integers/?num=3&min=1&max=23&col=1&base=10&format=plain&rnd=new). Si surten nombres repetits, recarrega la pàgina fins que siguin tots diferents. Ara ja saps les hores en que faràs les còpies (p. ex: 5, 12, 14 es faran a les 5h (AM), 12h (PM) i 14h (PM).

3. Per saber els minuts en els que faràs còpia, prem [aquí](https://www.random.org/integers/?num=3&min=1&max=59&col=1&base=10&format=plain&rnd=new). Si surten nombres repetits, recarrega la pàgina fins que siguin tots diferents. Ara ja saps les hores en que faràs les còpies (p. ex: 2, 11, 24 es faran als minuts 2, 11 i 24 :-).

4. **Apunta aquí les hores del segon apartat combinades amb els minuts del tercer apartat**. Per exemple, 5:02, 12:11 i 14:24.

5. **Apunta els dies del primer apartat combinats amb les hores i minuts de l'apartat anterior**. Per exemple: Dijous 5:02, Diumenge 12:11 i Dimarts 14:24.

6. Utilitzant l'eina **cron** del sistema, programa còpies de seguretat en els dies i hores de l'apartat anterior de les següents carpetes: /home, /etc i /var. **Els noms dels arxius han de contenir la data i hora en que s'ha fet la còpia**. Per exemple, **20171123-0502.tgz** Els arxius es desaran a la carpeta **/backups** (crea-la).

7. **Escriu aquí el contingut de l'arxiu crontab que has posat a l'apartat anterior**.

8. Per comprovar que es fan les còpies, canvia la hora i data del sistema de la teva màquina virtual.

---

#FpInfor #Smx #SmxMp06 #SmxMp06Uf02

* Resultats d'aprenentatge 1.e 1.f 1.h
---

###### Autor: Carles Caño 2017.11.23 15:27:08
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
