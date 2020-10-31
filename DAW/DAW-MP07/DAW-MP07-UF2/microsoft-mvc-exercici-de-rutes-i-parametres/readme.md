# Microsoft MVC - Exercici de rutes i paràmetres
## DAW-MP07-UF2 - Exercici de Generació dinàmica de pagines web.
Observa aquest fitxer `RouteConfig.vb`:

```c++
Public Module RouteConfig
    Public Sub RegisterRoutes(ByVal routes As RouteCollection)
        routes.IgnoreRoute("{resource}.axd/{*pathInfo}")

        routes.MapRoute(
            name:="munyir",
            url:="munyir/{hora}",
            defaults:=New With {.controller = "Vaca", .action = "Munyir", .hora = UrlParameter.Optional}
        )

        routes.MapMvcAttributeRoutes()

        routes.MapRoute(
            name:="Default",
            url:="{controller}/{action}/{id}",
            defaults:=New With {.controller = "Home", .action = "Index", .id = UrlParameter.Optional}
        )
    End Sub
End Module
```

I observa aquest fitxer `VacaController.vb`:

```c++
Public Class VacaController
    Inherits Controller

    Function Index() As String
        Return "Muuuu!"
    End Function

    Function Munyir() As String
        Dim msg As String
        Try
            Dim hora = ValueProvider.GetValue("hora").AttemptedValue
            Select Case hora
                Case 8
                    msg = "Aquí tens 10 litres"
                Case 22
                    msg = "Ara estic dormint"
                Case Else
                    msg = "No són hores"
            End Select
        Catch ex As Exception
            msg = "No sé pas quina hora és."
        End Try
        Return msg
    End Function

    <Route("lavaca/{temperaturaAigua:int}")> _
    Function Netejar() As String
        Dim temperaturaAigua As Integer = RouteData.Values("temperaturaAigua")
        Dim msg As String = ""
        If temperaturaAigua < 0 Then
            msg = "Frrrrred!!"
        ElseIf temperaturaAigua = 0 Then
            msg = "Ni fred ni calor"
        ElseIf temperaturaAigua > 60 Then
            msg = "Em cremo!!"
        Else
            msg = "Perfecte"
        End If
        Return msg
    End Function

End Class
```

Argumenta per què les seguents urls retornen aquests resultats, argumenta les rutes i els paràmetres:

|url|resultat|
|-|-|
|/munyir | No sé pas quina hora és
|/munyir/22 | Ara estic dormint
|/munyir?hora=16 | No són hores
|http://localhost:1259/vaca/munyir?hora=8 |Aquí tens 10 litres
|/vaca/munyir/8 | No sé pas quina hora és.
|/lavaca | 404 ( The resource cannot be found )
|/lavaca/8a| 404 ( The resource cannot be found )
|/lavaca/8 | Perfecte
|/vaca/ | Muuuu!




---

#FpInfor #Daw #DawMp07 #DawMp07Uf02

---

###### Autor: daniel herrera 2014.11.28 09:06:36
###### Editat per: daniel herrera 2014.11.28 09:06:36
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
