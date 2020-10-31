# Introducció a AJAX. Prediccions metereològiques
## DAW-MP06-UF4 - Exercici de Comunicació asíncrona client-servidor.
#Introducció a AJAX. Prediccions metereològiques

En aquesta activitat utilitzarem **AJAX **per fer peticions a la **_API OpenWeatherMap_**** **que ens donarà informació sobre la predicció metereològica d’una ciutat.

Podem trobar tota la informació sobre aquesta API a [http://openweathermap.org/api](http://openweathermap.org/api).

Per fer ús d’aquesta API, necessitaràs disposar d’una **API KEY**. Pots registrar-te a la web per obtenir-me una o bé fer ús de la següent clau.

```
API KEY = "906a992f434bb3aca14ffb6ff41010fa";
```

##Activitat

**Exercici 1: Objecte XMLHttpRequest**

Fes una interfície web que et permeti escollir entre diverses ciutats europees i un cop seleccionada la ciutat, et mostri la predicció metereològica d’aquella ciutat.

Utilitza el sistema que vulguis per seleccionar les ciutats (un desplegable, varis botons, etc).

La **_API OpenWeatherMap_** ens permet sol·licitar la informació meteorològica en **format
html **i per tant la visualitació en el web serà molt més sencilla. 

La petició AJAX ha d’anar dirigida a la següent url:

```
http://api.openweathermap.org/data/2.5/weather?q="+*ciutat*+"&mode=html&APPID=" + *api_key*
```
Un cop obtinguda la predicció per AJAX, cal mostrar-la a la interfície sense recarregar la pàgina.

**Exercici 2: Mètodes AJAX de jQuery**

Fes el mateix exercici anterior, però ara utilitzant els mètodes que ens proporciona **jQuery ** per fer peticions AJAX.

---

#FpInfor #Daw #DawMp06 #DawMp06Uf04

---

###### Autor: Sergi Coll 2016.05.12 15:31:57
###### Editat per: Sergi Coll 2016.05.12 16:21:57
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
