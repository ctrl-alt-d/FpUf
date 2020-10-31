# Gestió lògica de volums bàsica amb GNU/Linux (paquet lvm2)
## SMX-MP06-UF2 - Exercici de còpies de seguretat.
1. Afegeix quatre discos de 100 MB a una màquina virtual GNU/Linux.
2. Particiona els discos amb l'eina que vulguis i marca cada partició com a LVM.
3. Instal·la la utilitat per la gestió de volums lògics en GNU/Linux.
4. Marca els nous discos com a volums físics (PV) i executa la comanda que mostra informació dels diferents discos físics creats.  
5. Crea amb tres discos un grup de volums (VG), digues-li vg1 i executa la comanda que mostra informació dels diferents grups de volums creats. 
5. Crear un volum lògic (LV), anomena'l lv1 i fes que utilitzi tot l'espai del grup de volum vg1. Mostra que s'ha generat un directori a /dev i un fitxer dintre d'aquest directori que representa aquest volum lògic. 
6. Dona-li format ext4, munta'l i accedeix a ell.
7. Edita el fitxer /etc/fstab per a que munti aquest volum lògic a l'arrencar el sistema. Mostra com ho has fet. 
8. Afegeix el quart disc al grup de volum vg1 i augmenta la mida del volum lògic lv1 fins a la meitat del nou disc. Hauràs d'augmentar també la capacitat del sistema de fitxers que hi ha dins lv1 (fes servir la comanda resize2fs). 
9. Fes un altre volum lògic lv2 amb l'espai sense assignar del grup de volum vg1. 
10. Instal·la el paquet system-config-lvm (o des de la utilitat de disc) i visualitza l'estat dels volums.

---

#FpInfor #Smx #SmxMp06 #SmxMp06Uf02

---

###### Autor: Carles Caño 2016.11.10 14:31:34
###### Editat per: Carles Caño 2016.11.10 14:31:34
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
