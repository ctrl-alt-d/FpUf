# Resum xml i validacions DTD i XSD
## DAW-MP04-UF1 - Exercici de Programació amb XML
1) XML només amb node arrel.

```xml
<?xml version="1.0" encoding="utf-8"?>
<arrel>
   una mica de dades
</arrel>
```

2) XML amb elements dins el node arrel.

```xml
<?xml version="1.0" encoding="utf-8"?>
<persona>
   <nom>Pere</nom>
   <cognom>Calder</cognom>
</persona>
```

3) XML amb atributs.

```xml
<?xml version="1.0" encoding="utf-8"?>
<persona tipus="física">
   <nom>Pere</nom>
   <cognom>Calder</cognom>
</persona>
```

4) DTD d'un xml amb només node arrel.

Versió dtd està fora de l'xml:

```xml
<?xml version="1.0" encoding="utf-8"?>
<!DOCTYPE arrel SYSTEM "elMeu.dtd">
<arrel>
   una mica de dades
</arrel>
```

El seu DTD:

```xml
<?xml version="1.0" encoding="utf-8"?>
<!ELEMENT arrel (#PCDATA)>
```

Versió dtd està dins de l'xml:

```xml
<?xml version="1.0" encoding="utf-8"?>
<!DOCTYPE arrel [
  <!ELEMENT arrel (#PCDATA)>
]>
<arrel>
   una mica de dades
</arrel>
```

4) XSD d'un xml amb només node arrel.

```xml
<?xml version="1.0" encoding="utf-8"?>
<arrel xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="elMeu.xsd">
   una mica de dades
</arrel>
```

El seu esquema:

```xml
<?xml version="1.0" encoding="utf-8"?>
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema">
<xsd:element name="arrel" type="xsd:string"/>
</xsd:schema>
```

5) DTD d'un xml amb només elements dins el node arrel.

```xml
<?xml version="1.0" encoding="utf-8"?>
<!DOCTYPE persona SYSTEM "elMeu.dtd">
<persona>
   <nom>Pere</nom>
   <cognom>Calder</cognom>
</persona>
```

El seu dtd

```xml
<?xml version="1.0" encoding="utf-8"?>
<!ELEMENT persona (nom, cognom)>
<!ELEMENT nom (#PCDATA)>
<!ELEMENT cognom (#PCDATA)>
```

6) XSD d'un xml amb només elements dins el node arrel.

```xml
<?xml version="1.0" encoding="utf-8"?>
<persona  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="elMeu.xsd">
   <nom>Pere</nom>
   <cognom>Calder</cognom>
</persona>
```

Versió 1:

```xml
<?xml version="1.0" encoding="utf-8"?>
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema">
<xsd:element name="persona">
   <xsd:complexType>
     <xsd:sequence>
       <xsd:element name="nom" type="xsd:string" />
       <xsd:element name="cognom" type="xsd:string" />
     </xsd:sequence>
   </xsd:complexType>
</xsd:element>
</xsd:schema>
```

Versió 2:

```xml
<?xml version="1.0" encoding="utf-8"?>
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema">
<xsd:element name="persona" type="personaTipus" />
```

    <!-- tipus persona -->
    <xsd:complexType name="personaTipus">
      <xsd:sequence>
        <xsd:element name="nom" type="xsd:string" />
        <xsd:element name="cognom" type="xsd:string" />
      </xsd:sequence>
    </xsd:complexType>

    </xsd:schema>

7) DTD d'un xml amb element que es repeteix varies vegades dins un altre element.

```xml
<?xml version="1.0" encoding="utf-8"?>
<!DOCTYPE persones SYSTEM "elMeu.dtd">
<persones>
    <persona>
       <nom>Pere</nom>
       <cognom>Calder</cognom>
    </persona>
    <persona>
       <nom>Marta</nom>
       <cognom>Ayats</cognom>
    </persona>
</persones>
```

