# XPath. Testing Microsoft Examples
## DAW-MP04-UF2 - Exercici de Àmbits d’aplicació de l’XML
Quoting [XPath Syntax](https://msdn.microsoft.com/en-us/library/ms256471(v=vs.110).aspx):

>An XML Path Language (Xpath) expression uses a path notation, like those used in URLs, for addressing parts of an XML document. The expression is evaluated to yield an object of the node-set, Boolean, number, or string type. For example, the expression `book/author` will return a node-set of the `<author>` elements contained in the `<book>` elements, if such elements are declared in the source XML document. In addition, an XPath expression can have predicates (filter expressions) or function calls. For example, the expression `book[@type="Fiction"]` refers to the `<book>` elements whose type attribute is set to "Fiction".

1) Go to [XPath Tester / Evaluator](http://www.freeformatter.com/xpath-tester.html) and familiarize yourself with all samples:

```xml
<root xmlns:foo="http://www.foo.org/" xmlns:bar="http://www.bar.org">
	<actors>
		<actor id="1">Christian Bale</actor>
		<actor id="2">Liam Neeson</actor>
		<actor id="3">Michael Caine</actor>
	</actors>
	<foo:singers>
		<foo:singer id="4">Tom Waits</foo:singer>
		<foo:singer id="5">B.B. King</foo:singer>
		<foo:singer id="6">Ray Charles</foo:singer>
	</foo:singers>
</root>
```

1.- Select the document node

```bash
/
```

2.- Select the 'root' element

```bash
/root
```

3.- Select all 'actor' elements that are direct children of the 'actors' element.

```bash
/root/actors/actor
```

4.- Select all 'singer' elements regardless of their positions in the document.

```bash
//foo:singer
```

5.- Select the 'id' attributes of the 'singer' elements regardless of their positions in the document.

```bash
//foo:singer/@id
```

6.- Select the textual value of first 'actor' element.

```bash
//actor[1]/text()
```

7.- Select the last 'actor' element.

```bash
//actor[last()]
```

8.- Select the first and second 'actor' elements using their position.

```bash
//actor[position() < 3]
```

9.- Select all 'actor' elements that have an 'id' attribute.

```bash
//actor[@id]
```

10.- Select the 'actor' element with the 'id' attribute value of '3'.

```bash
//actor[@id='3']
```

11.- Select all 'actor' nodes with the 'id' attribute value lower or equal to '3'.

```bash
//actor[@id<=3]
```

12.- Select all the children of the 'singers' node.

```bash
/root/foo:singers/*
```

13.- Select all the elements in the document.

```bash
//*
```

14.- Select all the 'actor' elements AND the 'singer' elements.

```bash
//actor|//foo:singer
```

15.- Select the name of the first element in the document.

```bash
name(//*[1])
```

16.- Select the numeric value of the 'id' attribute of the first 'actor' element.

```bash
number(//actor[1]/@id)
```

17.- Select the string representation value of the 'id' attribute of the first 'actor' element.

```bash
string(//actor[1]/@id)
```

18.- Select the length of the first 'actor' element's textual value.

```bash
string-length(//actor[1]/text())
```

19.- Select the local name of the first 'singer' element, i.e. without the namespace.

```bash
local-name(//foo:singer[1])
```

20.- Select the number of 'singer' elements.

```bash
count(//foo:singer)
```

21.- Select the sum of the 'id' attributes of the 'singer' elements.

```bash
sum(//foo:singer/@id)
```



2) Go to [XPath Examples](https://msdn.microsoft.com/en-us/library/ms256086(v=vs.110).aspx), download [ Sample XML File for XPath Syntax (inventory.xml)](https://msdn.microsoft.com/en-us/library/ms256095(v=vs.110).aspx) and test and document all samples. You should create the right context for some samples.

---

#FpInfor #Daw #Dam #Asix #AsixMp04 #DawMp04 #DamMp04 #DawMp04Uf02 #AsixMp04Uf02 #DamMp04Uf02

---

###### Autor: daniel herrera 2016.12.14 10:57:50
###### Editat per: daniel herrera 2016.12.14 11:14:07
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
