# Transformació factura electrònica d'XML a HTML
## DAW-MP04-UF2 - Exercici de Àmbits d’aplicació de l’XML
Es tracta de transformar una factura en format eFact a HTML.

Cal usar un `if` per tractar diferent les persones jurídiques de les persones físiques. Et pots basar en aquest [exemple de Microsoft](https://msdn.microsoft.com/en-us/library/ms256206(v=vs.110).aspx):

```xml
<xsl:template match="stock">
   <p/>
   <xsl:if test="@international">International Stock </xsl:if>
   <xsl:apply-templates />
</xsl:template>
```

Procura que el format de factura HTML sigui com el que proposa [Textos de l'empresa de GenCat](http://www.gencat.cat/empresaiocupacio/departament/centre_documentacio/publicacions/empresa/mde/web/temari/comercials/17.htm)

Tanmateix, per simplificar l'exercici, usarem aquest altre format:

![Imgur](http://i.imgur.com/uqnhJvU.png)

---

#FpInfor #Daw #Dam #Asix #AsixMp04 #DawMp04 #DamMp04 #DawMp04Uf02 #AsixMp04Uf02 #DamMp04Uf02

---

###### Autor: daniel herrera 2017.01.25 13:45:55
###### Editat per: daniel herrera 2017.01.27 16:23:22
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
