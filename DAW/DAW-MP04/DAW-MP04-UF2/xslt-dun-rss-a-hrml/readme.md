# XSLT d'un RSS a HTML
## DAW-MP04-UF2 - Exercici de Àmbits d’aplicació de l’XML
Transforma a HTML un RSS mitjançant XSLT usant només `<xsl:template match=" ___ ">`, `<xsl:value-of select=" ___ "/>` i `<xsl:apply-templates select=" ____ "/>`.

Cal una pàgina html amb el nom del canal com a H1 i el títols, enllaços i descripció de les notícies usant `div` i donant format a la pàgina. Els divs de cada notícia tindran amplada 400px amb padding de 10px i cal que flotin a l'esquerra de manera que la pàgina sigui responsiva. A [Learn CSS Layout](http://learnlayout.com/inline-block.html) podeu trobar un exemple de pàgina amb divs que floten.

**Exemple de css**



```xml
<?xml version="1.0" encoding="UTF-8"?>
<?xml-stylesheet title="XSL_formatting" type="text/xsl" href="/shared/bsp/xsl/rss/nolsol.xsl"?>
<rss xmlns:dc="http://purl.org/dc/elements/1.1/" xmlns:content="http://purl.org/rss/1.0/modules/content/" xmlns:atom="http://www.w3.org/2005/Atom" version="2.0" xmlns:media="http://search.yahoo.com/mrss/">
    <channel>
        <title><![CDATA[BBC News - Home]]></title>
        <description><![CDATA[BBC News - Home]]></description>
        <link>http://www.bbc.co.uk/news/</link>
        <image>
            <url>http://news.bbcimg.co.uk/nol/shared/img/bbc_news_120x60.gif</url>
            <title>BBC News - Home</title>
            <link>http://www.bbc.co.uk/news/</link>
        </image>
        <generator>RSS for Node</generator>
        <lastBuildDate>Wed, 18 Jan 2017 14:31:06 GMT</lastBuildDate>
        <copyright><![CDATA[Copyright: (C) British Broadcasting Corporation, see http://news.bbc.co.uk/2/hi/help/rss/4498287.stm for terms and conditions of reuse.]]></copyright>
        <language><![CDATA[en-gb]]></language>
        <ttl>15</ttl>
        <item>
            <title><![CDATA[Brexit: Boris Johnson warns against 'punishment beatings']]></title>
            <description><![CDATA[Boris Johnson tells the EU not to treat the UK's Brexit "escape" like a "World War Two movie".]]></description>
            <link>http://www.bbc.co.uk/news/uk-politics-38658998</link>
            <guid isPermaLink="true">http://www.bbc.co.uk/news/uk-politics-38658998</guid>
```

**Exemple d'HTML que cal generar**

```html
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
<meta charset="utf-8">
<title>Noticiari</title>
<style>
   .items { ... }
   .item { ha_de_flotar_a_l_esquerra_per_a_fer_efecte_responsiu }
   ...
</style>
</head>
<body>
    <h1>BBC News - Home</h1>
<div class="items">
 <div class="item">
  <div class="titol">
   <a href="http://www.bbc.co.uk/news/uk-politics-38658998">
    Mosul battle: Iraqi army prepares offensive on west of city
   </a>
  </div>
  <div class="descripcio">
   Boris Johnson tells the EU not to treat the UK's Brexit "escape" like a "World War Two movie".
  </div>
 </div>
 <div class="item">
    ...
 </div>
</div>


```


**Solució simplificada `t.xslt`**

```xml
<?xml version="1.0" encoding="UTF-8"?>
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform">

<xsl:template match="/">
  <html>
  <head>
  <meta charset="utf-8" />
  <title></title>
  </head>
  <body>
   <xsl:apply-templates />
  </body>
  </html>
</xsl:template>

<xsl:template match="channel">
  <h1><xsl:value-of select="title"/> </h1>
  <ul>
     <xsl:apply-templates select="item"/>
  </ul>
</xsl:template>

<xsl:template match="item">
  <li><xsl:value-of select="title"/></li>
</xsl:template>

</xsl:stylesheet>
```

