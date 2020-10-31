# EF: Primera presa de contacte amb l'ORM de Microsoft.
## DAW-MP07-UF3 - Exercici de Tècniques d’accés a dades.
Ens basarem en l'article [Entity Framework Code First to a New Database](https://msdn.microsoft.com/en-us/library/jj554735(v=vs.113).aspx).

1) Crea un projecte tipus consola. Importa l'entity framework des de la Package Console: `Install-Package EntityFramework`.

2) Crea una carpeta Models i escriu els tres models `Blog`, `Post` i `BloggingContext als seus respectius fitxers:

```java
public class Blog 
{ 
    public int BlogId { get; set; } 
    public string Name { get; set; } 
```
 
        public virtual List<Post> Posts { get; set; }  = new List<Post>();
    } 
 
    public class Post 
    { 
        public int PostId { get; set; } 
        public string Title { get; set; } 
        public string Content { get; set; } 
 
        public int BlogId { get; set; } 
        public virtual Blog Blog { get; set; } 
    } 
 
    public class BloggingContext : DbContext 
    { 
        public DbSet<Blog> Blogs { get; set; } 
        public DbSet<Post> Posts { get; set; } 
    } 

3) Modifica el fitxer de configuració per tal que desi els canvis en una base de dades SQL Server. Per exemple:


```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <configSections>
    <section name="entityFramework" type="System.Data..." />
  </configSections>
  <connectionStrings>
    <add name="BloggingContext" 
         connectionString="Data Source=MYNAMEISBOND\MYSQLEXPRESS; Initial Catalog=ElsMeusBlogs; Integrated Security=True; MultipleActiveResultSets=True;" providerName="System.Data.SqlClient" 
         />
  </connectionStrings>
```

4) Prepara les migracions i genera la base de dades, des del package manager:

    enable-migrations
    add-migration   Migracio_Inicial
    update-database --script   ( opcional: per mirar l'SQL)
    update-database            ( això crearà la base de dades )
    

5) Afegir el camp `Likes` al model `Post` i crear i executar migracions. Des del package manager:
    
    Add-Migration Afegir_Camp_Likes
    Update-database

Comprovar que el camp s'ha creat a la base de dades.

6) Modifica el main per tal de insertar algunes dades:

```java
        var ctx = new BlogContext();
        
        Blog elMeuBlogCocinitas = new Blog();
        elMeuBlogCocinitas.Name = "Cocinitas";
        ctx.Blogs.Add(elMeuBlogCocinitas);
```

            Post elMeuPostDeCuina = new Post();
            elMeuPostDeCuina.Title = "Patates amb M&M";
            elMeuPostDeCuina.Content = "Posar en una paella M&M i patates a foc lent";
            elMeuPostDeCuina.Blog = elMeuBlogCocinitas;
            ctx.Posts.Add(elMeuPostDeCuina);

            ctx.SaveChanges();

            Blog blogEsport = new Blog();
            blogEsport.Name = "Esport";
            ctx.Blogs.Add(blogEsport);

            Post postFlexions = new Post();
            postFlexions.Title = "Flexions";
            postFlexions.Content = "Fer deu flexions";
            postFlexions.Blog = blogEsport;
            ctx.Posts.Add(postFlexions);

            Post postAbdomininals = new Post();
            postAbdomininals.Title = "Flexions";
            postAbdomininals.Content = "Fer deu abdominals";
            blogEsport.Posts.Add( postAbdomininals );
            ctx.Posts.Add(postAbdomininals);
            ctx.SaveChanges();


7) Recorrer les dades insertades:

```java
        var totsElsBlogs = ctx.Blogs.Include( x=>x.Posts );
        foreach (Blog b in totsElsBlogs )
        {
            Console.WriteLine( "Blog: " + b.Name );
```

                foreach (Post p in b.Posts)
                {
                    Console.WriteLine("   Post: " + p.Title);
                }
            }

            Console.ReadKey();

**Solució**

En aquests videos podeu veure pas a pas com resoldre la pràctica:

* [Introducció EF6 Creant models 1/4 ](https://youtu.be/O60CeAUYYKg)
* [Introducció EF6 Modificant models (migració) 2/4](https://youtu.be/C2GeUipUE9I) 
* [Introducció EF6 Introduint dades 3/4](https://youtu.be/7qm88l5aC9o) Tanmateix aquest video ha quedat mal gravat, us recomano que us mireu aquest altre vídeo que també explica com entrar dades de dos models relacionats entre ells: [EF6 - CRUD - C  ( Vídeo 2/5 )](https://youtu.be/pGbfPzwqrDc)
* [Introducció EF6 Recorrer les dades 4/4](https://youtu.be/jdwynlzG5ao)

**Ampliació**

* A la llista de reproducció [Introducció a EF6](https://www.youtube.com/playlist?list=PLjvPXGQt4UbDpO1K9zoxn57EoCiIAcdIT) podeu aprendre, a més, com actualitzar dades, seleccionar-ne i esborrar-ne. En aquests videos la part del diseny dels models es fa amb una eina que Microsoft discontinua, per això he publicat aquests nous videos de l'exercici.

---

#FpInfor #Daw #DawMp07 #DawMp07Uf03

---

###### Autor: daniel herrera 2016.11.07 15:36:22
###### Editat per: daniel herrera 2017.11.09 14:22:51
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
