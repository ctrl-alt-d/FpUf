# Keen.io send events with Net Core without wrappers
## DAW-MP07-UF4 - Exercici de Serveis web. Pàgines dinàmiques interactives. Webs Híbrids.
Exemple de codi per enviar events:


```c#
using System;
using System.Net.Http;
using System.Text;
using System.Threading.Tasks;
using Keen.Core;
using Keen.Query;
using Newtonsoft.Json;


namespace keencore
{
    class Program
    {
        static void Main(string[] args)
        {
            new Program().fes().GetAwaiter().GetResult();
        }
        
        private async Task fes() {


            var projectSettings = new ProjectSettingsProvider("52b735e6d97b852f93000002", 
                                        writeKey: "65c3b79b302c0c296949e4fa9aeb78d61e59b81143003b9f22bd83e1388f369f9ed1053432038142e62b5ec8809935250797bd3cdbc34580cabdd3b50a67dc5858bb2e63f3890b6ed580c427d615628e5468f02d4fe93996b7264aa8c10a974e9902e396eee2cddc50e48e4d46a5ce4f",
                                        readKey: "f828592f9dc6c314439c5cac2559c019cb5f039e85f334804070faf33c1f8dd313034a1c71e74c7933056f4811793948088d12cef2dec4433f8a31511a7e80dbf90de41df47167d6ee9bee93dd4819d4e6598cd70c7da1f7370019bdcd53fbc4461a4235fdcf7a600449c987788e8738");
            var keenClient = new KeenClient(projectSettings);
            
            
            var compra = new
            {
                classe = "DAW",
                curs = 2,
                curs_academic = 2017
            };
            
                        
            //var resposta = keenClient.AddEventAsync("compres", compra);

            //resposta.Wait();
            
            //serialitzo
            string dades_serialitzades = JsonConvert.SerializeObject(compra, Formatting.Indented);
            
            //faig el post
            
            HttpClient client = new HttpClient();
            client.BaseAddress = new Uri("https://api.keen.io/3.0/projects/52b735e6d97b852f93000002/events/");
            client.DefaultRequestHeaders.Add("Authorization", "65c3b79b302c0c296949e4fa9aeb78d61e59b81143003b9f22bd83e1388f369f9ed1053432038142e62b5ec8809935250797bd3cdbc34580cabdd3b50a67dc5858bb2e63f3890b6ed580c427d615628e5468f02d4fe93996b7264aa8c10a974e9902e396eee2cddc50e48e4d46a5ce4f");
            client.DefaultRequestHeaders.Add("Accept", "application/json");
            //client.DefaultRequestHeaders.Add("Content-Type", "application/json");
            
            HttpRequestMessage request = new HttpRequestMessage(HttpMethod.Post, "compres");
            request.Content = new StringContent(dades_serialitzades,
                                                Encoding.UTF8, 
                                                "application/json");//CONTENT-TYPE header

  

            var x = await client.SendAsync(request);
            var s=x.Content.ReadAsStringAsync();
            Console.WriteLine("Response: {0}", s.Result );
            
            
        }
    }
}
```

---

#FpInfor #Daw #DawMp07 #DawMp07Uf04

---

###### Autor: daniel herrera 2018.01.30 16:33:33
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
