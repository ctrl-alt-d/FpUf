# django - Consumir Web Service senzill amb AJAX
## DAW-MP07-UF4 - Exercici de Serveis web. Pàgines dinàmiques interactives. Webs Híbrids.
A la pràctica anterior hem preparat un Web Service senzill que [donada una cadena de caracters ens retorna un número màxim de persones que la contenen al seu nom o cognos](/DAW/DAW-MP07/DAW-MP07-UF4/django-construccio-dun-web-service-senzill/readme.md).

En aquesta pràctica anem a cridar aquest Web Service des del navegador client sense recarregar la pàgina. Usarem AJAX.

A la pràctica anterior haviem creat 1.000 persones. Des del punt de vista d'expericència d'usuari (UX) no és gaire recomenable que la Interface d'Usuari (UI) li mostri un control select amb 1.000 opcions. L'alternativa és un control *input text - select* combinat on les *opcions* del control *select* s'omplin dinàmicament amb el nom de les persones que contenen els caracters que l'usuari entra al control *input text*.

Per tant, hem de substituir el contrl html *select* per un control més ric en funcionalitats.

El procés de generar dinàmicament les opcions del select requereix que a mesura que l'usuari introdueix caracters al control *text*, es llenci una petició al web service i, a partir de la resposta d'aquest, oferir a l'usuari valors que cassin amb el que està buscant. Aquesta crida al web service es realitza **sense recarregar la pàgina html**, només les *opcions* de la *select* es recarreguen, això s'anomena AJAX.

La proposta és la següent, primer farem un formulari clàsic i li aplicarem *[Select2](http://ivaynberg.github.io/select2/)* per millorar una mica el control html *select*. Després ve la part amb AJAX on les opcions del select provenen del resultat d'una crida al WebService.

**Primera part de la pràctica:**

* A la nostre aplicació de recursos humans crearem un nou model anomenat `nòmina`. Aquest model tindrà `data nòmina`, `persona` i `import_nòmina`
* Crearem un *modelform* per tal de fer les operacions *Create* i *Update* de nòmines.
* Crearem les vistes i urls per comprovar que tot funciona.
* Aplicarem Bootstrap a la nostra interfície d'usuari.
* Aplicarem *[Select2](http://ivaynberg.github.io/select2/)* al control `<select id="id_persona"` d'html.
* Comprovarem que la IU és més rica amb el *[Select2](http://ivaynberg.github.io/select2/)*

**Segona part de la pràctica**, anem a millorar l'experiència d'usuari:

* [Substituirem](https://docs.djangoproject.com/en/dev/topics/forms/modelforms/#overriding-the-default-fields) el widget [select](https://docs.djangoproject.com/en/dev/ref/forms/widgets/#django.forms.Select) per un [hidden](https://docs.djangoproject.com/en/dev/ref/forms/widgets/#hiddeninput). Explicació: *[Select2](http://ivaynberg.github.io/select2/)* s'encarregarà de substituir el control *hidden* per un control *select*. 
* Utilitzarem *[Select2](http://ivaynberg.github.io/select2/)* per tal d'invocar les peticions al nostre Web Service. Cal entendre l'apartat 'Loading Remote Data'. El professor us explicarà quins són els paràmetres i com funciona aquest potent control javascript. 

![Selec2](http://i.imgur.com/msYXRaW.png)

**Entregables**

* Codi dels models, vists i urls.
* Codi del template amb `select2`.
* Captura de la pràctica en funcionament.






---

#FpInfor #Daw #DawMp07 #DawMp07Uf04

---

###### Autor: daniel herrera 2014.02.23 18:18:43
###### Editat per: daniel herrera 2014.02.28 15:28:45
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
