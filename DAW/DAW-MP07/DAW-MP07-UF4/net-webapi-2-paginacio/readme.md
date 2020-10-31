# Net WebApi 2: paginació
## DAW-MP07-UF4 - Exercici de Serveis web. Pàgines dinàmiques interactives. Webs Híbrids.
Anem a treballar amb paginació.

**Per què necessitem paginació?** Si hem de consultar des de la part client una col·leció molt gran d'objectes no ens els pot enviar tots de cop perquè podriem enfonsar la xarxa o el dispositiu client. Llavors, en comptes d'enviar-los tots, n'enviem uns quants i donem l'opció al client a que ens en demani més.

Un exemple de client que pot gestionar dades de manera paginada és Angular. En l'artícle [AngularJS with Web API: server side paging](https://code.msdn.microsoft.com/AngularJS-with-Web-API-43e5de16) de Microsoft ens explica com desenvolupar la part servidora per servir dades paginades.

Crea una WebAPI senzilla que serveixi dades del tipus `Persona` ( nom i data de neixement ) de manera paginada.

Codi més rellevant de l'article:


```C#
public static class WebApiConfig 
{ 
    public static void Register(HttpConfiguration config) 
    {            
        // Use camelCase for JSON data. 
        config.Formatters.JsonFormatter.SerializerSettings.ContractResolver = new CamelCasePropertyNamesContractResolver(); 
```
 
        } 
    }



    // GET: api/Clubs/pageSize/pageNumber/orderBy(optional) 
    [Route("{pageSize:int}/{pageNumber:int}/{orderBy:alpha?}")] 
    public IHttpActionResult Get(int pageSize, int pageNumber, string orderBy = "") 
    { 
        var totalCount = this.clubRepository.Clubs.Count(); 
        var totalPages = Math.Ceiling((double)totalCount / pageSize); 
     
        var clubQuery = this.clubRepository.Clubs; 
     
        if (QueryHelper.PropertyExists<Club>(orderBy)) 
        { 
            var orderByExpression = QueryHelper.GetPropertyExpression<Club>(orderBy); 
            clubQuery = clubQuery.OrderBy(orderByExpression); 
        } else 
        { 
            clubQuery = clubQuery.OrderBy(c => c.Id); 
        } 
     
        var clubs = clubQuery.Skip((pageNumber - 1) * pageSize)                             
                                .Take(pageSize)                 
                                .ToList(); 
     
        var result = new 
        { 
            TotalCount = totalCount, 
            totalPages = totalPages, 
            Clubs = clubs 
        }; 
     
        return Ok(result); 
    }

---

#FpInfor #Daw #DawMp07 #DawMp07Uf04

---

###### Autor: daniel herrera 2018.02.08 14:24:36
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
