# WebAPI: Custom result on validation error
## DAW-MP07-UF4 - Exercici de Serveis web. Pàgines dinàmiques interactives. Webs Híbrids.
En l'article [Handling validation responses for ASP.NET Core Web API](https://www.jerriepelser.com/blog/validation-response-aspnet-core-webapi/) ens explica com generar resultats 'customitzats' quan es produeixen errors als models.

Canvis que cal fer a l'aplicació. Ho fem per parts: 

1) Crear un `ActionFilterAttribute` i anotar el teu controlador:

```C#
/// creant el ActionFilterAttribute
public class ValidateModelAttribute : ActionFilterAttribute
{
    public override void OnActionExecuting(ActionExecutingContext context)
    {
        if (!context.ModelState.IsValid)
        {
            context.Result = new BadRequestObjectResult(context.ModelState);
        }
    }
}

//Anotant el controlador:
[Authorize]
[Route("api/properties")]
[ValidateModel]
public class PropertiesController : Controller
{
    // code omitted for brevity
}
```

provem i veiem que apareixen els errors igual que abans, ara cal modificar una mica el codi, ho fem a continuació.

2) Ara cal 'customitzar' l'error, modifiquem el `ActionFilterAttribute`:

```C#
public class ValidationError
{
    [JsonProperty(NullValueHandling=NullValueHandling.Ignore)]
    public string Field { get; }

    public string Message { get; }

    public ValidationError(string field, string message)
    {
        Field = field != string.Empty ? field : null;
        Message = message;
    }
}

```
 
    //ActionFilterAttribute
    public class ValidacioModelAttribute: ActionFilterAttribute
        {
            public override void OnActionExecuting(ActionExecutingContext context)
            {
                if (!context.ModelState.IsValid)
                {
                    var _error = new
                    {
                        Message = "Validation Failed",
                    Errors = context.ModelState.Keys
                            .SelectMany(key => context.ModelState[key].Errors.Select(x => new ValidationError(key, x.Exception.Message)))
                            .ToList()
                };
                    context.Result = new JsonResult(_error); //BadRequestObjectResult(context.ModelState);
                }
            }
        }

---

#FpInfor #Daw #DawMp07 #DawMp07Uf04

---

###### Autor: daniel herrera 2018.02.08 15:24:21
###### Editat per: daniel herrera 2018.02.08 15:24:21
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
