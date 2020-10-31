# .NET fent servir una WebAPI des d'una aplicació escriptori
## DAW-MP07-UF4 - Exercici de Serveis web. Pàgines dinàmiques interactives. Webs Híbrids.
Hem fet una aplicació escriptori on hem posat una `DataGrid` on carreguem les dades que ens envia la WebApi, després hem fet un update de les dades fent un `PUT` a la WebApi. Aquest és el codi sense fer refactoring:


    
```C#
    public partial class MainWindow : Window
    {
        private List<Persona> Persones = null;
        public MainWindow()
        {
            InitializeComponent();
        }

        private void CarregaPersones_Click(object sender, RoutedEventArgs e)
        {

            HttpClient client = new HttpClient();
            client.BaseAddress = new Uri("http://localhost:58940/");
            client.DefaultRequestHeaders.Add("Authorization", "_clau_super_xunga_");
            client.DefaultRequestHeaders.Add("Accept", "application/json");

            HttpRequestMessage request = new HttpRequestMessage(HttpMethod.Get, "api/APIPersones");

            var x = client.SendAsync(request).GetAwaiter().GetResult();
            string json_txt =  x.Content.ReadAsStringAsync().GetAwaiter().GetResult(); ;

            Persones = JsonConvert.DeserializeObject<List<Persona>>(json_txt);

            Resultat.Text = "";
            foreach ( Persona p in Persones)
                Resultat.Text += p.ToString() + Environment.NewLine;

            DataGridPersones.ItemsSource = Persones;
            DataGridPersones.CellEditEnding += myDG_CellEditEnding;


        }

        void myDG_CellEditEnding(object sender, DataGridCellEditEndingEventArgs e)
        {
            if (e.EditAction == DataGridEditAction.Commit && e.Column != null)
            {
                var column = e.Column as DataGridBoundColumn;
                var bindingPath = (column.Binding as Binding).Path.Path;
                if (bindingPath != "IdPersona")
                {
                    //preparo les dades que han canviat
                    int rowIndex = e.Row.GetIndex();
                    var el = e.EditingElement as TextBox;

                    Persona persona_a_editar = (Persona)e.Row.Item;
                    if (bindingPath == "Nom")
                        persona_a_editar.Nom = el.Text;
                    else if (bindingPath == "DataNeixement")
                        persona_a_editar.DataNeixement = DateTime.Parse( el.Text );

                    //serialitzo les dades
                    var dades_serialitzades = JsonConvert.SerializeObject(persona_a_editar, Formatting.Indented);

                    //faig un PUT amb les dades serialitzades
                    HttpClient client = new HttpClient();
                    client.BaseAddress = new Uri("http://localhost:58940/");
                    client.DefaultRequestHeaders.Add("Authorization", "_clau_super_xunga_");
                    client.DefaultRequestHeaders.Add("Accept", "application/json");

                    HttpRequestMessage request = new HttpRequestMessage(HttpMethod.Put, 
                                        $"api/APIPersones/{persona_a_editar.IdPersona}");

                    request.Content = new StringContent(dades_serialitzades,
                                            Encoding.UTF8,
                                            "application/json");//CONTENT-TYPE header

                    var x = client.SendAsync(request).GetAwaiter().GetResult();

                    //obting el resultat
                    string resultat_post= x.Content.ReadAsStringAsync().GetAwaiter().GetResult(); ;

                }
                
            }
        }

    }
```

---

#FpInfor #Daw #DawMp07 #DawMp07Uf04

---

###### Autor: daniel herrera 2018.02.06 16:06:25
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
