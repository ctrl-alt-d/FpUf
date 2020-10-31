# La factura electrònica
## DAW-MP04-UF1 - Exercici de Programació amb XML
Des del 15 de gener de 2015 les empreses estan obligades a que les factures que presentin a les Administracions Públiques siguin en format electrònic.

Les factures electròniques han de seguir el format Facturae, podeu trobar exemples d'aquest format a la web [http://www.facturae.gob.es/](http://www.facturae.gob.es/) a l'apartat Format Facturae.

El format facturae és un format XML.

**Exercici 1**

Descarrega't l'aplicació **Facturae** del Ministerio de Industria, Energía y Turismo que trobaràs a la web [http://www.facturae.gob.es/](http://www.facturae.gob.es/).

Fes una factura que contingui al menys 3 línies de factura. Totes elles amb iva. Una línia de factura les unitats seran hores ( per exemple 10 hores de programació a 40€ l'hora) i la segona línia seran ratolins. Posa dos descomptes pels motius que se t'acudeixin.

Genera l'XML des de l'aplicació i busca i documenta els imports de la teva factura dins l'XML. Mira quines etiquetes fa servir el format Facturae per tal de codificar la informació.

Documenta la pràctica de manera que es vegi la interfície d'usuari del programa Facturae i alguns dels imports que has entrat i com han quedat codificats dins l'XML.

* Quina etiqueta identifica al 'Comprador' ?
* Quina etiqueta identifica al 'Venedor' ?
* Sota quina etiqueta estan tant el comprador com el venedor?
* Quina etiqueta conté les línies de factura?
* I la capcelera de la factura?
* On trobem l'import total?
* Com és diu l'etiqueta principal?
* Com es codifiquen les dates?
* Busca algun atribut amb dades que hagis introduit tu a l'aplicació. En trobes cap?

**Exercici 2**

El Ministerio de Industria, Energía y Turismo disposa d'un [validador de factures XML](http://sedeaplicaciones2.minetur.gob.es/FacturaE/) que et dirà si la teva factura és correcta. Ull, pot ser que aquest validador només sàpiga treballar en format Facturae 3.1



* Valida la factura que acabes de realitzar. Desmarca la validació de signatura perquè no l'hem signat. Si no et valida, canvia el format a 3.1 dins l'XML. 
* Provoca errors al validador tot canviat alguna etiqueta del teu XML. Provoca dos tipus d'errors: etiquetes mal tencades. etiquetes que troba on no pertoca.






---

#FpInfor #Daw #Dam #Asix #AsixMp04 #DawMp04 #DamMp04 #DawMp04Uf01 #AsixMp04Uf01 #DamMp04Uf01

---

###### Autor: daniel herrera 2016.10.05 13:45:39
###### Editat per: daniel herrera 2016.10.05 14:29:27
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
