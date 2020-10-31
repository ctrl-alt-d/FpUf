# El Telenotícies
## DAW-MP04-UF2 - Exercici de Àmbits d’aplicació de l’XML
Instal·lat un programa de sintetització de veu, que et permeti enviar text als micros. Per exemple `spd-say` ( Més info: [How to text-to-speech output using command-line?](http://askubuntu.com/questions/501910/how-to-text-to-speech-output-using-command-line) )

Fés un script que, pasan't una url d'un RSS llegeixi totes les notícies. Pots afegir-hi més contingut, per exemple pot començar dient 'Aquestes són les notícies del dia' i entre notícia i notícia pot dir 'en un altre àmbit de coses ....'.

**L'script farà el següent:**

1) Llegirà la url:

```bash
echo -n "Enter some url > "
read url
echo "You entered: $url"
```

2) Descarregarà la url a un fitxer ( pots fer servir `curl` o `wget` )

```bash
wget -O producte.html \
--header="Accept: text/html" \
--user-agent="Mozilla/5.0 (Macintosh; Intel Mac OS X 10.8; rv:21.0) Gecko/20100101 Firefox/21.0" \
$url
```

4) Amb alguna utilitat per traballar xPath, per exemple `xmllint`, cal extreure els titulars i les notícies.

5) Ho enviem als altaveus. Pots decodificar les entitats html com ara `&lt;` usant `xmlstarlet` 


**Solució**

```bash
#!/bin/bash
echo -n "Enter some url > "
read url
echo "Downloading $url"
wget -O el_meu_rss.xml $url 2> /dev/null
if [ $? -ne 0 ]
then
   echo "error baixant rss"
   exit $?
fi
echo -ne "done! "
numero=`xmllint  --xpath "count(/rss/channel/item/title)" el_meu_rss.xml`
echo "$numero items:"
for titol in $(seq 1 $numero)
do
  a_title=`xmllint --nocdata   --xpath "/rss/channel/item[$titol]/title/text()" el_meu_rss.xml | xmlstarlet unesc`
  a_description=`xmllint --nocdata  --xpath "/rss/channel/item[$titol]/description/text()" el_meu_rss.xml | xmlstarlet unesc`  
  echo  $a_title
  echo $a_title | spd-say -e -w 
  echo  $a_description
  echo $a_description | spd-say -e -w 
done
```

**Exemple:**

```bash
dani@egg-v3:~/tmp/324324$ ./p.sh 
Enter some url > http://feeds.bbci.co.uk/news/rss.xml
Downloading http://feeds.bbci.co.uk/news/rss.xml
done! 44 Items:
Donald Trump says UK 'doing great' after Brexit vote ...

```


        
**Opció 2**

En comptes de transmetre les notícies pots connectar-te a e-commerce i cantar preus de productes. Et caldrà transformar la pàgina HTML en XML. Instal·lat el programa `tidy` que et permet convertir un document html en xml ( usant l'opicó `-asxml` )

```bash
tidy --force-output yes -asxml producte.html > producte.xml
```

---

#FpInfor #Daw #Dam #Asix #AsixMp04 #DawMp04 #DamMp04 #DawMp04Uf02 #AsixMp04Uf02 #DamMp04Uf02

---

###### Autor: daniel herrera 2016.12.21 15:32:32
###### Editat per: daniel herrera 2017.01.16 10:14:08
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
