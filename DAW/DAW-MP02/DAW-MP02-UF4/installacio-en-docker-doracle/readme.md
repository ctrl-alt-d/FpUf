# Instal·lació en Docker d'Oracle
## DAW-MP02-UF4 - Exercici de Bases de dades objectes-relacionals
Per a fer les pràctiques usarem una versió de base de dades que ens permet treballar amb ella sense haver d'adquirir una llicència. L'Express Edition.

Tenim dues opcions, la podem posar en un docker o bé la instal·lem, sigui a la pròpia màquina sigui a la màquina virtual.

[Oracle ens explica com fer el docker](https://github.com/oracle/docker-images), però és més senzill fer servir aquest:

[https://github.com/wnameless/docker-oracle-xe-11g](https://github.com/wnameless/docker-oracle-xe-11g)

Fes una instal·lació d'Oracle a la teva màquina i comprova que t'hi pots connectar:

```bash
docker run -d -p 49160:22 -p 49161:1521 -e ORACLE_DISABLE_ASYNCH_IO=true wnameless/oracle-xe-11g
docker container ls
ssh root@localhost -p 49160 #pot trigar una mica a engegar (passwd is admin)
sqlplus system
>password: oracle
SQL> CREATE USER o IDENTIFIED BY o DEFAULT TABLESPACE users TEMPORARY TABLESPACE temp;
SQL> GRANT CONNECT, RESOURCE TO o;
SQL> exit
root@58fdeb1d9cbe:~# sqlplus o 
password: o
```

### Editor sql

Escriute codi a l'SQLPLUS és una experiència no gaire agradable. Podeu mapejar una carpeta de la vostra màquina al docker i executar els scripts:

```bash
docker run -v $PWD:/c  -d -p 49160:22 -p 49161:1521 -e ORACLE_DISABLE_ASYNCH_IO=true wnameless/oracle-xe-11g
# sqlplus o     
SQL*Plus: Release 11.2.0.2.0 Production on Tue Apr 3 15:06:00 2018 
Copyright (c) 1982, 2011, Oracle.  All rights reserved.
Enter password: 
Connected to:
Oracle Database 11g Express Edition Release 11.2.0.2.0 - 64bit Production
SQL> 
SQL> @/c/s.sql
Type created.
```

---

#FpInfor #Daw #DawMp02 #DawMp02Uf04

---

###### Autor: daniel herrera 2018.04.01 14:49:30
###### Editat per: daniel herrera 2018.04.03 15:11:29
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