El dtd:

```xml
<?xml version="1.0" encoding="utf-8"?>
<!ELEMENT persones (persona+)>
<!ELEMENT persona (nom, cognom)>
<!ELEMENT nom (#PCDATA)>
<!ELEMENT cognom (#PCDATA)>
```

8) XSD d'un xml amb element que es repeteix varies vegades dins un altre element.

```xml
<?xml version="1.0" encoding="utf-8"?>
<persones xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="elMeu.xsd" >
    <persona>
       <nom>Pere</nom>
       <cognom>Calder</cognom>
    </persona>
    <persona>
       <nom>Marta</nom>
       <cognom>Ayats</cognom>
    </persona>
</persones>
```

    <?xml version="1.0" encoding="utf-8"?>
    <xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema">
    <xsd:element name="persones" type="personesTipus" />

    <!-- tipus persones -->
    <xsd:complexType name="personesTipus">
        <xsd:sequence>
           <xsd:element name="persona"
                        type="personaTipus"
                        maxOccurs="unbounded"/>
        </xsd:sequence>
    </xsd:complexType>

    <!-- tipus persona -->
    <xsd:complexType name="personaTipus">
      <xsd:sequence>
        <xsd:element name="nom" type="xsd:string" />
        <xsd:element name="cognom" type="xsd:string" />
      </xsd:sequence>
    </xsd:complexType>

    </xsd:schema>

9) DTD d'un xml que conté elements opcionals.

```xml
<?xml version="1.0" encoding="utf-8"?>
<!DOCTYPE persones SYSTEM "elMeu.dtd">
<persones>
    <persona>
       <nom>Pere</nom>
       <cognom>Calder</cognom>
       <data-neixement>2000-01-01</data-neixement>
    </persona>
    <persona>
       <nom>Marta</nom>
       <cognom>Ayats</cognom>
    </persona>
</persones>
```

El dtd:

```xml
<?xml version="1.0" encoding="utf-8"?>
<!ELEMENT persones (persona+)>
<!ELEMENT persona (nom, cognom, data-neixement?)>
<!ELEMENT nom (#PCDATA)>
<!ELEMENT cognom (#PCDATA)>
<!ELEMENT data-neixement (#PCDATA)>
```


10) XML que conté elements opcionals.

```xml
<?xml version="1.0" encoding="utf-8"?>
<persones xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="elMeu.xsd" >
    <persona>
       <nom>Pere</nom>
       <cognom>Calder</cognom>
       <data-neixement>2000-01-01</data-neixement>
    </persona>
    <persona>
       <nom>Marta</nom>
       <cognom>Ayats</cognom>
    </persona>
</persones>
```

L'esquema:

```xml
<?xml version="1.0" encoding="utf-8"?>
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema">
<xsd:element name="persones" type="personesTipus" />
```

    <!-- tipus persones -->
    <xsd:complexType name="personesTipus">
        <xsd:sequence>
           <xsd:element name="persona"
                        type="personaTipus"
                        maxOccurs="unbounded"/>
        </xsd:sequence>
    </xsd:complexType>

    <!-- tipus persona -->
    <xsd:complexType name="personaTipus">
      <xsd:sequence>
        <xsd:element name="nom" type="xsd:string" />
        <xsd:element name="cognom" type="xsd:string" />
        <xsd:element name="data-neixement"
                     type="xsd:date"
                     minOccurs="0" />
      </xsd:sequence>
    </xsd:complexType>

    </xsd:schema>


11) DTD d'un xml amb atributs.

```xml
<?xml version="1.0" encoding="utf-8"?>
<!DOCTYPE persona SYSTEM "elMeu.dtd">
<persona tipus="física">
   <nom>Pere</nom>
   <cognom>Calder</cognom>
   <cognom ordre="segon">Calder</cognom>
</persona>
```

El DTD:

