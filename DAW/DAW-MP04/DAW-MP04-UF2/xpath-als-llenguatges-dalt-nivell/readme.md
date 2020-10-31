# XPATH als llenguatges d'alt nivell
## DAW-MP04-UF2 - Exercici de Àmbits d’aplicació de l’XML
Observa aquest script de Python extret de [How To Scrape Amazon Product Details and Pricing using Python](https://www.scrapehero.com/tutorial-how-to-scrape-amazon-product-details-using-python/):

```python
from lxml import html
import requests
from time import sleep

url = "http://www.amazon.com/dp/B0046UR4F4"
headers = {'User-Agent': 'Mozilla/5.0 (compatible; MSIE 10.0; Windows NT 6.2; Trident/6.0)'}
page = requests.get(url,headers=headers)
sleep(8)
doc = html.fromstring(page.content)
xpath_name = '//h1[@id="title"]//text()'
raw_name = doc.xpath(xpath_name)
name = ' '.join(''.join(raw_name).split()) if raw_name else None
print "---------------"
print name
print "---------------"


```

**Exercici**

Tot i que no hagis estudiat Python és un llenguatge que pots seguir amb facilitat doncs té una sintaxi molt intuitiva. 

Hauras de provar aquest script, per tant, cal que executis les següents comandes:

```sh
mkdir -p ~/path/on/posaràs/l/script
cd ~/path/on/posaràs/l/script
virtualenv venv
source venv/bin/activate
pip install requests lxml
mousepad p.py   #<- un cop obert copy paste de l'script
python p.py 2> /dev/null
ls

```
Contesta:

1. Per a que serveix aquest script?
2. En quin format emmagatzema les dades aquest script?
2. Observa cada expressió XPATH i digues que fa.
3. Afegeix una expressió XPATH per tal que, donat un enllaç de videojoc, també informi de la seva classificació. Exemple, donada la url: `https://www.amazon.es/dp/B00MPM2ENW/` hauria de dir `No recomendada para menores de 16 años`

Exemples de com anar a buscar la classificació.

![Imgur](http://i.imgur.com/uV0a1is.png)

**Exemple 1** Busco un node `span` que contingui el text *'Clasificación.'* i agafo el text del seu germà:

```python
x="//span[contains(text(), 'Clasificado')]/following-sibling::span/a/text()"
doc.xpath(x)
[u'  \n                No recomendada para menores de 16 a\xc3\xb1os \n            ']
```

---

#FpInfor #Daw #Dam #Asix #AsixMp04 #DawMp04 #DamMp04 #DawMp04Uf02 #AsixMp04Uf02 #DamMp04Uf02

---

###### Autor: daniel herrera 2017.02.05 15:10:54
###### Editat per: daniel herrera 2017.02.15 15:30:13
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
