# Treballant amb Vistes: Tags Helpers
## DAW-MP07-UF2 - Exercici de Generació dinàmica de pagines web.
Llegeix amb atenció [ASP.NET Core built-in Tag Helpers](https://docs.microsoft.com/en-us/aspnet/core/mvc/views/tag-helpers/built-in/).

1.- Per què existeixen els tags helpers?

2.- Les aplicacions MVC es generen amb una ruta per defecte:

    app.UseMvc(routes =>
    {
       routes.MapRoute(
        name: "default",
        template: "{controller=Home}/{action=Index}/{id?}");
    });

Per crear una ruta com aquesta:

    <a href='/Speaker/Detail/12'>SpeakerId: 12</a>

Usem el següent codi:

```bash
@model SpeakerData
<!DOCTYPE html>
<html><body>
<a asp-controller='Speaker' asp-action='Detail' asp-route-id=@Model.SpeakerId>SpeakerId: @Model.SpeakerId</a>
<body></html>
```

Quin avantatge i veus d'escriure tot aquest codi en comptes de la ruta 'hardcoded'?

3.- On és la màgia per a que aquest tall de codi Razor de MVC Core:

@model RegisterViewModel

    <form asp-controller="Demo" asp-action="RegisterInput" method="post">
        Email:  <input asp-for="Email" /> <br />
        Password: <input asp-for="Password" /><br />
        <button type="submit">Register</button>
    </form>

Es renderitzi com:
    
    <form method="post" action="/Demo/RegisterInput">
           Email:
           <input type="email" data-val="true"
                  data-val-email="The Email Address field is not a valid e-mail address."
                  data-val-required="The Email Address field is required."
                  id="Email" name="Email" value="" /> <br>
           Password:
           <input type="password" data-val="true"
                  data-val-required="The Password field is required."
                  id="Password" name="Password" /><br>
           <button type="submit">Register</button>
         <input name="__RequestVerificationToken" type="hidden" value="<removed for brevity>" />
       </form>

4.- Observa una pàgina Edit generada per l'scaffolding de visual studio (.NET 4.6). Quina diferència hi veus respecte el Core? Quins helpers fa servir el .NET 4.6?

---

#FpInfor #Daw #DawMp07 #DawMp07Uf02

---

###### Autor: daniel herrera 2017.12.31 13:16:22
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
