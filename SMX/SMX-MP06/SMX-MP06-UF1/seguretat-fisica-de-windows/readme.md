# Seguretat física de Windows
## SMX-MP06-UF1 - Exercici de seguretat passiva. 
Introducció
--------------
En un sistema Windows hi ha una sèrie de programes que s'inicien abans de que l'usuari entri en el sistema. Si un atacant aconseguir canviar el programa que s'executa per defecte per un altre que permeti executar comandes podria entrar en el sistema sense conèixer cap compte d'usuari. 

Però a més tindrà els privilegis de l'usuari amb el que Windows executa el programa. En temps d'arrencada normalment és l'usuari SYSTEM, que és un usuari privilegiat de Windows, i que permet fer qualsevol tasca en el sistema operatiu com per exemple canviar la contrasenya de l'administrador

Amb una tècnica com aquesta un usuari limitat del sistema podrà incrementar els seus privilegis d'accés al sistema i aconseguir fer coses a les que no està autoritzat

Les *StickyKeys* són una característica d'accessibilitat per usuaris amb problemes per mantenir dues o més tecles premudes alhora. Quan cal una combinació de tecles per aconseguir accés a determinades opcions, com CTRL+P permet prémer les tecles una a una en comptes de requerir que es premin de forma simultània


Activitat
-------------
Atac offline a Windows fent servir sticky keys

1. Arranqueu una màquina virtual de Windows amb un LiveCD i substituïu el programa SETHC.exe per CMD.exe

2. Inicieu el sistema sense el LIVE CD i comprovareu que el sistema arranca normalment

3. Premeu cinc vegades la tecla SHIFT i veureu que se us obre un terminal amb privilegis de l'usuari SYSTEM!

4.  Al executar l'explorer ( EXPLORER.EXE) tindreu un entorn totalment funcional! Amb un fons d'escriptori curiós 

5. Comproveu que podeu crear usuaris en el sistema amb les comandes 'NET'

    net user /add pepet contrasenya

6. Inicieu el sistema normalment i comproveu que l'usuari que heu creat pot entrar en el sistema. Sou capaços de crear un usuari amb privilegis d'administració?





1. Documenteu el procés amb totes les passes que que heu realitzat per aconseguir vulnerar la seguretat del sistema i calculeu el temps que us cal per realitzar-lo

2. Descobriu com es poden desactivar les Sticky Keys en Windows

3. Busqueu per internet per aconseguir trobar un altre programa amb el que es pugui fer un atac semblant. Intenteu fer-lo i comproveu si funciona

4. Creieu que és possible fer una cosa semblant en Linux? Localitzeu una forma de fer-ho


---

#FpInfor #Smx #SmxMp06 #SmxMp06Uf01

* Resultats d'aprenentatge 1.3 
* Continguts 1.2 
---

###### Autor: Xavier Sala 2013.10.28 10:01:30
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
