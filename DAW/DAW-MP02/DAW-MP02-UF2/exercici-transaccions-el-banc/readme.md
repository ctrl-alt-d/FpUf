# Exercici transaccions. El banc.
## DAW-MP02-UF2 - Exercici de Llenguatges SQL: DML i DDL
Un banc té comptes corrents. Cada `compte corrent` s'identifica amb un número. Als comptes corrents es poden fer `moviments` que s'identifiquen també per un número de moviment que dona la màquina (identity). Els moviments, a més, tenen data, concepte i import, aquest últim pot ser possitiu o negatiu.

1) Crea les taules a la base de dades. Inserta 2 comptes bancaris amb 3 moviments cadascú.

2) El banc vol un resum del total de tots els ingressos ( imports positius ), totes les sortides ( imports negatius ) i el saldo. I volen que cuadri. Per fer-ho calen tres consultes diferents. Explica si és necessari posar les tres consultes dins una transacció i quin ha de ser el nivell mínim d'issolació d'aquesta transacció. Exemple d'informe:

```bash
Total Ingressos: 1000
Total Sortides:   750
Saldo:            250
```

3) Fes una transferència de diners d'un compte a un altre. De manera que primer treus els diners d'un compte i després el poses a l'altre. Explica quin serà el nivell mínim d'issolació d'aquesta transacció per a que les altres transaccions no vegin el que està passant aquí dins.

---

#FpInfor #Daw #Dam #Asix #AsixMp02 #DawMp02 #DamMp02 #DawMp02Uf02 #AsixMp02Uf02 #DamMp02Uf02

---

###### Autor: daniel herrera 2018.02.23 15:53:58
###### Editat per: daniel herrera 2018.02.23 16:25:03
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