**Exemple execució:**

```bash
dani@:~/$ wget -q -O rss.xml http://feeds.bbci.co.uk/news/rss.xml
dani@:~/$ xsltproc t.xslt rss.xml > f.html
```

**Resultat**

```html
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
<meta charset="utf-8">
<title></title>
</head>
<body>
    <h1>BBC News - Home</h1>
<ul>
<li>Mosul battle: Iraqi army prepares offensive on west of city</li>
<li>Brexit: Boris Johnson warns against 'punishment beatings'</li>
<li>CIA releases 13m pages of declassified documents online</li>
<li>Trump's views are '100% different' to Putin's, says Alexey Navalny</li>
<li>Italy weather: Quakes hit snowbound central regions</li>
<li>Obama administration gives $500m to UN climate change fund</li>
<li>Joe Biden tells Davos: Russia 'trying to collapse' liberal order</li>
<li>Babies remember their birth language - scientists</li>
<li>The Gambia's Yahya Jammeh's term extended by parliament</li>
<li>German fury at AfD Hoecke's Holocaust memorial remark</li>
<li>Chelsea Manning: Obama reduces sentence of Wikileaks source</li>
<li>Natalie Portman on playing Jackie Kennedy</li>
<li>Israeli policeman and Bedouin killed during clashes over demolitions</li>
<li>Sophie the Giraffe: How safe is it?</li>
<li>Moth with 'golden flake hairstyle' named after Donald Trump</li>
<li>Travelling from China to London</li>
<li>President Trump: What happens on inauguration day</li>
<li>On the banks of two majestic US rivers</li>
<li>The Gambia: British and Dutch tourists leave after new advice</li>
<li>Mexicans' Donald Trump fears</li>
<li>Who is Chelsea Manning?</li>
<li>Drone footage shows huge Antarctic ice crack</li>
<li>Syrian conflict: What's left of Aleppo's Great Mosque?</li>
<li>Japan's hi-tech toilets to get standardised symbols</li>
<li>Kim Kardashian will appear in the all-female Ocean's Eight</li>
<li>Jeremy Bowen: Returning home to ruins of East Aleppo</li>
<li>Gordon Corera: Why did the Zimmerman Telegram matter?</li>
<li>James Reynolds: Who was second-longest serving US president?</li>
<li>How often do planes fall on houses?</li>
<li>Is free trade good or bad?</li>
<li>Gambia political crisis: What happens next?</li>
<li>In pictures: Prize pigeons</li>
<li>Week in pictures: 7-13 January 2017</li>
<li>Africa's top shots: 7 - 13 January 2017</li>
<li>Keeping the slopes open</li>
<li>Australian Open 2017: Andy Murray through after Dan Evans stuns Marin Cilic</li>
<li>James Ellington &amp; Nigel Levine 'conscious and stable' after crash</li>
<li>Antonio Brown: Pittsburgh Steelers player faces punishment for live locker room video</li>
<li>Mud hut periods</li>
<li>East to West</li>
<li>Obama and Africa</li>
<li>The secret university</li>
<li>Shock of the nude</li>
<li>Golden idea</li>
<li>Awaiting the cut</li>
<li>'Nobody's people'</li>
<li>Enduring lessons</li>
<li>'Girly girls' in the workplace</li>
<li>Bridging the urban-rural divide</li>
<li>Bill Gates, Shakira and Brexit </li>
<li>Elites in retreat?</li>
</ul>
</body>
</html>
```

---

#FpInfor #Daw #Dam #Asix #AsixMp04 #DawMp04 #DamMp04 #DawMp04Uf02 #AsixMp04Uf02 #DamMp04Uf02

---

###### Autor: daniel herrera 2017.01.18 14:34:01
###### Editat per: daniel herrera 2017.01.25 13:43:51
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
