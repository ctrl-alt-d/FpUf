# jQuery i jQueryUI. Slideshow
## DAW-MP06-UF3 - Exercici de Esdeveniments. Manegament de formularis. Model d'objectes del document.
#jQuery i jQueryUI. Slideshow

Aquest exercici consisteix en desenvolupar un slideshow amb **jQuery i jQuery UI** a partir dels fitxers que trobaràs en aquest [enllaç](https://drive.google.com/file/d/0B6Jts4d21oYLNDktM0E3NUNsVUE/view?usp=sharing).

![Slideshow](http://i.imgur.com/heJZN43.png?1)

##Activitat
 
**1. MOSTRAR IMATGE ACTUAL (2 punts)**

* a) (1,5p) Fes una funció anomenada **mostraActual()** que mostri la imatge en miniatura que té la classe **actual** a la part central del slideshow.

  Fes que la imatge que es mostra actualment depereixi lentament amb un efecte i **quan finalitzi** aquest efecte aparegui la nova imatge lentament.

  Aquesta funció també ha **d'actualitzar la informació** de la imatge (Títol i Autor) a partir de la dades que es guarden en els atributs data de la miniatura.

* b) (0,5p) Fes que quan es faci **click sobre una imatge de les miniatures** , es mostri aquesta imatge en l'àrea central del slideshow utilitzant la funció anterior.

**2. INFORMACIÓ DE LA IMATGE (2 punts)**

* a) (0,5p) Fes que quan el ratolí passi per sobre la imatge central del slideshow, es **mostri** amb un efecte llistant la **informació**** de la imatge**. Cal fer desaparèixer la informació, també amb un efecte llistant, quan el ratolí surti de sobre la imatge.

  **Recorda** ocultar d'entrada la informació de la imatge.

* b) (0,5p) Fes que es pugui **editar la informació** de la imatge actual quan es faci click sobre el botó **Editar**.  D'entrada, el formulari ha d'estar ocult i es mostrarà, amb un efecte lliscant, quan es faci click sobre el botó editar.

* c) (1p) Un cop editada la informació s'ha de guardar fent click al botó **Guardar** i les noves dades s'han d'actualitzar en la informació de la imatge i també en els atributs data de la imatge en miniatura.

  Un cop guardades les dades, cal fer que **el formulari s'oculti** amb un efecte llistant.

  I finalment, per poder comprovar fàcilment que els canvis s'han realitzat, farem **que la informació de la imatge aparegui** , es mostri 3 segons i torni a desaparèixer.

**3. BOTONS PER DESPLAÇAR-SE PER LES IMATGES (2 punts)**

* Fes que els botons per **desplaçar-se a través de les imatges** de la galeria funcionin correctament.

  **Important** , cal fer que se prems Següent i ens trobem a la última imatge, passi a la primera. I igualment, si fem Anterior i estem a la primera imatge.

**4. AUTOPLAY (1 ,5 punts)**

* a) (1p) Si es prem el botó **Autoplay** s'iniciarà la **reproducció automàtica** de les imatges de la galeria. Es mostrarà una nova imatge cada 3 segons i de forma ordenada. Quan s'arribi a la última imatge, es passarà a la primera imatge.

  També **canviarem l'icona de play** per un de pausa. La classe que cal utilitzar per mostrar l'icona de pausa és_glyphicon-pause_.

* b) (0,5p) Finalment, si es torna a prémer el botó de Autoplay cal **aturar la reproducció automàtica** i tornar a mostrar l'icona de play.

**5. ELIMINACIÓ D'IMATGES DRAG&DROP (2,5 punts)**

* a) (2p) Fes que es puguin **eliminar imatges** de la galeria arrossegant-les cap a la paperera. Un cop deixem anar la miniatura sobre la paperera, s'ha d'afegir la imatge dins la paperera definint l'amplada de la imatge al 100% per tal que s'adapti a l'amplada de la paperera.

* b) (0,5p) Canvia el **cursor**** a tipus move **quan estem arrossegant la imatge i investiga l'opció **revert** del mètode draggable per fer que si es deixa anar la imatge a un lloc que no sigui la paperera, retorni a la seva posició original.

---

#FpInfor #Daw #DawMp06 #DawMp06Uf03

---

###### Autor: Sergi Coll 2016.05.11 15:27:04
###### Editat per: Sergi Coll 2016.05.11 16:57:09
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
