# Instal·lació d'Ubuntu amb RAID
## SMX-MP06-UF2 - Exercici de còpies de seguretat.
Tasca
-----------

###Teoria
1. Busca informació i explica els diferents tipus de RAID que hi ha i digues quins poden servir per 
aconseguir tolerància a fallades.
2. Explica els avantatges i inconvenients de fer servir RAID 1 respecte a RAID 0 i RAID 5
3. Dibuixa o copia d'Internet un esquema de com es distribueixen les dades dins dels discs de RAID 1

###Pràctica

1. En una màquina virtual sense sistema operatiu afegiu-hi dos discs
2. Afegiu el CD de Ubuntu Server i comenceu la instal·lació (recordeu que s'ha de fer el particionat de disc manual)
3. Creeu la taula de particions en un dels discs de manera que hi hagi quatre particions en cada un dels discs
    Assegureu-vos que les particions són iguals en tot dos discs
4. Creeu quatre dispositius RAID perquè facin mirroring entre les particions que siguin iguals entre els dos discs
    ![El resultat serà semblant a aquest](http://imageshack.us/a/img855/6990/a7fg.png "El resultat serà semblant a aquest")
5. Acabeu la instal·lació del sistema operatiu
6. Comproveu que el sistema està funcionant amb RAID comprovant /dev/mdstat


---

#FpInfor #Smx #SmxMp06 #SmxMp06Uf02

* Resultats d'aprenentatge 1.4
* Continguts 1.2 1.3
---

###### Autor: Xavier Sala 2013.10.28 09:48:45
###### Editat per: Xavier Sala 2013.11.03 22:06:03
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
