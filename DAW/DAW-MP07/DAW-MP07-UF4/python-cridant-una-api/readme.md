# Python - Cridant una API
## DAW-MP07-UF4 - Exercici de Serveis web. Pàgines dinàmiques interactives. Webs Híbrids.
Realitza el [getting started de keen.io](https://keen.io/docs/getting-started-guide/).

Ara envia crea l'event fent un post des del teu llenguatge de programació. Exemple des de Python:

    import json
    import urllib2
    
    url = 'https://api.keen.io/3.0/projects/<project_id>/events/<event_collection>?api_key=<write_key>'
    
    values_dict = {"category": "magical animals",
                   "animal_type": "pegasus",
                   "payment_type": "head of medusa",
                   "price": 4.50}
    values = json.dumps( values_dict )
    headers = { 'Content-Type': 'application/json' }
    req = urllib2.Request(url, values, headers)
    response = urllib2.urlopen(req)
    print response.read()

**Exercici**:

 * Estudia com serialitzar [estructures django a json](http://docs.python.org/2/library/json.html)
 * Enten i comenta línia a línia el codi Python de l'exemple que crida la API [keen.io](https://keen.io/).
 * Passa a fer la segona part de l'exercici [Python - Cridant una API II](/DAW/DAW-MP07/DAW-MP07-UF4/python-cridant-una-api-ii/readme.md).

**En aquest exercici hem aprés:**

1 | 2 | 3
---|---|---
Crear estructura python |  Serialitzar a json |  Enviar json 




---

#FpInfor #Daw #DawMp07 #DawMp07Uf04

---

###### Autor: daniel herrera 2014.02.10 18:52:00
###### Editat per: daniel herrera 2014.02.14 20:27:38
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
