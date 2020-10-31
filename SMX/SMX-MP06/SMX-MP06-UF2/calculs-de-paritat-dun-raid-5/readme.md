# Càlculs de paritat d'un RAID 5
## SMX-MP06-UF2 - Exercici de còpies de seguretat.
##Material de referència
Vídeo (12m, 57s) [RAID 5](http://youtu.be/blppUYdiNjY)

##Activitat
1. Donat el conjunt de 4 discs de la Figura 1 que munta un volum RAID 5, calcula els blocs de paritat (Ap, Bp, Cp, etc).
![Figura 1](http://presentastico.com/wp-content/uploads/2013/10/figura1-exercici-raid5.png "Calcular els bytes de paritat")
2. Imagina que es perdés el disc 1. Arriba una petició de lectura de la línia F, ¿es podria dur a terme? ¿Quina informació retornaria?
3. Quan encara no s'ha recuperat el disc 1, arriba una petició d'escriptura per a la línia F: cal escriure els valors **10001111 00001110 0101110**. ¿Creus que es podrà dur a terme aquesta operació? Fes les modificacions que creguis necessàries.
4. Suposa que ja han canviat el disc 1 i el sistema s'ha recuperat. Passen els dies, les dades van canviant i llavors es perd el disc 3. Recupera la informació del disc 3 fent servir la informació dels discs 0, 1 i 2. Amb aquest RAID5, en quins casos no es podria recuperar la informació?
![Figura 2](http://presentastico.com/wp-content/uploads/2013/10/figura2-exercici-raid5.png "Reconstruir Disc 3")

---

#FpInfor #Smx #SmxMp06 #SmxMp06Uf02

* Resultats d'aprenentatge 1.d
* Continguts 3
---

###### Autor: Carles Caño 2013.10.26 21:49:46
###### Editat per: Carles Caño 2013.10.26 22:01:33
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
