# Microsoft MVC AttributeRouting
## DAW-MP07-UF2 - Exercici de Generació dinàmica de pagines web.
El projecte [AttributeRouting](http://attributerouting.net/) inclós a MVC5 permet definir routes tot anotant els mètodes del controlador.

Reescriu l'exercici [Microsoft MVC Processant rutes](/DAW/DAW-MP07/DAW-MP07-UF2/microsoft-mvc-processant-rutes/readme.md) de manera que les rutes quedin anotades a les accions i no al fitxer de rutes.

Per tal de provar les rutes, el controlador i les accions, escriu de nou al navegador les urls que disparan aquestes accions.

Nota, el post [Attribute Routing in ASP.NET MVC 5](http://blogs.msdn.com/b/webdev/archive/2013/10/17/attribute-routing-in-asp-net-mvc-5.aspx) de *.NET Web Development and Tools Blog* et pot ajudar amb exemples de constraints:

```c++
// eg: /users/5
[Route("users/{id:int}")]
public ActionResult GetUserById(int id) { ... }
 
// eg: users/ken
[Route("users/{name})"]
public ActionResult GetUserByName(string name) { ... }
```

Recorda!! Amb MVC5 no cal importar cap paquet nou per treballar amb `AttributeRouting`, tantmateix has de posar `routes.MapMvcAttributeRoutes();` al fitxer de rutes:

    public class RouteConfig
    {
        public static void RegisterRoutes(RouteCollection routes)
        {
            routes.IgnoreRoute("{resource}.axd/{*pathInfo}");
     
            routes.MapMvcAttributeRoutes();
        }
    }

Més info a [Attribute Routing in ASP.NET MVC 5](http://blogs.msdn.com/b/webdev/archive/2013/10/17/attribute-routing-in-asp-net-mvc-5.aspx)

---

#FpInfor #Daw #DawMp07 #DawMp07Uf02

---

###### Autor: daniel herrera 2014.11.24 14:36:49
###### Editat per: daniel herrera 2014.12.02 15:46:31
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
