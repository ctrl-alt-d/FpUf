# Selects, complexitat mitjana. Servei tècnic
## DAW-MP02-UF2 - Exercici de Llenguatges SQL: DML i DDL
Observa aquestes taules:

```sql
create table tecnic ( 
 idTecnic int, 
 nom varchar(100), 
 constraint tecnic_pk primary key (idTecnic) 
) ;
create table producte ( 
 idProducte int, 
 nom varchar(100), 
 constraint producte_pk primary key (idProducte) 
) ;
create table client ( 
 idClient int, 
 nom varchar(100), 
 esPrincipal char(1),
 constraint client_pk primary key (idClient) 
) ;
create table incidencia( 
  idIncidencia int  not null, 
  data date  not null, 
  idTecnicQueAten int not null, 
  idTecnicQueResol int null, 
  idClient int not null, 
  idProducte int not null, 
  constraint incidencia_pk primary key (idIncidencia ), 
  constraint incidencia_ak unique ( data, idProducte ), 
  constraint incidencia_a_tecnic_aten_fk 
  foreign key (idTecnicQueAten) references tecnic( idTecnic ), 
  constraint incidencia_a_tecnic_resol_fk 
  foreign key (idTecnicQueResol) references tecnic( idTecnic ), 
  constraint incidencia_a_client_fk 
  foreign key (idClient) references client( idClient ), 
  constraint incidencia_a_producte_fk 
  foreign key (idProducte) references producte( idProducte ) 
);

```
1. Fés el MCD per poder tenir una visió global de l'estructura de la base de dades:
0. Inserta els tècnics: 'Marta', 'Carles', 'Jaume' i 'Miren'. Inserta 3 clients principals (esPrincipal='S'), 3 productes, 8 incidències no resoltes ( sense idTecnicResol ) i 2 de resoltes.
2. Selecciona tots els tècnics que el seu nom contingui la lletra 'A'
3. Selecciona el número total d'incidències no resoltes (idTecnicResol valdrà null) dels clients principals (esPrincipal = 'S') amb més de 2 incidències no resoltes. Es demana idClient, nomClient i número d'incidències.
4. Selecciona tots els tècnics (id i nom) acompanyats del total d'incidències que han resolt. Cal que apareguin tots els tècnis, hagin o no resolt alguna la incidència. Ordenat per número d'incidències resoltes de més a menys.
5. Total de incidències gestionades per tècnic i producte (nom tècnic, nom producte, total). Ordenat per número incidències descendent. Cal que aparegui el nom del tècnic que resol, i si no està resolta, el nom del tècnic que aten.
6. Diferents noms del tècnic que resol i nom del tècnic que aten de totes les incidències on el tècnic que resol és diferent al tècnic que aten i estan resoltes. Es demana: tecnic que aten, tecnic que resol, nom producte sense fileres duplicades.
7. Afegeix el camp `stock int not null default 0` a `producte`.
8. Posa l'stock a 100 a tots els productes que continguin la lletra 'A'.
9. Inicia una transacció, esborra totes les fileres de la taula de incidències, comprova que està buida, desfés la transacció.
10. Incrementa en un 10% l'stock de tots els productes.
11. Posa a 0 els productes sobre els quals hi ha incidències no tancades.
12. Escriu les instruccions SQL per a insertar dos tècnics, un prunducte, un client i una incidència.
13. *["No te olvides de poner el where en el Delete From"](https://www.youtube.com/watch?v=i_cVJgIz_Cs)*

---

#FpInfor #Daw #Dam #Asix #AsixMp02 #DawMp02 #DamMp02 #DawMp02Uf02 #AsixMp02Uf02 #DamMp02Uf02

---

###### Autor: daniel herrera 2013.09.07 14:39:40
###### Editat per: daniel herrera 2018.02.15 18:09:42
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
