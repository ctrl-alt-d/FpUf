# Examen DDL i Consultes
## DAW-MP02-UF2 - Exercici de Llenguatges SQL: DML i DDL
Observa aquestes taules d'una BDD:


```bash
Clients ( Nif (PK), Nom )
Factures ( nFactura (PK), Data, Descripcio, Nif (FK1 a clients) )
FamiliesProductes ( nFamilia (PK), nomFamilia )
Productes ( nProducte (PK), Descripcio, PreuDeReferencia, 
            nFailia (FK1 a FamiliesProductes) )
LiniesDeFactura( Quantitat, preuDeVendaUnitari, 
                 nProducte (PK) (FK1 a Productes), 
                 nFactura (PK) (FK2 a Factures) )
```


**Aclariment**: Dins les LiniesDeFactura emmagatzemem el detall d'una factura, és a
dir, la quantitat de cada producte de la factura acompanyat del preu unitari al que
l'hem venut.
**Nota necessaria per a fer el DDL**: No tots els productes tenen una família,
exemples de famílies podrien ser 'refrigerats', 'higene', món animal', 'bebé', ....


1. Expresa aquestes manteixes taules amb les seves relacions utilitzant el diagrama de caixes treballat a classe (LDM)
2. Create: Escriu el create de totes les taules.
3. Insert: Inserta dues famílies i dos productes. Un producte no ha de tenir família i l'altre sí.
4. Consulta: Nom de tots els clients que continguin una 'F' (o 'f') al seu nom.
5. Consulta: Nom dels clients acompanyats de la quantitat de productes que han comprat i el total facturat ( exemple “el client 1 ha comprat 120 productes i ha pagat en total 300€” : Client1, 120, 300 ). Compte, per saber la quantitat has de sumar la quantitat que apareix a la línia de factura, per saber l'import has sumar el resultat de
multiplicar quantitat pel preu de venda.
6. Consulta: Tots els clients que han comprat més de 5 productes.
7. Nom dels clients als que hem facturat per sobre de la mitjana (per saber el total de cada factura cal sumar el resultat de Quantitat x preuDeVendaUnitari de totes les línies de la factura d'aquell client ) La mitjana es calcula sumant tot el Quantitat x preuDeVendaUnitari i dividint pel número de clients.
8. Consulta: Nom de tots els productes de la familia amb nom 'refrigerats' utilitzant una subconsulta i utilitzant un inner join
9. Consulta: Nom del producte i nom de la família tingui o no família. Utilitza la funció coalesce per a que aparegui 'Sense família' aquells productes que no en tenen.
10. Transaccions: En aquesta empresa els preus fluctuen constantment i volem assegurar-nos que les factures que es facis des del precís instant que modifiquem el preu d'un producte portaran el nou preu. Quan es fa una factura cal llegir el
PreuDeReferencia de la taula 'Productes' per posar-lo a preuDeVendaUnitari de la taula 'LiniesDeFactura'. 

Ho podem veure en aquest pseudo codi:

```sql
--­­inici transacció.
BEGIN TRANSACTION;
SET TRANSACTION ISOLATION LEVEL ????
--­­dades a insertar
SET @producte_a_comprar=12;
SET @nFactura=35;
SET @qtat=3;
­­--busquem el preu
SELECT @PreuDeReferencia = PreuDeReferencia
  FROM productes
 WHERE nProducte = @producte_a_comprar;
--­­insertem la línia dins la factura
INSERT INTO LiniesDeFactura( Quantitat, preuDeVendaUnitari, nProducte, nFactura )
VALUES ( @qtat, @PreuDeReferencia, @producte_a_comprar, 3, @nFactura )
­­--FI
COMMIT;
```

Pregunta: Llegint el pseudocodi argumenta quin és el primer nivell d'isolació que ens
garantirà els requeriments de l'enunciat.

---

#FpInfor #Daw #Dam #Asix #AsixMp02 #DawMp02 #DamMp02 #DawMp02Uf02 #AsixMp02Uf02 #DamMp02Uf02

---

###### Autor: daniel herrera 2017.02.13 18:59:48
###### Editat per: daniel herrera 2017.02.13 19:06:25
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
