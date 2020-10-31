# XPath i factura electrònica
## DAW-MP04-UF2 - Exercici de Àmbits d’aplicació de l’XML
Genera una factura electrònica XML amb al menys dues línies de factura.

Excriu les expressions XPath per comprovar:

1. El total de la factura segons el camp `FileHeader`, `TotalInvoicesAmount` com a número.
2. El total de la factura sumant els camps `Items`, `InvoiceLine`, `TotalCost`. Com a número.
3. El nom dels productes a les línies de factura `Items`, `InvoiceLine`, `ItemDescription` com cadena de caracter.
4. El TaxIdentificationNumber de les parties ( `SellerParty` o `BuyerParty` ) que siguin `individual` i no pas `LegalEntity`.


* **Bonus point** Obté un booleà que ens digui si l'import total sumant els imports de les línies de factura és el mateix que l'import total de la factura consultant la capçalera. És a dir, si el resultat de l'exercici `1` i el `2` coincidèixen.

Utilitza [la línia de comandes](/DAW/DAW-MP04/DAW-MP04-UF2/xpath-executar-expressions-xpath-des-de-la-shell/readme.md) per obtenir els resultats.

---

#FpInfor #Daw #Dam #Asix #AsixMp04 #DawMp04 #DamMp04 #DawMp04Uf02 #AsixMp04Uf02 #DamMp04Uf02

---

###### Autor: daniel herrera 2016.12.16 15:09:27
###### Editat per: daniel herrera 2016.12.21 15:20:18
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
