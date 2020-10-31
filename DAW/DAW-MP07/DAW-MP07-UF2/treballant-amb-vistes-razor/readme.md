# Treballant amb Vistes: Razor
## DAW-MP07-UF2 - Exercici de Generació dinàmica de pagines web.
Llegeix amb atenció [Razor syntax for ASP.NET Core](https://docs.microsoft.com/en-us/aspnet/core/mvc/views/razor) i contesta a les següents preguntes:

1.- Com es renderitza aquest codi Razor?

```html
<p>@@Username</p>
<p>@Username</p>
<a href="mailto:Support@contoso.com">Support@contoso.com</a>
<p>@DateTime.Now</p>
<p>@DateTime.IsLeapYear(2016)</p>
<p>@GenericMethod<int>()</p>
<p>@(GenericMethod<int>())</p>
<p>Last week this time: @(DateTime.Now - TimeSpan.FromDays(7))</p>
<p>Last week: @DateTime.Now - TimeSpan.FromDays(7)</p>
@("<span>Hello World</span>")
```

2.- Per què fan servir parèntesi en aquesta expressió?

```html
@{
    var joe = new Person("Joe", 33);
}    
<p>Age@(joe.Age)</p>
```

3.- Per què és perillòs fer servir el mètode Raw de l'HTML helper?

```html
@Html.Raw("<span>Hello World</span>")
```

4.- Aquí veiem codi html i c# barrejat, com pot ser?

```html
@{
    var inCSharp = true;
    <p>Now in HTML, was in C# @inCSharp</p>
}
```

5.- Per a que serveix el tag `<text>`?

```java
@for (var i = 0; i < people.Length; i++)
{
    var person = people[i];
    <text>Name: @person.Name</text>
}
```

6.- Per a que serveix `@:` ?

```bash
@for (var i = 0; i < people.Length; i++)
{
    var person = people[i];
    @:Name: @person.Name
}
```

7.- Cal el símbol @ davant de l'`else`?

```java
@if (value % 2 == 0)
{
    <p>The value was even.</p>
}
else if (value >= 1337)
{
    <p>The value is large.</p>
}
else
{
    <p>The value is odd and small.</p>
}
```

8.- Donat el següent codi Razor:

```bash
@{
    var people = new Person[]
    {
          new Person("Weston", 33),
          new Person("Johnathon", 41),
          ...
    };
}

```
Quin bucle t'agrada més i per què?

```bash
<!-- bucle for -->
@for (var i = 0; i < people.Length; i++)
{
    var person = people[i];
    <p>Name: @person.Name</p>
    <p>Age: @person.Age</p>
}

@{
    /* bucle foreach */
}
@foreach (var person in people)
{
    <p>Name: @person.Name</p>
    <p>Age: @person.Age</p>
}
```

    @{
        /* bucle while */
    }    
    @{ var i = 0; }
    @while (i < people.Length)
    {
        var person = people[i];
        <p>Name: @person.Name</p>
        <p>Age: @person.Age</p>
    
        i++;
    }
    
    @*
       bucle do while
    *@
    @{ var i = 0; }
    @do
    {
        var person = people[i];
        <p>Name: @person.Name</p>
        <p>Age: @person.Age</p>
    
        i++;
    } while (i < people.Length);

9.- Per que fa un `@using System.IO`?

    @using System.IO
    @{
        var dir = Directory.GetCurrentDirectory();
    }
    <p>@dir</p>

10.- *"The @model directive specifies the type of the model passed to a view:"*. És obligatòria aquesta directiva? En quina d'aquestes vistes creus que la farem servir: index, edit, create.

11.- Per què podem accedir a @Model si no l'hem declarat?

    <div>The Login Email: @Model.Email</div>

12.- *"The @section directive is used in conjunction with the layout to enable views to render content in different parts of the HTML page. For more information, see Sections."* Creus que podem fer servir @section per posar el nostre propi codi javascript en una pàgina?

---

#FpInfor #Daw #DawMp07 #DawMp07Uf02

---

###### Autor: daniel herrera 2017.12.31 12:46:10
###### Editat per: daniel herrera 2017.12.31 12:54:29
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
