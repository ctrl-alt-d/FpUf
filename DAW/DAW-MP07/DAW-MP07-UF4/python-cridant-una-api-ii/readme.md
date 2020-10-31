# Python - Cridant una API II
## DAW-MP07-UF4 - Exercici de Serveis web. Pàgines dinàmiques interactives. Webs Híbrids.
Un cop completat l'exercici [Python - Cridant una API](/DAW/DAW-MP07/DAW-MP07-UF4/python-cridant-una-api/readme.md) aprendrem a tractar el resultat de la crida.

Per a l'exercici esmentat el resultat a tractar és la confirmació que l'event s'ha creat:

    {
        "created": true
    }

A l'exercici anterior pintavem aquest resultat com una cadena de caracters, però hem d'apendre a representar-ho amb les estructures del propi llenguatge.

**Exercici**

 * Llegeix i compren [JSON encoder and decoder](http://docs.python.org/2/library/json.html) l'apartat *Decoding JSON*, és tan fàcil com sembla. Fixat en que el resultat no és un string sino una llista amb un string i un diccionari que, a la seva vegada, conté una llista com a valor.
 * Decodifica el json que t'envia *keen.io*. I accedeix al valor de 'created'
 * Apren a distingir `stream` de `string`. Fixat que la resposta la rebem en un *stream* i que python pot llegir-lo sense haver de carregar-lo en un *string*, mitjançant el mètode `load` ( en compte de *loads* ).
 * Fes crides a l'API per obtenir [recomptes](https://keen.io/docs/getting-started-guide/#simple-count-request), sumes, mitjanes i mostra els seus valors. Exemple `https://api.keen.io/3.0/projects/PROJECT_ID/queries/count?api_key=READ_KEY&event_collection=COLLECTION_NAME&group_by=vista`
 * Fes una crida complexa i recorre el resultat. Per exemple, [request with interval](https://keen.io/docs/getting-started-guide/#request-with-interval) 
 * Fes una crida a google maps per aconseguir el codi postal d'una adreça. Mira el codi amb php d'exemple.

Codi d'exemple amb PHP (from [Using Google Maps to lookup UK Postcodes](http://ben-major.co.uk/2012/02/using-google-maps-to-lookup-uk-postcodes/) post):

```php
<?php
// First, we need to take their postcode and get the lat/lng pair:
$postcode = $_REQUEST['postcode'];

// Sanitize their postcode:
$search_code = urlencode($postcode);
$url = 'http://maps.googleapis.com/maps/api/geocode/json?address=' . $search_code . '&sensor=false';
$json = json_decode(file_get_contents($url));

$lat = $json->results[0]->geometry->location->lat;
$lng = $json->results[0]->geometry->location->lng;

// Now build the lookup:
$address_url = 'http://maps.googleapis.com/maps/api/geocode/json?latlng=' . $lat . ',' . $lng . '&sensor=false';
$address_json = json_decode(file_get_contents($address_url));
$address_data = $address_json->results[0]->address_components;

$street = str_replace('Dr', 'Drive', $address_data[1]->long_name);
$town = $address_data[2]->long_name;
$county = $address_data[3]->long_name;

$array = array('street' => $street, 'town' => $town, 'county' => $county);
echo json_encode($array);
```


**En aquest exercici hem aprés:**

1 | 2 
---|---
Rebre json com stream |  deserialitzar json a estructures Python  




---

#FpInfor #Daw #DawMp07 #DawMp07Uf04

---

###### Autor: daniel herrera 2014.02.14 12:55:45
###### Editat per: daniel herrera 2016.02.17 16:41:51
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
