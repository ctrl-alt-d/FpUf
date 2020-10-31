# Gestió de RAID en Linux
## SMX-MP06-UF2 - Exercici de còpies de seguretat.
Introducció
===============

mdadm
-------
mdadm és una comanda de Linux que serveix per administrar els dispositius RAID d'una màquina: 

    # mdadm --detail /dev/md0
    /dev/md0:
    Version : 1.2
    Creation Time : Sat Feb 19 16:29:11 2011
    Raid Level : raid1
    Array Size : 3904500 (3.72 GiB 4 GB)
    Used Dev Size : 3904500 (3.72 GiB 4 GB)
    Raid Devices : 2
    Total Devices : 2
    Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Mon Feb 21 12:42:12 2011
    State : clean
    Active Devices : 2
    Working Devices: 2
    Failed Devices : 0
    Spare Devices : 0

    Name : ubuntu:0 (local to host ubuntu)
    UUID : a1500c81:a4bdadeb:382ce4fd:28800507 (local to host homeServer)
    Events : 131
    Number Major Minor RaidDevice State
    0 8 17 0 active sync /dev/sda1 
    2 8 33 - active sync /dev/sdb1

Directory /proc/mdstat
------------------------
El sistema va mantenint un fitxer en el que es pot veure en quin estat es troben els dispositius RAID

    # cat /proc/mdstat
    Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
    md0 : active raid1 sda1[1] sdb1[0]
    976759936 blocks [2/2] [UU]
    unused devices: <none>

Tasques
==========

En una màquina virtual amb dos dics configurats per fer RAID entre dues particions. 

1. Afegiu-hi un nou disc. 

2. Creeu dues particions que tinguin la mateixa mida que les que fan RAID. 

3. Afegiu la primera partició al primer RAID (/dev/md0) de manera que s'acabi fent **mirroring** entre totes tres particions. 
    * Feu una captura de les comandes `cat /proc/mdstat` i `mdadm --detail` per demostrar que està funcionant 

4. Fent servir mdadm substitutiu una de les particions de l'altre dispositiu RAID (/dev/md1) per la  segona partició del disc que encara no estava en el RAID (/dev/sdc2). 
    * Feu una captura de la comanda `cat /proc/mdstat` i `mdadm --detail` per demostrar que està funcionant

---

#FpInfor #Smx #SmxMp06 #SmxMp06Uf02

* Resultats d'aprenentatge 1.4
* Continguts 1.2 1.3
---

###### Autor: Xavier Sala 2013.10.28 09:02:05
###### Editat per: Xavier Sala 2017.10.18 13:37:16
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
