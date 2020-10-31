# Consultant la API de last.fm
## DAW-MP04-UF2 - Exercici de Àmbits d’aplicació de l’XML
En aquesta pràctica farem consultes a la API de last.fm i:

* aplicarem xslt per a crear pàgines web amb els resultats 
* aplicarem xpath per fer consultes sobre els resultats.

**Preparatius**

1) Cal donar-se d'alta a [last.fm](https://www.last.fm/home) i també cal registrar una aplicació. Això ho fem des de l'enllaç `Add API account` de la pàgina [Last.fm Web Services Introduction](http://www.last.fm/api/intro)

2) Un cop tenim la **API key** ja podem fer consultes. Per exemple, per [consultar els àlbums](http://www.last.fm/api/show/album.search) que contenen la paraula `believe` la documentació ens diu que cal anar a la url: `http://ws.audioscrobbler.com/2.0/?method=album.search&album=somiador&api_key=YOUR_API_KEY`. Fixa't amb el paràmetre api_key a la url, que volen dir amb *YOUR_API_KEY*? Prova a baixar els resultats amb `wget`:

```bash
wget -q -O - "http://ws.audioscrobbler.com/2.0/?method=album.search&album=somiador&api_key=YOUR_API_KEY" 
```

Això retornarà un xml com aquest:

```xml
<?xml version="1.0" encoding="UTF-8" ?>
<lfm status="ok">
<results for="somiador">
<opensearch:Query role="request" searchTerms="somiador" startPage="1">
</opensearch:Query>
<opensearch:totalResults>1</opensearch:totalResults>
<opensearch:startIndex>0</opensearch:startIndex>
<opensearch:itemsPerPage>50</opensearch:itemsPerPage>
<albummatches><album><name>Somiadors</name>
<artist>BarraLliure!</artist>
<url>https://www.last.fm/music/BarraLliure%21/Somiadors</url>
<image size="small"></image>
<image size="medium"></image>
<image size="large"></image>
<image size="extralarge"></image>
<streamable>0</streamable>
<mbid></mbid>
</album>
</albummatches>
</results>
</lfm>


```
**Exercici**

1) Crea un compte a last.fm i fes una consulta com la de l'apartat anterior per comprovar que tot et funciona. Modifica la consulta per buscar altres paraules i observa els resultats.

2) Modifica la consulta anterior i busca els àlbums que continguin la paraula **Love**. Observa l'etiqueta `<opensearch:totalResults>` per saber quants àlbums contenen aquesta paraula.

3) Desa el resultat anterior a un fitxer: `> love.xml`. Fes una consulta xpath per veure els artistes: `xmllint --xpath "//artist" love.xml` Quin error t'apareix? A què és degut?

4) Modifica a mà el fitxer `love.xml` per posar el namespace d'[OpenSearch](http://www.opensearch.org/Specifications/OpenSearch/1.1): `<lfm status="ok" xmlns:opensearch="http://a9.com/-/spec/opensearch/1.1/">`. Repeteix ara la consulta anterior, encara et dona error? (doncs no te n'hauria de donar :)

5) Què fa la expressió xpath `xmllint --xpath "count(//album)" love.xml` ? Per què només hi ha 50 àlbums si abans hem vist que n'hauria d'haver molts més?

6) Consulta la documentació d'[Album Search](http://www.last.fm/api/show/album.search). Què fa el paràmetre `page`? Prova a fer-lo servir.

7) Fes una transformació de `love.xml` que ens quedi com aquesta pàgina:

![Love](http://i.imgur.com/AsLPJV4.png)

Nota: mira de millorar l'aspecte posant els separadors dels milers amb[format-number](https://www.google.es/search?q=xslt+format-number)

Nota: Quan treballes amb namespace cal demanar pel localname, per exemple, per agafar el valor d'un atribut d'un element amb namespace cal fer: `xmllint --xpath "string(//*[local-name()='Query']/@searchTerms)" love.xml`

Nota: No pots posar un `xsl:value-of` dins de les comentes d'un `src` d'una `img`. Llavors, has de fer servir un codi com aquest:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform">
<xsl:template match="/">
   <td>
     <img>
       <xsl:attribute name="src">
          <xsl:value-of select="//album/image[@size='large']"/> 
       </xsl:attribute>
     </img>
   </td>
</xsl:template>
</xsl:stylesheet>

```

8) Mira't una mica la documentació de la API, prova alguna altre consulta que sigui interessant i prova-la, per exemple el top d'artistes per pais.

---

#FpInfor #Daw #Dam #Asix #AsixMp04 #DawMp04 #DamMp04 #DawMp04Uf02 #AsixMp04Uf02 #DamMp04Uf02

---

###### Autor: daniel herrera 2017.02.21 09:43:41
###### Editat per: daniel herrera 2017.02.22 15:38:22
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
