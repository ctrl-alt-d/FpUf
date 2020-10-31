# El Model Conceptual de Dades en Notació Crow's Foot
## DAW-MP02-UF1 - Exercici de Introducció a les bases de dades
Llegeix l'artícle de Jim Stewart [Crow's Feet Are Best](http://www.tdan.com/view-articles/7474). 

* De que parla aquest artícle?
* Enumera els arguments que l'autor esgrimeix per a defensar la Notació Crow's Foot. 
* Quines eines aparaixen al text que permeten fer diagrames conceptuals? Quines són més potents segons l'autor? Ves a la web del fabricant i comprova quan val una llicència de les eines esmentades per l'autor, sobre tot les més potents. Quines altres eines conèixes tu i que no apareguin en aquest text?
* Hi estàs d'acord amb l'autor? Expressa la teva opinió, exposa els teus arguments.

####Copio aqui sota els paràgrafs més importants:

*Crow's Feet Are Best*

Peter Chen invented data modeling with his innovative way of showing data structures in terms of entities and relationships. For the first time, complex data could be modeled so it was understandable to both business users and system designers. Before long, many data diagramming notations were invented and published. Of the many choices, the approach that conveys the richest set of information and is most easily understood by a non-technical audience is the crow’s foot notation. Clive Finkelstein developed this style in his work on information engineering. Having tried different notations in modeling sessions with business users, I have found that the crow’s foot style is the one that is most readily accepted and is understood with the least amount of training. My own experience has been validated with anecdotal evidence from many other data modelers.

**What is the Crow’s Foot Data Model?**

All data modeling approaches attempt to show three things – data entities (or classes, if you prefer), the relationships between them and their cardinality. Cardinality rules define the allowable counts of the relationships – one to many, many to many, etc. Most techniques show entities as boxes and relationships as connecting lines, which is intuitive and effective. But when it gets to cardinality, all manner of symbols – arrows, slashes, circles, numbers and text have been tried. It is here, in the depiction of cardinality, that the crow’s foot style is so much better than the others.

Cardinality specifies two business rules – the minimum number and maximum number of each entity that can participate in the relationship. Another name for minimum cardinality is “optionality.” It tells us if the relationship is mandatory or optional (i.e., “Can entity A exist without entity B?”). Maximum cardinality sets the upper bound on the relationship – “for each A, can there be only one B, or many B’s?” The crow’s foot symbol works so well because the cardinality constraints are diagrammed clearly and intuitively. The minimum cardinality is noted toward the center of the relationship line and the maximum cardinality goes toward the ends

**Automated Diagrammers**

If you are using automated diagramming software, you may or may not get a choice of which technique to use. The most frequently used product is probably Microsoft Visio. Its data diagramming templates include an entity relational format and an object relational format. Unfortunately, both styles use the same single-arrow symbol for relationships, which misses all the advantages of crow’s feet. If you want to use crow’s feet with Visio, you must give up the automatically maintained relationships and use simple connectors, which can show crow’s feet as the line end. More advanced design tools, such as Sybase Power Designer, get high marks for fully supporting crow’s feet, among other choices.

**Summary**

Of the different choices available for diagramming cardinality, the crow’s foot notation is clearly the most desirable. It shows both minimum and maximum cardinality in a visible graphic format. The multiplicity symbol is intuitive and easily understood by non-technical readers. It does not use expressions that have to be carefully parsed to interpret their meaning. It places the symbols directly on the relationship line so they remain visible and unambiguous in a complex diagram. The crow’s foot notation should be used in all conceptual data model diagrams that are to be reviewed by business users. It is also appropriate to use in physical database design models and object-oriented class models, although it is less accepted in those disciplines.

In the quarter-century since Mr. Chen showed us the way, we have seen a bunch of different ways of diagramming data. Although the crow’s foot style is popular, other techniques are still unfortunately in use. The modeling “wars” of the early methodologists should long be over. It is time to kill off the competitors, declare “Crow’s Feet Are Best!” and make it the standard! Now, if we can just get Microsoft to see the light...

---

#FpInfor #Daw #Dam #Asix #AsixMp02 #DawMp02 #DamMp02 #DawMp02Uf01 #AsixMp02Uf01 #DamMp02Uf01

---

###### Autor: daniel herrera 2013.09.07 09:40:10
###### Editat per: daniel herrera 2013.09.07 09:40:10
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
