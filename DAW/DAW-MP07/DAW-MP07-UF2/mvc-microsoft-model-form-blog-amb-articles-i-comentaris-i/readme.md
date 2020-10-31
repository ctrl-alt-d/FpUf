# MVC Microsoft - Blog amb artícles i comentaris  ( Model Form )
## DAW-MP07-UF2 - Exercici de Generació dinàmica de pagines web.
Segueix les instruccions i entrega el que es demana:

* Crea una aplicació MVC5 amb VS.
* Crea tipus autenticació *sense autenticació*
* Afegeix aquests dos models i crea un context en un fitxer a banda. Degut a que no has afegit models d'autenticació et caldrà instal·lar l'EntityFramework des del *Package Manager Console*. Tindràs tres nous fitxers `Article.cs`, `Comentari.cs` i `Context.cs`.

*Fitxers:*

```c#
//dins article.cs ...
public class Article
{
    public int ID { set; get; }
```

        [MaxLength(120)]
        public string titol;

        [MaxLength(8000)]
        [DataType(DataType.MultilineText)]
        public string cos { set; get; }

        [MaxLength(30)]
        public string autor { set; get; }

        public DateTime momentPublicacio { set; get; }

    }

    //dins comentari.cs ...
    public class Comentari
    {
        public int ID { get; set; }

        [MaxLength(300)]
        public string comentari { get; set; }

        public virtual Article article { get; set; }

    }

* Crea les migracions i aplicales a una base de dades d'SQL Server. No oblidis tocar el fitxet web.config amb el connection string:

Exemple:

```xml
<configuration>
  <configSections>
    <!-- For more information on Entity Framework configuration, visit http://go.microsoft.com/fwlink/?LinkID=237468 -->
    <section name="entityFramework" type="System.Data.Entity.Internal.ConfigFile.EntityFrameworkSection, EntityFramework, Version=6.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" requirePermission="false" />
</configSections>
<connectionStrings>
  <add name="blogDbContext" connectionString="Data Source=MYNAMEISBOND\mysqlexpress;Initial Catalog=p;Integrated Security=True" providerName="System.Data.SqlClient" />
</connectionStrings>
```

* Crea *controladors amb vistes, usant EntityFramework* tant per a `Article` com per a `Comentari`.

* Fes que la plantilla per defecte tingui entrada de menú per a manegar els Artícles.

**Entregables**

1. Fes captura de pantalla del *Solution Explorer* on es vegin tots els fitxers creats.
2. Fes captura del programa en funcionament un cop hagis entrat tres artícles.
3. Fixat que l'acció delete rep el paràmetre via ruta: `public ActionResult Delete(int? id)`, en canvi, l'acció que realment esborra rep el paràmetre via post: `public ActionResult DeleteConfirmed(int id)`. Explica per què aquest és un patró de bones pràctiques a la programació web.
4. Identifica el mètode que realment actualitza les dades. Quins resultats pot generar aquest mètode? ( ho estudiarem més endavant )
5. Quins camps permet editar la vista del `Comentari`?

---

#FpInfor #Daw #DawMp07 #DawMp07Uf02

---

###### Autor: daniel herrera 2014.12.14 17:38:43
###### Editat per: daniel herrera 2017.11.25 16:06:06
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
