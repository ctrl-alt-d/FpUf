# Sass - Sexy Buttons
## DAW-MP09-UF1 - Exercici de Disseny de la interfície. Estils.
**Presentació** [Preprocessadors CSS](https://docs.google.com/presentation/d/1SiHdo6uoXVy48Px_QqmG8hlsKVdhri3lx_IoKnZkIJY/edit?usp=sharing)

En aquesta activitat utilitzarem **Sass** per crear uns botons sexys per utilitzar en les nostres aplicacions.

![Sexy Buttons](http://i.imgur.com/JMGaQw6.png)

Primerament crea un nou projecte amb un arxiu ***index.html***, un arxiu ***app.scss*** on hi definirem els estils generals de tota l’aplicació i una altre arxiu partial anomenat ***_buttons.scss*** on hi definirem els estils dels botons.

En el fitxer ***index.html*** posar-hi un botó de cada tipus.
```html
  <button class="button">Default Button</button>
  <button class="button info">Info Button</button>
  <button class="button info disabled">Info Button Disabled</button>
  <button class="button success">Success Button</button>
  <button class="button warning">Warning Button</button>
  <button class="button danger">Danger Button</button>
```
En el fitxer ***app.scss*** defineix les següent variables que ens permetran configurar els nostres botons.
```
 $base-color: #999;        // Base color of your button 
 $border-radius: 10px;     // Button border radius 
 $border-width: 1px;       // Button border width 
 $padding: 0.5em 1.5em;    // Button padding 
 $font-size: 20px;         // Button font-size 
 $text-color: white;       // Button text color 
```
En el fitxer ***_buttons.scss*** defineix 2 mixins:

- **button-style**: que defineix les propietats bàsiques del botons a partir dels 3 paràmetres que rep (border-radius, font-size i padding). Fes, també, que al posar el ratolí sobre el botó els cursor sigui de tipus pointer. 

- **button-color**: que defineix les propietats de color del botons a partir dels 2 paràmetres que rep (base-color i text-color). 

    - El **color de fons** dels botons ha de ser un gradient des del color base aclarit un 25% fins al color base enfosquit un 10%.
*Nota:* per aclarir i enfosquir color fes servir les funcions lighten() i darken() 
    - El **border** del botó ha de ser de 1px i color és el color base enfosquit un 25%. 
    - La **ombra** del botó ha de tenir una ombra interna del color base aclarit un 15%. 
    - El text del botó ha de ser del color definit pel paràmetre text-color i amb una ombra de color igual al color base enfosquit 60%; 
    - Quan es faci **hover** en el botó, el color de fons ha de ser d’un gradient més fosc que l’actual.
*Nota:* Recorda utilitzar el selector pare &. 
    - Defineix una classe **disabled** que permeti deshabitar els botons mostrant-los semi-transparents, amb el cursor per defecte i el color de fons el color base. 

Finalment, en el fitxer ***app.scss*** crea les regles css per cada classe (button, info, success, warning, danger) i utilitza el mixins definits anteriorment per establir l’estil d’aquestes classes.

**Altres consideracions:**

- Utilitza regles i propietats aniuades sempre que sigui possible (i utilitzant el selector pare &). 
- Posa comentaris d’una línia amb // i comprova que els generar el CSS no es mostren.

---

#FpInfor #Daw #DawMp09 #DawMp09Uf01

---

###### Autor: Sergi Coll 2016.11.04 15:54:31
###### Editat per: Sergi Coll 2016.11.15 12:25:02
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
