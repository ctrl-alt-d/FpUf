# Muntatge d'un sistema de replicació Master-Slave amb MySQL 5.6 (Percona)
## ASIX-MP10-UF2 - Exercici de instal·lació i ajustament de SGBD corporatiu.
### **REPLICACIÓ (Master-Slave)**



Es vol muntar entorn SGBD MySQL Percona amb rèplica. Es vol tenir un MySQL master a on s'aniran enviant totes les instruccions SQL d'inserció, modificació i esborrat. Es vol tenir un MySQL  esclau del master anteriorment esmentat.
Cal que que al realitzar un INSERT en el master veiem les dades a l'esclau al cap d'un instant de temps.

**CONFIGURACIÓ MASTER**

- Realitza una còpia del fitxer de configuració del MySQL `/etc/my.conf` --> `/etc/my.conf.bkp`
- Modifica el fitxer `/etc/my.conf` i activa el `paràmetrelog-bin` (tal i com vàreu fer a M02). 
- Amb el nom: `<PRIMER LLETRA DEL NOM + 1r COGNOM>rep`
Exemple: `log-bin=rventurarep`
- Verifica que el paràmetre `server-id` té un valor numèric (per defecte és 1).
- Verifica que tots els paràmetres de InnoDB estiguin descomentats
- Canvia el paràmetre `innodb_log_buffer` a 10M
- Canvia o afegeix el paràmetre `innodb_log_files_in_group` a 2
- Para el servei de MySQL
- Borra tots els fitxers de log InnoDB del directory `/var/lib/mysql`
- Engega el servei de MySQL.
- Quants fitxers comencen amb el nom `<PRIMER LLETRA DEL NOM + 1r COGNOM>rep` dins el directori `/var/lib/mysql`? Digues quins són
- Realitza un instrucció DML, per exemple INSERT,UPDATE o DELETE
- Obre un altre terminal i utilitzant l'eina mysqlbinlog mira el contingut del fitxer `<PRIMER LLETRA DEL NOM + 1r COGNOM>rep.000001`
mysqlbinlog <PRIMER LLETRA DEL NOM + 1r COGNOM>rep.000001
** Quin és el seu contingut?**
- Fes un FLUSH DELS LOGS utilitzant la comanda FLUSH LOGS dins del MySQL


`mysql> FLUSH LOGS`;
- Realitza una comprovació dels logs com a master mitjançant SHOW MASTER LOGS




`mysql> SHOW MASTER LOGS`


**CONFIGURACIÓ SLAVE i MASTER**

- Realitza una còpia de la màquina virtual a on tinguis SGBD MySQL. Aquesta nova màquina serà que farà d'eslau.
- Esbrina quina IP tenen cadascuna de les màquines (master, slave).
- Crea un backup de la BD a la màquina master utilitzant:


`$> mysqldump –-user=root –-password=vostrepwd -–master-data=2 sakila > /tmp/master_backup.sql`
- Edita el fitxer master_backup.sql i busca la línia que comenci per `--CHANGE MASTER TO....` i busca els valors `MASTER_LOG_FILE` i `MASTER_LOG_POS`.


SLAVE
- Para el servei de MySQL.
- Modifica el fitxer de configuració `/etc/my.conf` 
- Comenta els paràmetres `log-bin` i `binlog_format`. D'aquesta manera desactivarem el sistema de `log-bin`.
- Assigna un valor al paràmetre  `server-id` (diferent que el del Master)
Torna engegar el servei MySQL.
MASTER
- Afegeix l'usuari slave amb la IP de la màquina slave


`CREATE USER 'slave'@'IP-SERVIDOR-SLAVE' 
 IDENTIFIED BY 'patata';`


- Afegix el permís de `REPLICATION SLAVE` a l'usuari que acabes de crear.


`GRANT REPLICATION SLAVE ON *.* TO 'slave'@'IP-SERVIDOR-SLAVE';`, 


`FLUSH PRIVILEGES;`


- A la màquina SLAVE executa la següent comanda ajudant-te de les dades del pas 3 i 4:



exemple:

```sql
CHANGE MASTER TO
 MASTER_HOST = '<ip-servidor-master>',
 MASTER_USER = 'slave',
 MASTER_PASSWORD = 'patata',
 MASTER_PORT = '3306',
 MASTER_LOG_FILE = '<PRIMER LLETRA DEL NOM + 1r COGNOM>rep.000002',
 MASTER_LOG_POS = <valor trobat en el pas 4>,
 MASTER_CONNECT_RETRY = 10;
```

- Comprova mitjançant `SHOW SLAVE STATUS`, quins valors et dóna?
- Comprova que es repliquin les dades realitzant modificacions a la BD master.

---

#FpInfor #Asix #AsixMp10 #AsixMp10Uf02

---

###### Autor: Robert Ventura 2016.06.29 06:50:18
###### Editat per: daniel herrera 2016.06.29 09:05:24
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