```xml
<?xml version="1.0" encoding="utf-8"?>
<!ELEMENT persona (nom, cognom+)>
<!ATTLIST persona tipus CDATA #REQUIRED>
<!ELEMENT nom (#PCDATA)>
<!ELEMENT cognom (#PCDATA)>
<!ATTLIST cognom ordre CDATA #IMPLIED>
```

12) XSD d'un xml amb atributs de tipus enumerat.

```xml
<?xml version="1.0" encoding="utf-8"?>
<persona
  tipus="física"
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="elMeu.xsd"
  >
   <nom>Pere</nom>
   <cognom>Calder</cognom>
   <cognom ordre="2">Calder</cognom>
</persona>
```

L'esquema:

```xml
<?xml version="1.0" encoding="utf-8"?>
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema">
<xsd:element name="persona" type="personaTipus" />
```

    <!-- tipus persona -->
    <xsd:complexType name="personaTipus">
      <xsd:sequence>
        <xsd:element name="nom" type="xsd:string" />
        <xsd:element name="cognom"
                     type="cognomTipus"
                     maxOccurs="2"
                     minOccurs="1"/>
      </xsd:sequence>
      <xsd:attribute name="tipus" type="xsd:string" />
    </xsd:complexType>

    <!-- tipus cognom -->
    <xsd:complexType name="cognomTipus">
        <xsd:simpleContent>
            <xsd:extension base="xsd:string">
              <xsd:attribute name="ordre" type="xsd:integer" />
            </xsd:extension>
        </xsd:simpleContent>
    </xsd:complexType>

    </xsd:schema>


13) DTD d'un xml amb un element que pot variar el seu contingut.

```xml
<?xml version="1.0" encoding="utf-8"?>
<!DOCTYPE persones SYSTEM "elMeu.dtd">
<persones>
    <persona>
       <nom>Pere</nom>
       <cognom>Calder</cognom>
    </persona>
    <persona>
       <nom-comercial>Marta</nom>
    </persona>
</persones>
```
El dtd:

```xml
<?xml version="1.0" encoding="utf-8"?>
<!ELEMENT persones (persona+)>
<!ELEMENT persona ( (nom, cognom) | nom-comercial )>
<!ELEMENT nom (#PCDATA)>
<!ELEMENT cognom (#PCDATA)>
```


14) DTD i XSD d'un xml amb un element que pot variar el seu contingut.


```xml
<?xml version="1.0" encoding="utf-8"?>
<persones xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="elMeu.xsd" >
    <persona>
       <nom>Pere</nom>
       <cognom>Calder</cognom>
    </persona>
    <persona>
       <nom-comercial>Marta</nom>
    </persona>
</persones>
```

L'esquema:

```xml
<?xml version="1.0" encoding="utf-8"?>
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema">
<xsd:element name="persones" type="personesTipus" />
```

    <!-- tipus persones -->
    <xsd:complexType name="personesTipus">
        <xsd:sequence>
           <xsd:element name="persona"
                        type="personaTipus"
                        maxOccurs="unbounded"/>
        </xsd:sequence>
    </xsd:complexType>

    <!-- tipus persona -->
    <xsd:complexType name="personaTipus">
       <xsd:choice>
          <xsd:sequence>
            <xsd:element name="nom" type="xsd:string" />
            <xsd:element name="cognom" type="xsd:string" />
          </xsd:sequence>
          <xsd:sequence>
            <xsd:element name="nom-comercial" type="xsd:string" />
          </xsd:sequence>
       </xsd:choice>
    </xsd:complexType>

    </xsd:schema>

---

#FpInfor #Daw #Dam #Asix #AsixMp04 #DawMp04 #DamMp04 #DawMp04Uf01 #AsixMp04Uf01 #DamMp04Uf01

---

###### Autor: daniel herrera 2016.11.09 15:28:55
###### Editat per: daniel herrera 2016.11.09 15:45:12
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
