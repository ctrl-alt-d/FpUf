# Treballant amb Vistes: Layout
## DAW-MP07-UF2 - Exercici de Generació dinàmica de pagines web.
Llegeix amb atenció la secció [Layout](https://docs.microsoft.com/en-us/aspnet/core/mvc/views/layout) dels tutorials ASP.NET Core MVC i contesta aquestes preguntes:

1.- Mitjançant Layouts podem reduir codi duplicat a les vistes?

2.- Localitza al teu projecte el layout per defecte. *"By convention, the default layout for an ASP.NET app is named _Layout.cshtml. The Visual Studio ASP.NET Core MVC project template includes this layout file in the Views/Shared folder"*

3.- Quin funció creus que realitza `@RenderBody()` dins el layout? i `@RenderSection("scripts", required: false)` ?

4.- Per què posem la propietat `Layout` a les pàgines Razor?

    @{
        Layout = "_Layout";
    }

5.- On posem aquest tall de codi, al layout o a la vista?

    @section Scripts {
         <script type="text/javascript" src="/scripts/main.js"></script>
       }

6.- Quina és la funció de `_ViewStart.cshtml` i quan s'executa i quan no s'executa? 

7.- Si `_ViewStart.cshtml`  conté aquet codi:

    @{
        Layout = "_Layout";
    }
    
cal que les vistes també el continguin? Per què?

---

#FpInfor #Daw #DawMp07 #DawMp07Uf02

---

###### Autor: daniel herrera 2017.12.31 12:56:10
###### Editat per: daniel herrera 2017.12.31 13:03:23
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
