# C# - Cridant una API
## DAW-MP07-UF4 - Exercici de Serveis web. Pàgines dinàmiques interactives. Webs Híbrids.
Realitza el [getting started de keen.io](https://keen.io/docs/getting-started-guide/).

Ara envia l'event fent un post des del teu llenguatge de programació. Exemple des de .NET:

```c++
using Newtonsoft.Json.Linq;
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
using System.Net.Http;
using System.Text;
using System.Threading.Tasks;

namespace ConsoleApplication3
{
    class Program
    {

        static async Task RunAsync()
        {

            var aPurchase = new
                {
                    category = "magical animals",
                    username = "hagrid",
                    price = 7.13,
                    payment_type = "information",
                    animal_type = "norwegian ridgeback dragon"
                };

            var jEvent = JObject.FromObject(aPurchase);
            var content = jEvent.ToString();

            using (var client = new HttpClient())
            using (var contentStream = new StreamContent(new MemoryStream(Encoding.UTF8.GetBytes(content))))
            {
                contentStream.Headers.Add("content-type", "application/json");

                string url = string.Format("https://api.keen.io/3.0/projects/{0}/events/{1}?api_key={2}", "XX", "XX","XX");
                
                var httpResponse = await client.PostAsync(url, contentStream)
                    .ConfigureAwait(continueOnCapturedContext: false);
                var responseString = await httpResponse.Content.ReadAsStringAsync()
                    .ConfigureAwait(continueOnCapturedContext: false);
                JObject jsonResponse = null;
                jsonResponse = JObject.Parse(responseString);

                if (!httpResponse.IsSuccessStatusCode)
                    throw new Exception("AddEvent failed with status: " + httpResponse);

                Console.WriteLine(jsonResponse.ToString() );
            }
        }

        static void Main(string[] args)
        {
            RunAsync().Wait();

        }
    }
}

```


**Exercici**:

 * Explica per que cal fer `install-package  Newtonsoft.Json` o `install-package Microsoft.Net.Http` per poder compilar el projecte.
 * Enten i comenta línia a línia el codi .NETde l'exemple que crida la API [keen.io](https://keen.io/).
 
**En aquest exercici hem aprés:**

1 | 2 | 3
---|---|---
Crear estructura anònima C# |  Serialitzar a json |  Enviar json 




---

#FpInfor #Daw #DawMp07 #DawMp07Uf04

---

###### Autor: daniel herrera 2015.02.23 13:26:53
###### Editat per: daniel herrera 2015.02.23 13:26:48
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
