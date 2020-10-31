# django - Formularis I
## DAW-MP07-UF2 - Exercici de Generació dinàmica de pagines web.
Llegeix i familiaritzat amb els [formularis django](https://docs.djangoproject.com/en/dev/topics/forms/) i contesta aquestes preguntes.

1. Copia la definició de Widget, Field i Form.
2. **Form object**, què és un objecte form? De quina classe hereta? A que et recorda l'estil declaratiu dels forms?
3. Familiaritzat amb el [patró d'usar forms en una vista](https://docs.djangoproject.com/en/dev/topics/forms/#using-a-form-in-a-view). Que afegiries en aquest patró per indicar a l'usuari si tot ha anat bé?
4. Els valors que entra l'usuari als camps del formulari els trobem a *form.cleaned_data* (siguen *form* l'objecte formulari), però, que cal fer abans per poder trobar valors en aquest diccionari?
5. El formulari el pintem mitjançant templates. Podem tenir [un sol template per a tots els nostres formularis](https://docs.djangoproject.com/en/dev/topics/forms/#looping-over-hidden-and-visible-fields) o, si cal, podem fer un [template a mida](https://docs.djangoproject.com/en/dev/topics/forms/#customizing-the-form-template) per a un determinat formulari. Familiaritzat amb [els camps del formulari](https://docs.djangoproject.com/en/dev/topics/forms/#looping-over-the-form-s-fields). 


Els camps de formulari:

1. Familiaritzat amb els [camps de formulari que venen amb django](https://docs.djangoproject.com/en/dev/ref/forms/fields/#built-in-field-classes) i els seus corresponents widgets.
2. Quin widget li correspon a un BooleanField? A un CharField? A un ChoiceField? A un IntegerField? A un MultipleChoiceField?
3. Fes un formulari que utilitzi els fields esmentats a l'apartat anterior. Documenta el projecte.
4. Posa un [valor inicial](https://docs.djangoproject.com/en/dev/ref/forms/fields/#initial) al charField i a l'IntegerField.
5. Comprova que al MultipleChoiceField t'han triat exactament 3 opcions. Si no és així dispara un error. Apren com fer-ho a ['Cleaning a specific field attribute'](https://docs.djangoproject.com/en/dev/ref/forms/validation/#cleaning-a-specific-field-attribute)
6. Que ens aporta el ModelChoiceField respecte el ChoiceField? Quin paràmetre cal passar-li a ModelChoiceField?

---

#FpInfor #Daw #DawMp07 #DawMp07Uf02

* Resultats d'aprenentatge 1.d
* Continguts 1.3
---

###### Autor: daniel herrera 2014.01.08 15:02:03
###### Editat per: daniel herrera 2014.01.08 15:37:59
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
