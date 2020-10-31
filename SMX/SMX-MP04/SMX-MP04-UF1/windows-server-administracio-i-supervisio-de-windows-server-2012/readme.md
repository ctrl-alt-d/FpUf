# Windows Server - Administració i supervisió
## SMX-MP04-UF1 - Exercici de sistemes operatius propietaris en xarxa.
#Activitat 2. Administració i supervisió de Windows Server 2016

Apunts [Supervisió Windows Server 2016](https://seicoll.gitbooks.io/sox/UF1/uf1-supervisio.html)

## Activitat

###1. Administrador de tasques

1.1. Quins operacions/tasques ens permet fer l’administrador de tasques?

1.2. Indica les 4 formes d’accedir a la consola d'administració de tasques.

1.3. Enumera i resumeix la utilitat de les 5 pestanyes que formen l'administrador de tasques. Posa una captura de pantalla de cada una d’aquestes pestanyes del Windows Server 2016.

1.4. Obre la línia de comandes (cmd) des de l’administrador de tasques.

1.5. Que és el PID d’un procés?

###2. Administrador de serveis

2.1. Què significa el “tipus d'inici” d'un servei?

2.2. Per a què serveix la pestanya de Recuperació que trobem dins les propietats d’un servei?

2.3. Modifica el servei “Client dhcp” per a que tingui un inici manual. Canvia la teva IP a DHCP (Obtenir IP automàticament) i reinicia el sistema. Què hauria d'anar malament? Per què? Torna-ho a deixar com estava.

### 3. Usuaris

3.1. Com podem desconnectar a un usuari que s'ha connectat remotament al nostre servidor?

3.2. Desconnecta el teu propi usuari.

3.3. Obre un altra sessió de Windows 2016 amb un altre nom d'usuari (recorda que tindrà que pertànyer al grup d'administradors per poder obrir sessió local en el servidor). Ara canvia d'usuari i torna a la sessió inicial. Comprova en l'administrador de tasques quins usuaris estan connectats (enganxa aquí una captura de la finestra).

3.4. Envia un missatge a l'altre usuari connectat. Canvia a la seva sessió i comprova que ha arribat (enganxa aquí una captura de la finestra del missatge). Ja pots tancar aquesta sessió.

### 4. Registre d’esdeveniments

4.1. Ara torna a entrar a la sessió de l'administrador però primer amb una contrasenya incorrecta. Això genera errors d'auditoria que queda registrat. Una vegada has posat la contrasenya correcta i has entrat com administrador engega el visor d'esdeveniments ("visor de eventos") i indica el que trobis a la secció de _**Registros de windows > seguridad**_ relacionat amb aquests accessos no autoritzats. 

4.2. Fes una captura de pantalla amb l’error que trobis al registre. Quina informació et dóna?

### 5. Actualitzacions

5.1. Actualitza el sistema operatiu. Hi ha alguna actualització o "service pack" disponible?

5.2. Configura les hores actives de 9:00h a 18:00h.

### 6. Administració del servidor

6.1. Executa l’eina **_Administrador del servidor_**. Quins rols i característiques es poden configurar?

6.2. Mostra, des del Windows Server, el processador, la RAM i l’espai de disc que té el sistema.

### AMPLIACIÓ
Busqueu informació sobre com instal·lar la funció Terminal Server i com podem connectar-nos des d'una màquina remota. Crea un usuari amb el teu nom i cognom (nomcognom). Configura aquest usuari perquè es pugui connectar al servidor des del Windows client mitjançant el terminal server.

---

#FpInfor #Smx #SmxMp04 #SmxMp04Uf01

---

###### Autor: Sergi Coll 2017.06.05 17:00:34
###### Editat per: Sergi Coll 2017.10.20 13:36:43
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
