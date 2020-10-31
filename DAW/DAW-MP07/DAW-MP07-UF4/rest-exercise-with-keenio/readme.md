# REST exercise with Keen.io
## DAW-MP07-UF4 - Exercici de Serveis web. Pàgines dinàmiques interactives. Webs Híbrids.
In a help desk application scenario we want to be able to get in real time statistics about help desk issues status.

1) Modify [the help desk exercise](/DAW/DAW-MP07/DAW-MP07-UF2/mvc-microsoft-fluent-api/readme.md) to include in controler an event POST to keen.io with fields: `technician Id`, `technician name`, `issue description`. You should write raw code to make the post as [C# - Calling an API](/DAW/DAW-MP07/DAW-MP07-UF4/c-cridant-una-api/readme.md).

2) Make a new *controler action* named `statistics`. This action should fill a *ModelView* with keen.io aggregated data: **total issues by technician name**. Learn how to get aggregates at [Data Analysis APIs - Group By](https://keen.io/docs/data-analysis/group-by/)

3) Include in view a [pie chart visualization](https://github.com/keen/keen-js/blob/master/docs/visualization.md#pie-chart) of total issues by `technician name`.

**Requirements:**

* Exercise [C# - Calling API](/DAW/DAW-MP07/DAW-MP07-UF4/c-cridant-una-api/readme.md) completed.
* Points 1 and 2 should be coded on C# with out keen.io .NET SDK, no fear!

---

#FpInfor #Daw #DawMp07 #DawMp07Uf04

---

###### Autor: daniel herrera 2015.02.24 15:48:08
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
