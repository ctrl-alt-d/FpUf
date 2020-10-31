# Seguretat física de Linux
## SMX-MP06-UF1 - Exercici de seguretat passiva. 
En sistemes Linux si no es configura adequadament el sistema d'arrancada un atacant el pot fer servir per arrancar el sistema en mode monousuari i aconseguir accés total al sistema.

> El mode monousuari serveix perquè els administradors puguin realitzar gestions que no es poden fer si hi ha algun procés interferint. Però quan estem en aquest mode el sistema només té un sol usuari, el root, i per tant té el control total del sistema

Per accedir al mode monousuari només cal afegir a la comanda de càrrega del nucli l'entrada 'single'. 

En Lilo només calia afegir en l'entrada 'single'

    Boot: linux single

Actualment la majoria dels sistemes Linux venen amb GRUB o GRUB2 com a gestors d'arrencada. En aquest cas el que s'ha de fer és editar la línia d'arrencada del nucli simplement fent sortir el menú (prement SHIFT durant l'arrencada) i clicant la lletra 'e' per editar: 

![Grub](http://imageshack.us/a/img571/72/8e49.png "Grub")

En la línia que especifica el nucli (comença per linux)                 
    linux /boot/vmlinuz-3.2.0-24-generic root=UUID=bc6f8146-1523 ro quiet splash initrd /boot/initrd.img-3.2.0-24-generic 

Canviem l'entrada **'ro quiet splash'** per **'ro quiet splash single'** o bé s'hi afegeix **'init=/bin/bash'**


###Protegir la modificació de la càrrega del sistema
GRUB2 ofereix un sistema de protecció bàsic basat en usuari/contrasenya. D'aquesta forma es pot definir un grup d'usuaris i quines entrades poden modificar o executar.

Les contrasenyes i els usuaris es defineixen en el fitxer /etc/grub.d/40_custom (es pot afegir en altres llocs):

    ...
    set superusers="admin"
    password admin patata
    ...

Tenir la contrasenya en planer en el fitxer de configuració no és un procediment gaire segur de manera que també s'ofereix la possibilitat de que la contrasenya estigui xifrada. Per fer-ho s'ofereix la comanda grub-mkpasswd-pbkdf2

    # grub-mkpasswd-pbkdf2

El que surti d'aquesta comanda serà la contrasenya que s'ha de definir a l'usuari
    ...
    set superusers="admin"
    password_pbkdf2 admin grub.pbkdf2.sha512.10000.FC58373BCA1...

I evidentment s'ha de tornar a carregar GRUB

    # update-grub

També es poden protegir determinades entrades perquè només les puguin fer servir determinats usuaris

Activitat
----------------------

### 1. Atacar el sistema amb l'arrancada en mode monousuari
Per fer aquesta part heu d'imaginar que sou un atacant que vol accedir en una màquina que no és la vostra i que esteu davant d'ella...

1. Arranqueu una màquina en Linux editant una de les entrades de GRUB perquè arrenqui amb mode mono usuari

2. Un cop iniciat el sistema canvieu la contrasenya de l'usuari administrador

3. Reincieu la màquina i comproveu que la contrasenya ha estat canviada

### 2, Protegir l'arrencada de GRUB2
Per fer aquesta part us poseu en el lloc de l'administrador de la màquina que vol evitar que sigui tant fàcil entrar en el seu sistema... 

4. Configureu GRUB perquè no permeti l'edició de les entrades del menú a menys que es conegui una contrasenya

5. Reinicieu la màquina i comproveu que no és possible entrar en mode monousuari editant les entrades de GRUB

### 3. Arrancada amb un altre sistema
Per fer aquesta part torneu a ser un atacant que vol accedir a una màquina en la que l'administrador ha protegit les entrades del GRUB amb contrasenya...

6. Tot i les proteccions comproveu que arrencant el sistema amb un Live CD podeu iniciar la màquina

7. Munteu el disc dur i comproveu que podeu veure les contrasenyes dels usuari del fitxer /etc/shadow

8. Creeu un usuari nou

9. Reinicieu el sistema i comproveu que podeu entrar en el sistema amb l'usuari que heu creat


---

#FpInfor #Smx #SmxMp06 #SmxMp06Uf01

* Resultats d'aprenentatge 1.3
* Continguts 1.2
---

###### Autor: Xavier Sala 2013.10.28 10:12:24
###### Editat per: Xavier Sala 2013.11.03 22:07:18
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
