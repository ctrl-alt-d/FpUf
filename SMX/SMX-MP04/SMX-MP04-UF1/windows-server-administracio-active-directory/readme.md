# Windows Server - Administració Active Directory
## SMX-MP04-UF1 - Exercici de sistemes operatius propietaris en xarxa.
#Activitat 4 Administració Active Directory

![Active Directory](https://seicoll.gitbooks.io/sox/content/assets/ActiveDirectory.png)

### 1. Creació d’usuaris

1. Entreu com administrador al servidor i doneu d'**alta un nou usuari** amb nom **_alumne1 _**al Directori Actiu.

2. **Comproveu **que des del client podeu accedir al Domini amb les credencials de l’usuari.

3. **Prova **l'accés d'aquest usuari als recursos compartits mitjançant **_Inici>executar_** i posar l'adreça al servidor per IP, per nom de màquina o per variable.

  * \\\IP_SERVIDOR **(Poseu la IP del vostre servidor)**
  * \\\nom_maquina_servidor
  * %logonserver%

4. Prova d'accedir als **recursos compartits especials** C$ i ADMIN$ (\\\IP_SERVIDOR\C$ i \\\IP_SERVIDOR\ADMIN$). Has pogut accedir?

5. Ara tanca la sessió del client i torna a entrar amb les credencials d'administrador. Pots accedir ara als recursos compartits ocults C$ i ADMIN$? Cerca per internet perquè serveixen aquests recursos compartits i perquè es posa el símbol $.

6. **Restringeix la connexió** del alumne1 de manera que no pugui iniciar sessió tots els dies laborables de 13:00h a 20:00h. Comprova que ara no es pot connectar.

#### 2. Creació d’Unitats Organitzatives (UO)

1. Crea les següents unitats organitzatives (UO):

* Professors
* Alumnes
* Direcció
* Equips Windows7
* Equips Windows10

2. Posa l'equip que teniu preparat a dins "Equips Windows7". I els comptes d’usuari alumne1 creat en l’apartat anterior a la UO que correspon.

3. Crea un usuari administrador a cada una de les UOs de Professors, Alumnes i Direcció amb el nom **_AdmProfessors_**, **_AdmAlumnes _**i **_AdmDirecció_**.

4. Delega el control total de cada UO al Administrador de la UO.

### 3. Creació de grups d’usuaris

1. Crea 3 **grups d’usuaris global de domini**:

* Alumnes
* Professsors
* Colaboradors

2. Afegeix **3 usuaris al grup Alumnes i Professors**.

3. **Afegeix com a membre del grup "Colaboradors"** un alumne dels creats anteriorment i tot el grup “Professors”.

Un cop creat els grups, veurem la utilitat que poden tenir, per exemple, per controlar l’accés a recursos compartits:

4. Anem a la unitat C: del nostre servidor i creem la carpeta "Documents" i a dins la carpeta “DadesProfessors”.

5. Fem botó sobre la carpeta "DadesProfessors" i anem a “Compatir con...” i a “Usuarios específicos”, allà afegim el grup “Professors” i li donem permisos de “Lectura i escriptura”

6. Connectat al equip client amb un usuari del grup de "Professors" i comprova que pots accedir a la carpeta “DadesProfessors” i crear-hi un document.

7. Crea la carpeta "Revista" a **_C:/Documents_**. Comparteix aquesta carpeta assignant permisos de “Lectura i escriptura” al grup “Colaboradors” i també dóna permisos només de “Lectura” al grup “Alumnes”.

8. Connectat al equip client amb un usuari del grup de "Alumnes" i que no sigui del grup “Colaboradors” i comprova que pot accedir a la carpeta “Revista” però no pot crear-hi documents.

### 4. Creació plantilles d'usuari.

Per facilitar l'alta de nous usuaris heu de crear tres plantilles:

1. Plantilla **_UsuariColaborador_**:
* No pot canviar la contrasenya
* Només pot accedir al sistema en horari laboral (8:00-17:00 de dilluns a divendres)
* Pertany al grup de Colaboradors
* Ha de disposar de connexió a unitat remota en el servidor

2. Plantilla **_UsuariAlumne_**:
* No pot canviar la contrasenya
* No pot accedir els caps de setmana
* Pertany al grup Alumnes.

3. Plantilla **_UsuariProfessor_**:
* Ha de canviar la contrasenya al pròxim inici de sessió.
* Pot accedir sempre a totes hores
* Pertany al grup Professors.

4. Amb aquestes plantilles doneu d'alta **3 usuaris per a cada grup**.
Afegeix aquests usuaris a la Unitat Organitzativa que els hi correspon.

---

#FpInfor #Smx #SmxMp04 #SmxMp04Uf01

---

###### Autor: Sergi Coll 2017.06.05 17:07:16
###### Editat per: Sergi Coll 2017.06.05 17:07:16
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
