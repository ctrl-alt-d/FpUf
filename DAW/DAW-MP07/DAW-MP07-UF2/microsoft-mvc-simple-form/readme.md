# Microsoft MVC - Sumem dos números ( Simple Form )
## DAW-MP07-UF2 - Exercici de Generació dinàmica de pagines web.
Anem a crear un formulari senzill que sumi dos números amb MVC5:

1. Crea un controlador anomenat `CalculController`
2. Afegeix un mètode al controlador anomenat `Suma`.
3. Anota el mètode suma per tal que la seva ruta sigui `'suma'`.
4. El mètode suma rebrà dos paràmetres opcionals ( són els dos números que volem sumar )
5. Crea la vista suma i allà escriu el codi html i codi razor per tal de demanar els dos números.
6. La acció suma sumarà els dos números i el `Resultat` el posarà com string al ViewBag.
7. La vista de l'acció suma mostrarà el `ViewBag.Resultat`.
8. Divideix el mètode suma en dos mètodes amb identificador `suma` però signatures diferents. Anota per tal que el primer mètode s'executi quan la crida sigui `GET` i el segon mètode (amb els dos paràmetres) s'executi quan la crida sigui `POST`.

Codi més rellevant:

Els mètodes del controlador:

        [Route("suma"), HttpGet]
        public ActionResult Suma(  )
        {
            return View();
        }
 
        [Route("suma"), HttpPost]
        public ActionResult Suma(int numero1, int numero2)
        {
 
            ViewBag.Resultat = string.Format("El resultat de {0} + {1} = {2}", 
                                              numero1, numero2, numero1 + numero2);
            return View();
        }

La vista:

```html
@{
    ViewBag.Title = "Suma";
}
 
<div class="container">
```
 
    <h2>Suma</h2>
     
    @using (Html.BeginForm())
    {
       
        <fieldset>
            <legend>Números a sumar</legend>
            <div class="form-group">
                <div class="row">
                    <div class="col-xs-4">
                        @Html.Label("numero1", "numero 1")
                    </div>
                    <div class="col-xs-4">
                        @Html.TextBox("numero1", null, 
                                      htmlAttributes: new { @class = "form-control" })
                    </div>
                </div>
     
                <div class="row">
                    <div class="col-xs-4">
                        @Html.Label("numero2", "numero 2")
                    </div>
                    <div class="col-xs-4">
                        @Html.TextBox("numero2", null, 
                                       htmlAttributes: new { @class = "form-control" })
                    </div>
                </div>
     
                <div class="row">
                    <input type="submit" class="btn btn-primary" />
                </div>
     
                <div class="row">
                    <h2>@ViewBag.Resultat</h2>
                </div>
     
            </div>
        </fieldset>
       
    }
     
    </div>

Exercicis:

1. Implementa el projecte a la teva màquina.
2. Millora les rutes usant [Microsoft MVC AttributeRouting](/DAW/DAW-MP07/DAW-MP07-UF2/microsoft-mvc-attributerouting/readme.md)
3. Modifica per tal que la acció post faci un Post/Redirect/Get a una tercera acció on s'executi la suma i prepari el viewBag.

Ajuda:



        [Route("suma"), HttpPost]
        public ActionResult Suma(int numero1, int numero2)
        {

            return RedirectToAction("SumaResultat", "Calcul", 
                                    routeValues: new { numero1 = numero1, numero2 = numero2 });
        }

        [Route("suma/{numero1}/{numero2}"), HttpGet]
        public ActionResult SumaResultat(int numero1, int numero2)
        {
            ViewBag.Resultat = string.Format("El resultat de {0} + {1} = {2}", 
                                              numero1, numero2, numero1 + numero2);

            return View("Suma");
        }

---

#FpInfor #Daw #DawMp07 #DawMp07Uf02

---

###### Autor: daniel herrera 2014.12.05 15:13:22
###### Editat per: daniel herrera 2017.11.25 15:58:24
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
