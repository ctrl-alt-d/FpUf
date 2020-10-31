# Disseny conceptual E/R - SUPERMERCATS VAVI
## ASIX-MP02-UF1 - Exercici de Introducció a les bases de dades
**La Cadena de supermercats VAVI vol obrir la seva botiga-online aquests dies de nadal. Ens demanen un disseny de com hauria de ser la base de dades.**

* Els usuaris registrats a la web hi accediran mitjançant un nom d’usuari i un password. Aquest nom d’usuari identificarà un usuari envers els altres.

* A banda del nom d’usuari i el password, en el procés de registre, la plataforma demanarà les següents dades personals: Nom, Cognoms, email i DNI.

* Cal dir que no tots els usuaris registrats són clients, ja que es considera client aquell que alguna vegada ha realitzat alguna compra a través de la plataforma.

* A la web, els productes estan organitzats per categories (Begudes, Aliments frescos, Neteja i Llar,...) i subcategories (Begudes: aigua, refrescos, sucs, vins, licors,...;Aliments frescos: fruita i verdura, carnisseria, formatges, peixateria,... ). Tots els productes s'identifiquen mitjançant un codi de barres.
Dels productes en sabem el seu nom, el preu de venda públic, el preu de cost.
Per facilitar la feina a l'usuari la plataforma ofereix un recurs anomenat les "Llistes de la compra". Una "Llista de la compra" és un llistat d'articles que l'usuari ha escollit i guarda amb un nom. Un usuari pot tenir diferents llistes de diferents articles dins la plataforma. Cada llista s’identificarà envers les altres mitjançant un codi autogenerat per la plataforma.

* En qualsevol moment un usuari pot transformar una "Llista de la compra" en una comanda i realitzant-ne el pagament mitjançant una de les diferents formes de pagament (targeta de crèdit, PayPal, transferència bancària, pagar en el moment de rebre la comanda...) disponibles.

* En el procés de formalitzar la compra, la plataforma demanarà a l'usuari que especifiqui una adreça de facturació i una adreça d'enviament. Aquestes adreces es podran introduir en aquell mateix instant o bé es podran escollir de les introduïdes anteriorment. Qualsevol d’aquestes adreces hem de saber-ne l’adreça (carrer i número), el codi postal i la població.

* A la factura que el client rep a casa hi ha el detall de la compra amb les dades del client, l'adreça de facturació, el detall dels productes amb el preu de cada article, la quantitat de cada article, el subtotal, impostos aplicats, el possible descompte i el total de la factura. Aquesta factura també serà consultable on-line a través d'Internet pel client. 

* Per poder servir les diferents comandes la cadena de supermercats disposa d'una flota de transportistes encarregats de servir-les. De cada transportista en sabem el nom, l'adreça, la latitud, longitud i la ciutat a on es troba perquè s'assignaran les comandes a aquells que estiguin més a prop de l'adreça d'enviament que ha marcat el client en la comanda.

* Depenent de les ofertes que puguin fer els nostres proveïdors aquests ens vendran els productes a diferents preus. Ens interessa saber un històric de preus dels diferents productes i en quina data s'ha realitzat aquest canvi. Això pot provocar un canvi de preu en el preu de venda públic, però en aquest cas no ens interessarà guardar-ne l’històric.

**El nostre sistema cal que permeti. Entre altres coses, fer:**

* A final de mes hem de poder treure un llistat de les comandes que ha servit un transportista concret.
* Des de la fitxa de perfil de l'usuari es podran mantenir les diferents adreces de facturació i enviament, així com les formes de pagament preferides.
* A quines poblacions hem realitzat més enviament l’últim mes.

---

#FpInfor #Daw #Asix #Dam #AsixMp02 #DawMp02 #DamMp02 #AsixMp02Uf01 #DawMp02Uf01 #DamMp02Uf01

---

###### Autor: Robert Ventura 2018.10.06 14:13:10
###### Editat per: Robert Ventura 2018.10.06 14:13:10
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
